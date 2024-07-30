---
title: Bookmark Android - Navitia SDK Docs
---

# Bookmark Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:bookmark:1.6.0")
}
```

The activity launching Bookmark must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `BookmarkUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`AroundMeConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

``` kotlin
BookmarkUI.getInstance().let { instance ->
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
| `.setNavigationListener(bookmarkNavigationListenerImpl)` | Set the class instance implementing `BookmarkNavigationListener` interface |

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `BookmarkNavigationListener.Event` parameter you can rely on.

| Event |
| --- |
| `ADD_ADDRESS_BACK_TO_FAVORITES` |
| `EXTERNAL_TO_ADD_ADDRESSES` |
| `EXTERNAL_TO_FAVORITES` |
| `FAVORITES_BACK_TO_EXTERNAL` |
| `FAVORITES_TO_JOURNEY` |
| `FAVORITES_TO_ADD_ADDRESS` |
| `FAVORITES_TO_ROADMAP` |

## 🚀  Launching

Bookmark has a single entry point `FavoriteFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, FavoriteFragment.newInstance(), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## 📱 Screens

### Favorites

This screen lists all the favorite stations, Bike sharing service stations, car parkings and addresses added by the user through other UI modules (Around Me, Schedule...) or from within a 3rd party application.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_android_favorites_screen.png" alt="Favorites screen">

## 🎨 Theming

The module uses graphical components from Material Design 3. To ensure these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`

## 📢 Communicating with other modules or the app

Bookmark module can exchange data with, or navigate to, other modules or the host application.

### Application

Some route or callbacks are delegated to the application.
If you have to receive some module data, the `Router` module must register a receiver with the right parameter:

``` kotlin
Router.getInstance()
    .register(appData = appRouterDataImpl) // (1)
```

1.  `appRouterDataImpl` should be the class instance implementing `AppRouter.Data` interface. We recommend using an `Application` subclass.

If you have to handle navigation between modules, the `Router` module must also register a receiver:

``` kotlin
Router.getInstance()
    .register(appUi = appRouterUiImpl) // (1)
```

1.  `appRouterUiImpl` should be the class instance implementing `AppRouter.UI` interface. We recommend using a `Application` subclass.

#### Data interface methods

```kotlin
override fun onUpdateFavoriteStations(id: String) {
    // handle the favorite station update booking
}
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Updated favorite station id |

### Modules

#### Journey

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
When the user taps on a marker on the map, the buttons **Go from there** and **Go to there** should pop up as follows:

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_android_go_fromto.png" alt="Go from/to">

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.

The following method from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Journey module or any other custom screens. Note that the parameters of these methods can be ignored as needed.

```kotlin
override fun openJourneysViaHost(
    origin: SharedData.JourneyPoint?,
    destination: SharedData.JourneyPoint?,
    showDirectlyAutoCompletion: Boolean
) {
    // launch the journey module screen or your custom screen
}
```

| Param | Type | Description |
| --- | --- | --- |
| `origin` | `SharedData.JourneyPoint?` | Journey departure point  |
| `destination` | `SharedData.JourneyPoint?` | Journey arrival point  |
| `showDirectlyAutoCompletion` | `Boolean` | Enable/disable showing the autocompletion on screen launch |
