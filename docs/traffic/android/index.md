---
title: Traffic Android - Navitia SDK Docs
---

# Traffic Android

## :computer: Setup

Add the following dependencies in the `build.gradle` file of your application:

```kotlin
dependencies {
    implementation("com.kisio.navitia.sdk.ui:traffic:3.2.1")
}
```

The activity launching Traffic must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding

This module is set up by calling `TrafficUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" style="text-decoration: underline">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`TrafficConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate` | :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack` | :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

=== "Configuration with file"

    ``` kotlin
    TrafficUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token"
            configurationJsonFile = "config.json"
        )
    }
    ```

=== "Manual configuration"

    ``` kotlin
    TrafficUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configuration = TrafficConfiguration(
                coverage = "your_coverage",
                timezone = "Europe/Paris",
                env = TrafficEnvironment.PROD,
                colors = TrafficColors(
                    primary = "#88819f"
                ),
                transportCategories = listOf<TrafficTransportCategory>()
            )
        )
    }
    ```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

``` kotlin
TrafficUI.getInstance()
    .setNavigationListener(trafficNavigationListenerImpl) // (1)
```

1.  `trafficNavigationListenerImpl` should be the class instance implementing `TrafficNavigationListener` interface.

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `TrafficNavigationListener.Event` parameter you can rely on.

``` kotlin
// Navigation events
ALL_DISRUPTIONS_BACK_TO_EXTERNAL
ALL_DISRUPTIONS_TO_AUTO_COMPLETION
ALL_DISRUPTIONS_TO_DISRUPTION
ALL_DISRUPTIONS_TO_MY_ALERTS
AUTO_COMPLETION_BACK_TO_ALL_DISRUPTIONS
AUTO_COMPLETION_TO_EDIT_ALERT
DISRUPTION_BACK_TO_ALL_DISRUPTIONS
EDIT_ALERT_BACK_TO_AUTO_COMPLETION
EDIT_ALERT_BACK_TO_ALL_DISRUPTIONS
EXTERNAL_TO_TRAFFIC
MY_ALERTS_BACK_TO_ALL_DISRUPTIONS
MY_ALERTS_TO_AUTO_COMPLETION
MY_ALERTS_TO_EDIT_ALERT
```

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

### Events tracking

In order to receive the list of generated events within Traffic module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

``` kotlin
TrafficUI.getInstance()
    .attachTracker(trafficTrackerImpl) // (1)
```

1.  `trafficTrackerImpl` should be the class instance implementing `TrafficTracker` interface.

## :rocket: Launching

Traffic has a single entry point `AllDisruptionsFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(
        R.id.container_id,
        AllDisruptionsFragment.newInstance(showBack = false),
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

## :art: Theming

The module uses graphical components from Material Design 3. To ensure these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`
