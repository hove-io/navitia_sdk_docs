# Traffic Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:traffic:2.4.0")
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

This module is set up by calling `TrafficUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`TrafficConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate` | :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack` | :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

``` kotlin
TrafficUI.getInstance().let { instance ->
    instance.init(
      context = this,
      token = "your_token"
      configurationJsonFile = "config.json"
    )
}
```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

| Method | Description |
| --- | --- |
| `.setNavigationListener(trafficNavigationListenerImpl)` | Set the class instance implementing `TrafficNavigationListener` interface |

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `TrafficNavigationListener.Event` parameter you can rely on.

| Event |
| --- |
| `ALL_DISRUPTIONS_BACK_TO_EXTERNAL` |
| `ALL_DISRUPTIONS_BACK_TO_NETWORKS` |
| `ALL_DISRUPTIONS_TO_AUTO_COMPLETION` |
| `ALL_DISRUPTIONS_TO_DISRUPTION` |
| `ALL_DISRUPTIONS_TO_MY_ALERTS` |
| `AUTO_COMPLETION_BACK_TO_ALL_DISRUPTIONS` |
| `AUTO_COMPLETION_TO_EDIT_ALERT` |
| `DISRUPTION_BACK_TO_ALL_DISRUPTIONS` |
| `EDIT_ALERT_BACK_TO_AUTO_COMPLETION` |
| `EDIT_ALERT_BACK_TO_ALL_DISRUPTIONS` |
| `EXTERNAL_TO_TRAFFIC` |
| `MY_ALERTS_BACK_TO_ALL_DISRUPTIONS` |
| `MY_ALERTS_TO_AUTO_COMPLETION` |
| `MY_ALERTS_TO_EDIT_ALERT` |
| `NETWORK_BACK_TO_EXTERNAL` |
| `NETWORK_TO_ALL_DISRUPTIONS` |

### Alert subscription

To enable the alert subscription feature, the following instructions are required:
- Add the [environment configuration](../../getting_started/#traffic-features)
- Pass the [Kronos API credentials](#traffic-alert-subscription-credentials) to the initialization method
- Set the firebase token `TrafficUI.getInstance().firebaseToken("token")` once received from the Firebase API at runtime

#### Traffic alert subscription credentials

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `username` | :material-check: | Kronos authentication username | `String` |
| `password` | :material-check: | Kronos authentication password | `String` |

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
| `showBack` | :material-close: | Show/hide back button on the first screen | `Boolean` | `false` |

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
Some disruptions have messages with included hyperlinks. Those links are also accessible to the user and will redirect him to an external browser to view the related link.<br>

If the [alert subscription](#alert-subscription) feature is enabled, a bell button appears allowing the user to subscribe/unsubscribe to/from the line alerts.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_all_disruptions_screen.png" alt="All disruptions screen">

### Line selection

This screen includes an autocompletion that enables the user to search the transport line needed for alert subscription.<br>
The parameter [`transport_networks`](../../getting_started/#traffic-features) allows to show the network providing the searched line. 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_line_selection_screen.png" alt="Line selection screen">

### Subscription schedule

After selecting a line from the autocompletion screen, this screen appears giving the ability to the user to choose/modify the periods in which the alert subscription can be received.<br>
Please verify that you have passed valid [Kronos API credentials](#traffic-alert-subscription-credentials) to the module initialization method in order to ensure a successful alert subscription process.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_subscription_schedule_screen.png" alt="Subscription schedule screen">

### Subscriptions list

This screen lists all the alert subscriptions that the user have registered. The subscriptions are also grouped by transport categories allowing to filter the subscriptions depending on the impacted line transport mode.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_android_subscriptions_list_screen.png" alt="Subscriptions list screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/traffic_android_screen_flow.png" alt="Screen flow">
