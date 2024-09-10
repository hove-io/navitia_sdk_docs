---
title: Around Me Android - Navitia SDK Docs
---

# Around Me Android

## :computer: Setup

Add the following dependencies in the `build.gradle` file of your application:

```kotlin
dependencies {
    implementation("com.kisio.navitia.sdk.ui:aroundme:2.10.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Around Me must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding

This module is set up by calling `AroundMeUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`AroundMeConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

=== "Configuration with file"

    ``` kotlin
    AroundMeUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configurationJsonFile = "your_config_file"
        )
    }
    ```

=== "Manual configuration"

    ``` kotlin
    AroundMeUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configuration = AroundMeConfiguration(
                coverage = "your_coverage",
                timezone = "Europe/Paris",
                env = AroundMeEnvironment.PROD,
                colors = AroundMeColors(
                    primary = "#88819f"
                ),
                transportCategories = listOf<AroundMeTransportCategory>(),
            )
        )
    }
    ```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

| Method | Description |
| --- | --- |
| `.setNavigationListener(aroundMeNavigationListenerImpl)` | Set the class instance implementing `AroundMeNavigationListener` interface |

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `AroundMeNavigationListener.Event` parameter you can rely on.

| Event |
| --- |
| `MAP_TO_FAVORITES` |
| `MAP_TO_JOURNEY` |
| `MAP_TO_TRAFFIC` |
| `MAP_TO_ROADMAP` |
| `MAP_TO_FILTER` |
| `MAP_TO_SEARCH` |
| `MAP_BACK_TO_EXTERNAL` |
| `SEARCH_BACK_TO_MAP` |
| `FILTER_BACK_TO_MAP` |

### Events tracking

In order to receive the list of generated events within Around me module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachTracker(aroundMeTrackerImpl)` | Attach the class instance implementing `AroundMeTracker` interface |

## :rocket: Launching

Around Me has a single entry point `MapFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, MapFragment.newInstance(), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## :mega: Communicating with other modules or the app

Around Me module can exchange data with or navigate to either other modules or the host application.

### Application

Some route or callbacks are delegated to the application.
If you have to receive some module data, `Router` must register the app data receiver:

``` kotlin
Router.getInstance()
    .register(appData = appRouterDataImpl) // (1)
```

1.  `appRouterDataImpl` should be the class instance implementing `AppRouter.Data` interface. We recommand usign a `Application` subclass.

If you have to handle navigation between modules, `Router` must also register the app UI receiver:

``` kotlin
Router.getInstance()
    .register(appUi = appRouterUiImpl) // (1)
```

1. `appRouterUiImpl` should be the class instance implementing `AppRouter.UI` interface. We recommand usign a `Application` subclass.

After registering, you have to call `init()`:

``` kotlin
Router.getInstance().init()
```


#### Data interface methods

A customizable button appears in the free floating details screen and the clicking event should be intercepted by the application.

```kotlin
override fun onBookFreeFloating(id: String) {
    // handle the free floating booking
}
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Selected free floating id |

A customizable button appears in the POI details screen and the clicking event should be intercepted by the application.

```kotlin
override fun onBookPoi(id: String) {
    // handle the free POI booking
}
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Selected POI id |

#### Custom account UI

```kotlin
override fun openAccountViaHost() {
    // launch your custom screen
}
``` 

### Modules

#### Bookmark

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Bookmark](../../bookmark/) module in order to display favorite stations and POIs. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

:octicons-arrow-right-24: Methods<br>

The following methods from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Bookmark module or any other custom screen. Note that the parameters of these methods can be omitted as needed.

```kotlin
override fun openFavoritesViaHost(linkedModule: LinkedModule, tab: FavoriteTab) {
    // launch the bookmark module screen or your custom screen
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `linkedModule` | `BookmarkLinkedModule` | Module triggering the method call | `BookmarkLinkedModule.AROUND_ME` or `BookmarkLinkedModule.JOURNEY` |
| `tab` | `FavoriteTab` | Tab to display in the Bookmark module screen | `FavoriteTab.TRANSPORTS`, `FavoriteTab.JOURNEYS` or `FavoriteTab.ADDRESSES` |

```kotlin
override fun openFavoriteHomeAddViaHost(linkedModule: BookmarkLinkedModule) {
    // launch the bookmark module screen or your custom screen
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `linkedModule` | `BookmarkLinkedModule` | Module triggering the method call  | `BookmarkLinkedModule.AROUND_ME` or `BookmarkLinkedModule.JOURNEY` |

```kotlin
override fun openFavoriteWorkAddViaHost(linkedModule: LinkedModule) {
    // launch the bookmark module screen or your custom screen
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `linkedModule` | `LinkedModule` | Module triggering the method call  | `LinkedModule.AROUND_ME` or `LinkedModule.JOURNEY` |

#### Journey

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen itinerary. You should enable the `journey_mode` and the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
Another way to communicate with is through the [Map](../screens/#map) screen and precisely the _Where are we going?_ button, this feature should also be enabled by setting the `where_shall_we_go` in the [features configuration](../../getting_started/#around-me-features) to `true`.<br>

:octicons-arrow-right-24: Methods<br>

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

#### Schedule

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Schedule](../../traffic/) module in order to show line and station search. You should enable the `schedule_mode` parameter in the [features configuration](../../getting_started/#around-me-features).

:octicons-arrow-right-24: Method<br>

The following method from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Schedule module or any other custom screens.

```kotlin
override fun openScheduleSearchViaHost() {
    // launch the schedule module screen or your custom screen
}
```

#### Traffic

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Traffic](../../traffic/) module in order to easily access traffic information. You should enable the `traffic_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

:octicons-arrow-right-24: Method<br>

The following method from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Traffic module or any other custom screen.

```kotlin
override fun openTrafficViaHost() {
    // launch the ticket module screen or your custom screen
}
```

## :art: Theming

The module uses graphical components from Material Design 3. To ensure that these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`
