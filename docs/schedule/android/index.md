---
title: Schedule Android - Navitia SDK Docs
---

# Schedule Android

## :computer: Setup

Add the following dependencies in the `build.gradle` file of your application:

```kotlin
dependencies {
    implementation("com.kisio.navitia.sdk.ui:schedule:2.9.4")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Schedule must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding

This module is set up by calling `ScheduleUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" style="text-decoration: underline">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`ScheduleConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate` | :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack` | :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

=== "Configuration with file"

    ``` kotlin
    ScheduleUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configurationJsonFile = "config.json"
        )
    }
    ```

=== "Manual configuration"

    ``` kotlin
    ScheduleUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configuration = ScheduleConfiguration(
                coverage = "your_coverage",
                timezone = "Europe/Paris",
                env = ScheduleEnvironment.PROD,
                colors = ScheduleColors(
                    primary = "#88819f"
                ),
                transportCategories = listOf<ScheduleTransportCategory>()
            )
        )
    }
    ```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

``` kotlin
ScheduleUI.getInstance()
    .setNavigationListener(scheduleNavigationListenerImpl) // (1)
```

1.  `scheduleNavigationListenerImpl` should be the class instance implementing `ScheduleNavigationListener` interface.

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `ScheduleNavigationListener.Event` parameter you can rely on.

``` kotlin
// Navigation events
LINES_BACK_TO_EXTERNAL
LINES_TO_STATIONS
LINES_TO_TIMETABLE
STATIONS_BACK_TO_LINE
TIMETABLE_BACK_TO_LINES
```

### Events tracking

In order to receive the list of generated events within Schedule module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

``` kotlin
JourneyUI.getInstance()
    .attachTracker(scheduleTrackerImpl) // (1)
```

1.  `scheduleTrackerImpl` should be the class instance implementing `ScheduleTracker` interface.

## :rocket: Launching

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

## :mega: Communicating with other modules or the app

Schedule module navigate to other modules directly or via the host application.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules or the app. Communication will not occur unless those are registered beforehand:

``` kotlin
Router.getInstance()
    ... // Register modules and/or app
    .init()
```

### Application

Some routes are delegated to the application.
If you have to handle navigation between modules, the `Router` module must register a receiver:

``` kotlin
Router.getInstance()
    .register(appUi = appRouterUiImpl) // (1)
```

1.  `appRouterUiImpl` should be the class instance implementing `AppRouter.UI` interface. We recommend using a `Application` subclass.


### Modules

#### Bookmark

This module communicates with [Bookmark](../../bookmark/android) module in order to display favorite stations. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#schedule-features).

#### Journey

This module communicates with [Journey](../../journey/android) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#schedule-features).<br>

The following method from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Journey module or any other custom screens. Note that the parameters of these methods can be ignored as needed.

```kotlin
override fun openJourneysViaHost(
    origin: SharedData.JourneyPoint?,
    destination: SharedData.JourneyPoint?,
    showDirectlyAutoCompletion: Boolean,
    showDirectlyJourneysSearch: Boolean
) {
    // launch the journey module screen or your custom screen
}
```

| Param | Type | Description |
| --- | --- | --- |
| `origin` | `SharedData.JourneyPoint?` | Desired starting point of the journey. Optional |
| `destination` | `SharedData.JourneyPoint?` | Desired endpoint of the journey. Optional |
| `showDirectlyAutoCompletion` | `Boolean` | Directly displays the search for the starting point and/or endpoint. If true, `showDirectlyJourneysSearch` can only be false |
| `showDirectlyJourneysSearch` | `Boolean` | Directly displays the journey search. If true, `showDirectlyAutoCompletion` can only be false |

## :art: Theming

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
    <item name="colorPrimary"><!-- your color --></item>
    <item name="colorOnPrimary"><!-- your contrasted color --></item>

    <item name="materialCalendarStyle">@style/Schedule.MaterialCalendar.Style</item>
    <item name="materialCalendarHeaderLayout">@style/Schedule.MaterialCalendar.HeaderLayout</item>
    <item name="materialCalendarHeaderTitle">@style/Schedule.MaterialCalendar.HeaderTitle</item>
    <item name="materialCalendarHeaderSelection">@style/Schedule.MaterialCalendar.HeaderSelection</item>
    <item name="materialCalendarHeaderToggleButton">@style/Schedule.MaterialCalendar.HeaderToggleButton</item>
</style>

<style name="Schedule.MaterialCalendar.Style" parent="Widget.Material3.MaterialCalendar">
    <item name="backgroundTint"><!-- your contrasted color --></item>
</style>
<style name="Schedule.MaterialCalendar.HeaderLayout" parent="Widget.Material3.MaterialCalendar.HeaderLayout">
    <item name="android:background"><!-- your color --></item>
</style>
<style name="Schedule.MaterialCalendar.HeaderTitle" parent="Widget.MaterialComponents.MaterialCalendar.HeaderTitle">
    <item name="android:textColor"><!-- your contrasted color --></item>
</style>
<style name="Schedule.MaterialCalendar.HeaderSelection" parent="Widget.MaterialComponents.MaterialCalendar.HeaderSelection">
    <item name="android:textColor"><!-- your contrasted color --></item>
</style>
<style name="Schedule.MaterialCalendar.HeaderToggleButton" parent="Widget.MaterialComponents.MaterialCalendar.HeaderToggleButton">
    <item name="android:tint"><!-- your contrasted color --></item>
</style>
```
