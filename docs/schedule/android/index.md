---
title: Schedule Android - Navitia SDK Docs
---

# Schedule Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:schedule:2.7.1")
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

This module is set up by calling `ScheduleUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`ScheduleConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate` | :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack` | :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

``` kotlin
ScheduleUI.getInstance().let { instance ->
    instance.init(
      context = this,
      token = "your_token",
      configurationJsonFile = "config.json"
   )
}
```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

| Method | Description |
| --- | --- |
| `.setNavigationListener(scheduleNavigationListenerImpl)` | Set the class instance implementing `ScheduleNavigationListener` interface |

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `ScheduleNavigationListener.Event` parameter you can rely on.

| Event |
| --- |
| `LINES_BACK_TO_EXTERNAL` |
| `LINES_TO_STATIONS` |
| `LINES_TO_TIMETABLE` |
| `STATIONS_BACK_TO_LINE` |
| `TIMETABLE_BACK_TO_LINES` |

## 🚀  Launching

Schedule has a single entry point `LinesFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(
        R.id.container_id,
        LinesFragment.newInstance(showBack = false),
        "TAG"
    )
    addToBackStack("TAG")
    commit()
}
```

The `newInstance()` method creates an instance of the target fragment and takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | --- | --- |
| `showBack` | :material-close: | Show/hide back button on the first screen | `Boolean` | `false` |

## 📱 Screens

### Lines

The lines screen allows the user to see all the lines of the defined coverage. The lines are sorted by the different configurable transport categories.<br>
Another filter is added for each transport mode in the selected transport category. 

The lines can also be grouped by networks. To enable this feature, you need to switch the `transport_networks` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_home_screen.png" alt="Lines screen">

If there is any favorite station, an additional tab will be shown listing all bookmarked stations. Each station has a maximum of 3 next departures by destination or an empty state if data is unavailable.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_home_favorites_screen.png" alt="Lines screen with favorites">

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

This screen allows the user to see the next departures of the target transport mode through the selected station which is heading to the chosen destination. The map gives more details about the vehicle journey by drawing the line path and both selected station and destination markers.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_next_departures_screen.png" alt="Next departures screen">

The user can also bookmark this selected station by taping the Favorite button on the bottom-right corner of the map. To enable this feature, you need to switch the `bookmark_mode` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_next_departures_favorites_screen.png" alt="Next departures screen with favorite">

### All schedules

When the user taps on the All schedules button in the [next departures](#next-departures) screen, the all schedules screen shows up and gives all theoretical departures of the selected line from the selected station to the target destination.<br>

This screen includes a datepicker button allowing the user to choose a date and see all the scheduled departures on that date.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_all_schedules_screen.png" alt="All schedules screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/schedule_android_screen_flow.png" alt="Screen flow">

## 🎨 Theming

### App theme

The module utilizes graphical components from Material Design 3. To ensure these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`

### Date time picker

The date picker theme in the Journeys screen is set by the system and cannot really offer yet some flexibility. If a dark mode is applied on the phone, the system will apply predefined colors regardless of the configured colors.<br>
If you want to theme the date picker, you can only add the following in your style or theme file of your app:

```xml
<style name="Schedule.MaterialCalendar" parent="ThemeOverlay.Material3.MaterialCalendar">
    <item name="colorPrimary">@#251942</item>
    <item name="colorOnPrimary">#FFFFFF</item>
</style>
```
