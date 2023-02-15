# Bookmark Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:bookmark:1.2.0")
}
```

The activity launching Bookmark must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `BookmarkUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context`| :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token`| :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration`| :material-close: | Module configuration object | [`AroundMeConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile`| :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate`| :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack`| :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

``` kotlin
BookmarkUI.getInstance().let { instance ->
    instance.init(
      context = this,
      token = "your_token",
      configurationJsonFile = "config.json"
   )
   instance.attachActivity(this)
}
```

### Activity delegation

Since the module launches its fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `BookmarkUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Around Me fragments |

Then, you can call `BookmarkUI.getInstance().delegate` to obtain the delegate.
If you try to access it without attaching an activity before, an exception will be thrown.

``` kotlin
BookmarkUI.getInstance().attachActivity(AppCompatActivity)
BookmarkUI.getInstance().delegate.onBackPressed()
```

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

## 📢 Communicating with other modules

### Journey

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
When the user taps on a marker on the map, the buttons **Go from there** and **Go to there** should pop up as follows:

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_android_go_fromto.png" alt="Go from/to">

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.<br>

The `Router` module should also be initialized with the right parameters since it’s mandatory to build the connection between these modules:

``` kotlin
if (!Router.getInstance().isInit) {
    Router.getInstance()
        .register(aroundMe = BookmarkUI.getInstance().delegate)
        .register(journey = JourneysUI.getInstance().delegate)
        .init()
}
```
