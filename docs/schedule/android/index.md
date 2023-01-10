# Schedule Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:schedule:2.1.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/> <!-- (1) -->
```

1.  Replace `YOUR_API_KEY` with your Google Maps API Key

The activity launching Schedule must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `ScheduleUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context`| :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token`| :material-check: | Navitia token | `String` | :material-close: |
| `configuration`| :material-close: | Module configuration object | [`ScheduleConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile`| :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate`| :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack`| :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

``` kotlin
ScheduleUI.getInstance().let { instance ->
    instance.init(
      context = this,
      configurationJsonFile = "config.json"
   )
   instance.attachActivity(this)
}
```

### Activity delegation

Since the module launches its fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `ScheduleUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Schedule fragments |

Then, you can call `ScheduleUI.getInstance().delegate` to obtain the delegate.
If you try to access it without attaching an activity before, an exception will be thrown.

``` kotlin
ScheduleUI.getInstance().attachActivity(AppCompatActivity)
ScheduleUI.getInstance().delegate.onBackPressed()
```

## 🚀  Launching

Schedule has a single entry point `HomeFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(
        R.id.container_id,
        HomeFragment.newInstance(showBack = false),
        "TAG"
    )
    addToBackStack("TAG")
    commit()
}
```

The `newInstance()` method creates an instance of the target fragment and takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | --- | --- |
| `showBack`| :material-close: | Show/hide back button on the first screen | `Boolean` | `false` |

## 📱 Screens

### Home

The home screen allows the user to see all the lines of the defined coverage. The lines are sorted by the different configurable transport categories.<br>
Another filter is added for each transport mode in the selected transport category.

The lines can also be grouped by networks. To enable this feature, you need to switch the `transport_networks` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_home_screen.png" alt="Home screen">

### Search

The search screen allows the user to seek for a station or a line using a built-in autocompletion. The result is based on the user search input text.<br>
The station result combines both the name of the station and all the lines passing through that station. This will allow the user to select directly the searched line and get the list of all destinations starting from the target station point.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_search_screen.png" alt="Search screen">

### Stations

The station screen lists all the stations of the selected line alphabetically sorted. A search feature is added to filter the lines and makes it easier for the user to search for the desired station.<br>
In case the `directions_first` parameter is set to `true` in the [features configuration](../../getting_started/#schedule-features), this screen will show all stations of a defined route (destination).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_line_stations_screen.png" alt="Stations screen">

### Destinations

The destinations screen lists all possible destinations starting from the target station point.<br>
In case the `directions_first` parameter is set to `true` in the [features configuration](../../getting_started/#schedule-features), this screen will show all the destinations of the selected line.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_destinations_screen.png" alt="Destinations screen">

### Next departures

This screen allows the user to see the next departures of the target transport mode through the selected station which is heading to the choisen destination. The map gives more details about the vehicle journey by drawing the line path and both selected station and destination markers.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_next_departures_screen.png" alt="Next departures screen">

### All schedules

When the user taps on the All schedules button in the [next departures](#next-departures) screen, the all schedules screen shows up and gives all theoretical departures of the selected line from the selected station to the target destination.<br>

This screen includes a datepicker button allowing the user to choose a date and see all the scheduled departures on that date.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_all_schedules_screen.png" alt="All schedules screen">

## 🗺 Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/schedule_android_navigating.png" alt="Navigating">
