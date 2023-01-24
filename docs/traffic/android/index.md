# Traffic Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:traffic:2.1.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/> <!-- (1) -->
```

1.  Replace `YOUR_API_KEY` with your Google Maps API Key

The activity launching Traffic must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `TrafficUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context`| :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token`| :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration`| :material-close: | Module configuration object | [`TrafficConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile`| :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate`| :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack`| :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

``` kotlin
TrafficUI.getInstance().let { instance ->
    instance.init(
      context = this,
      token = "your_token"
      configurationJsonFile = "config.json"
   )
   instance.attachActivity(this)
}
```

### Activity delegation

Since the module launches its fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `TrafficUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Traffic fragments |

Then, you can call `TrafficUI.getInstance().delegate` to obtain the delegate.
If you try to access it without attaching an activity before, an exception will be thrown.

``` kotlin
TrafficUI.getInstance().attachActivity(AppCompatActivity)
TrafficUI.getInstance().delegate.onBackPressed()
```

## 🚀  Launching

Traffic has a single entry point `HomeFragment`.<br>
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

The home screen allows the user to view all the line and network disruptions sorted by transport category.<br>
When clicking on a disrupted line, the message and the application period of the disruption shows up along with an **All disruptions** button. This button redirects the user to the [line disruptions](#linenetwork-disruptions) screen.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_home_screen.png" alt="Home screen">

#### Filters

The home screen integrated a menu accessible through the header right button. This menu shows the different transport categories with a default selection.<br>
If the user hits the **Apply** button after changing the selection state, the home screen will refresh and will show the disruptions according to the updated filters.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_filters_menu.png" alt="Filters menu">

### Line/network disruptions

This screen lists the disruptions related to the selected line or to all disrupted networks. Each element shows the title, the message and the application period of a target disruption.<br>
Some disruptions have messages with included hyperlinks. Those links are also accessible to the user and will redirect him to an external browser to view the related link.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_all_disruptions_screen.png" alt="All disruptions screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/traffic_android_screen_flow.png" alt="Screen flow">
