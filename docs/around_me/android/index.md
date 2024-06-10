---
title: Around Me Android - Navitia SDK Docs
---

# Around Me Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:aroundme:2.8.1")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/> <!-- (1) -->
```

1.  Replace `YOUR_API_KEY` with your Google Maps API Key

The activity launching Around Me must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `AroundMeUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`AroundMeConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

``` kotlin
AroundMeUI.getInstance().let { instance ->
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

## 🚀  Launching

Around Me has a single entry point `MapFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, MapFragment.newInstance(), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## 📱 Screens

### Map

The map screen represents the main screen of this module. It shows the places nearby the center of the visible region, draws them on the map and adds them to the bottom sliding panel.<br>
The shown data depend on the selected elements in the [filters](#filters) screen.

In the bottom sheet of the main screen, the last added favorite stations are shown with the next departures for each direction, as well as an All Favorites button that redirects the user to the bookmark module. In the same section, if the user has added his journeys to favorites in journey module, a favorite journeys section appears showing the list of bookmarked journeys.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_map_screen.png" alt="Map screen">

In the details bottom sheet of a station or a POI, there is a star button in order to save or delete it from the bookmarks.
<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_bookmark_saving_node.png" alt="Bookmark node">

### Search

The search screen allows the user to seek for a place using a built-in autocompletion. The result is a selection of addresses, stations and points of interest based on the user search input text.<br>
If an element is selected, this screen will disappear and the map will be centered over the selected item location.
Please note that a history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_search_screen.png" alt="Search screen">

### Filters

This screen content is a visual version of the passed transport categories and POI categories configuration (check [modules configuration](../../getting_started/#modules-configuration) section for more information). The selected elements will be used to filter the data received and drawn within the map. One filter should at least be selected or else the user can't apply the current filters configuration.<br><br>
If you want to reset the user filters configuration, you can simply call `AroundMeUI.getInstance().resetUserPreferences()` and the current configuration will be deleted and the screen will be updated according to the new passed configuration.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_filters_screen.png" alt="Filters screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens:

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/aroundme_android_screen_flow.png" alt="Screen flow">

## 📢 Communicating with other modules

### Journey

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
When the user taps on a marker on the map, the buttons **Go from there** and **Go to there** should pop up as follows:

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_go_fromto.png" alt="Go from/to">

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.<br>

Another way to communicate with [Journey](../../journey/) module is through the [Map](#map) screen and precisely the **Where are we going?** button, this feature should also be enabled by setting the `where_shall_we_go` in the [features configuration](../../getting_started/#around-me-features) to `true`.<br>

### Bookmark

This module communicates with [Bookmark](../../bookmark/) module in order to vizualize favorite stations and POIs. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

### Traffic

This module communicates with [Traffic](../../traffic/) module in order to easily access traffic information. You should enable the `traffic_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
A red traffic button will appear in the top right corner, only when the search bar is hidden.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_traffic_button.png" alt="Traffic mode">

### Application

Some route or callbacks are delegated to the application. 
If you have to receive some module data, the `Router` module must register a receiver with the right parameter:

``` kotlin
Router.getInstance()
    .register(appData = appRouterDataImpl) // (1)
```

1.  `appRouterDataImpl` should be the class instance implementing `AppRouter.Data` interface. We recommand usign a `Application` subclass.

If you have to handle navigation between modules, the `Router` module must also register a receiver:

``` kotlin
Router.getInstance()
    .register(appUi = appRouterUiImpl) // (1)
```

1. `appRouterUiImpl` should be the class instance implementing `AppRouter.UI` interface. We recommand usign a `Application` subclass.

##### POI event

A customizable button appears in the POI details screen and the clicking event should be catched from the application. A POI ID is sent with the callback in order to identify the selected POI.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_android_poi_button_event.png" alt="POI button event">

### Crowdsourcing

⚠️ This section will be available soon!
