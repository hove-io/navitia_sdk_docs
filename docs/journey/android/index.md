# Journey Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:journey:5.1.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/> <!-- (1) -->
```

1.  Replace `YOUR_API_KEY` with your Google Maps API Key

The activity launching Journey must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `JourneyUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context`| :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `configuration`| :material-close: | Module configuration object | [`JourneyConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile`| :material-close: | Module configuration JSON file name | `String` | `null` |
| `onNavigate`| :material-close: | Listener for the navigation between module screens | `Unit` | `{ _ -> }` |
| `onBack`| :material-close: | Listener for the navigation back button click event | `Unit` | `{ _ -> }` |

<h4>Example</h4>

```kotlin
JourneyUI.getInstance().let { instance ->
    instance.init(
      context = this,
      configurationJsonFile = "config.json"
   )
   instance.attachActivity(this)
}
```

### Activity delegation

Since the module launches its fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `JourneyUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Journey fragments |

Then, you can call `JourneyUI.getInstance().delegate` to obtain the delegate.
If you try to access it without attaching an activity before, an exception will be thrown.

```kotlin
JourneyUI.getInstance().attachActivity(AppCompatActivity)
JourneyUI.getInstance().delegate.onBackPressed()
```

## 🚀  Launching

Journey has a single entry point `JourneysFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

```kotlin
supportFragmentManager.beginTransaction().run {
    replace(
        R.id.container_id,
        JourneysFragment.newInstance(journeysRequest = JourneysRequest(), showBack = false),
        "TAG"
    )
    addToBackStack("TAG")
    commit()
}
```

The `newInstance()` method creates an instance of the target fragment and takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | --- | --- |
| `journeysRequest`| :material-check: | Itinerary search configuration | [`JourneysRequest`](#journeysrequest) | :material-close: |
| `showBack`| :material-close: | Show/hide back button on the first screen | `Boolean` | `false` |

### JourneysRequest

The `JourneysRequest` object allows to configure the first itinerary search at screen launch. It has the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | --- | --- |
| `allowedId`| :material-close: | Allowed Navitia object IDs | `List<String>` | `emptyList()` |
| `addPoiInfos`| :material-close: | Request extra POI infos | [`MutableSet<AddPoiInfos>`](#addpoiinfos) | `mutableSetOf()` |
| `count`| :material-close: | The number of journeys to be displayed | `Int` | `-1` |
| `dataFreshness`| :material-close: | To indicate if theoretical or realtime data are requested | [`DataFreshness`](#datafreshness) | `DataFreshness.BASE_SCHEDULE` |
| `dateTime`| :material-close: | Requested date and time for journey results | `DateTime` | `null` |
| `dateTimeRepresents`| :material-close: | Whether the datetime represents the departure or arrival | [`DateTimeRepresents`](#datetimerepresents) | `DateTimeRepresents.DEPARTURE` |
| `destinationAddress`| :material-close: | Destination point address | `String` | `""` |
| `destinationId`| :material-close: | Destination Navitia ID | `String` | `""` |
| `destinationLabel`| :material-close: | Destination label, if not set the address will be displayed | `String` | `""` |
| `directPathMode`| :material-close: | List of direct path modes | `MutableSet<String>` | `mutableSetOf()` |
| `firstSectionModes`| :material-close: | List of first section modes | `MutableSet<String>` | `mutableSetOf()` |
| `forbiddenUris`| :material-close: | List of forbidden physical modes | `MutableSet<String>` | `mutableSetOf()` |
| `lastSectionModes`| :material-close: | List of last section modes | `MutableSet<String>` | `mutableSetOf()` |
| `maxJourneys`| :material-close: | The max number of journeys to be displayed | `Int` | `-1` |
| `minJourneys`| :material-close: | The min number of journeys to be displayed | `Int` | `-1` |
| `originAddress`| :material-close: | Origin point address | `String` | `""` |
| `originId`| :material-close: | Origin Navitia ID | `String` | `""` |
| `originLabel`| :material-close: | Origin label, if not set the address will be displayed | `String` | `""` |
| `travelerType`| :material-close: | Traveler type | [`TravelerType`](#travelertype) | `TravelerType.STANDARD` |

#### AddPoiInfos

| Enum value | Description |
| --- | --- |
| `BSS_STANDS` | Request the number of available stands in a BSS station |
| `CAR_PARK` | Request the number of available places in a car parking |

#### DataFreshness

| Enum value | Description |
| --- | --- |
| `BASE_SCHEDULE` | Get disrupted journeys with the given results |
| `REALTIME` | Avoid disrupted journeys |

#### DateTimeRepresents

| Enum value | Description |
| --- | --- |
| `ARRIVAL` | The requestd datetime represents the arrival of the journey |
| `DEPARTURE` | The requested datetime represents the departure of the journey |

#### TravelerType

| Enum value | Description |
| --- | --- |
| `FAST` | Fast walker |
| `LUGGAGE` | With luggage |
| `SLOW` | Slow walker |
| `STANDARD` | Standard profile |
| `WHEELCHAIR` | Using wheelchair |

## 📱 Screens

### Journeys

The journeys screen is fundamental and offers the solutions to the user for the requested itinerary.
After defining all the required parameters, this screen will popup with multiple results combining public transport, personal bikes/cars, bike sharing system and even ridesharing possibilities.

Each result gives the needed information to the user in order to planify his journey. He can check the duration, the suggested means of transport, the next departure datetimes and many other useful details. This combination of data, being served by <a href="https://doc.navitia.io" target="_blank">Navitia</a> servers and translated into a comprehensible/user friendly interface, is perfectly shaped to the user profile and needs.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_journeys_screen.png" alt="Journeys screen">

### Search

The search feature can be enabled in the configuration by setting the parameter `search` to `true` as mentioned in the [Journey features](../../getting_started/#journey-features) section.<br>
In this screen, the user can choose the departure and the arrival of his itinerary. While typing in the target field, a list of options is shown below the field. The user can simply choose one of the suggested options and mark it as a departure or as an arrival point.<br>

The suggested options are grouped in sections, it's whether a station, an address or a place.
In this screen, a geolocation service is used to get the user location. Therefore, another option is given and it allows the user to set his position as a departure or an arrival of the itinerary.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_autocompletion_screen.png" alt="Autocompletion screen">

### Roadmap

We believe that the user needs more useful details about his journey and that's where the roadmap screen comes in. In this page, the user gets a visual overview about the selected itinerary with a simple colorful drawing on a map. Departure and arrival markers are also shown on the map along with the user location and itinerary segments delimiters.

The screen also includes a draggable bottom sheet which offers a step-by-step journey sections. Each section is represented in a way that it makes it easier to the user to follow the given instructions. The public transport section is also well detailed when it comes to explain to the user how to take different means of transport from the departure to the arrival point.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_roadmap_screen.png" alt="Roadmap screen">

### Ridesharing offers

This screen lists the different ridesharing offers for the selected journey. Regardless of the fact that the journey can propose a full ridesharing trip or a partial ride, the user can select among different third party offers. He has all the information needed to choose the best offer that fits his needs including the departure time, the available seats, the price and some data about the driver offering the ride.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_ridesharing_offers_screen.png" alt="Ridesharing offers screen">

## 🗺 Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/journey_android_navigating.png" alt="Navigating">
