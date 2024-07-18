---
title: Journey Android - Navitia SDK Docs
---

# Journey Android

## 💻 Setup

Add the following dependencies in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.ui:journey:5.13.0")
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

This module is set up by calling `JourneyUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`JourneyConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

```kotlin
JourneyUI.getInstance().let { instance ->
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
| `.setNavigationListener(journeyNavigationListenerImpl)` | Set the class instance implementing `JourneyNavigationListener` interface |

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `JourneyNavigationListener.Event` parameter you can rely on.

| Event |
| --- |
| `EXTERNAL_TO_JOURNEYS` |
| `EXTERNAL_TO_ROADMAP` |
| `GUIDANCE_BACK_TO_ROADMAP` |
| `JOURNEYS_BACK_TO_EXTERNAL` |
| `JOURNEYS_TO_RIDESHARING` |
| `JOURNEYS_TO_ROADMAP` |
| `RIDESHARING_BACK_TO_JOURNEYS` |
| `RIDESHARING_TO_ROADMAP` |
| `ROADMAP_TO_GUIDANCE` |
| `ROADMAP_BACK_TO_EXTERNAL` |
| `ROADMAP_BACK_TO_JOURNEYS` |
| `ROADMAP_BACK_TO_RIDESHARING` |

### Events tracking

In order to receive the list of generated events within Journey module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

| Method | Description |
| --- | --- |
| `.attachTracker(journeyTrackerImpl)` | Attach the class instance implementing `JourneyTracker` interface |

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
| `journeysRequest` | :material-check: | Itinerary search configuration | [`JourneysRequest`](#journeysrequest) | :material-close: |
| `showBack` | :material-close: | Show/hide back button on the first screen | `Boolean` | `false` |

### JourneysRequest

The `JourneysRequest` object allows to configure the first itinerary search at screen launch. It has the following parameters:

| Name | Description | Type | Default |
| --- | --- | --- | --- |
| `additionalTimeAfterFirstSectionTaxi` | Additional time after first taxi section | `Int` | `null` |
| `additionalTimeBeforeLastSectionTaxi` | Additional time before last taxi section | `Int` | `null` |
| `allowedId` | Allowed Navitia object IDs | `List<String>` | `emptyList()` |
| `bikeSpeed` | Bike speed | `Float` | `null` |
| `bssSpeed` | BSS speed | `Float` | `null` |
| `carNoParkSpeed` | Car no park speed | `Float` | `null` |
| `carSpeed` | Car speed | `Float` | `null` |
| `count` | The number of journeys to be displayed | `Int` | `-1` |
| `dataFreshness` | To indicate if theoretical or realtime data are requested | [`DataFreshness`](#datafreshness) | `DataFreshness.BASE_SCHEDULE` |
| `dateTime` | Requested date and time for journey results | `DateTime` | `null` |
| `dateTimeRepresents` | Whether the datetime represents the departure or arrival | [`DateTimeRepresents`](#datetimerepresents) | `DateTimeRepresents.DEPARTURE` |
| `depth` | The request depth | `Int` | `null` |
| `destinationId` | Destination Navitia ID | `String` | `""` |
| `destinationLabel` | Destination label, if not set the address will be displayed | `String` | `""` |
| `directPath` | Set the direct path of the journey | [`DirectPath`](#directpath) | `""` |
| `disruptionActive` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Boolean` | `null` |
| `equipmentDetails` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Boolean` | `null` |
| `freeRadiusFrom` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `freeRadiusTo` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `isJourneySchedules` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Boolean` | `null` |
| `maxBikeDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxBikeDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxBssDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxBssDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxCarDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxCarDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxCarNoParkDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxCarNoParkDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxJourneys` | The max number of journeys to be displayed | `Int` | `-1` |
| `maxNbTransfers` | The max number of public transport transfers | `Int` | `-1` |
| `maxRidesharingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxRidesharingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxTaxiDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxTaxiDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxWaitingDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxWalkingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `maxWalkingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `null` |
| `minJourneys` | The min number of journeys to be displayed | `Int` | `-1` |
| `minNbTransfers` | The min number of public transport transfers | `Int` | `-1` |
| `originId` | Origin Navitia ID | `String` | `""` |
| `originLabel` | Origin label, if not set the address will be displayed | `String` | `""` |
| `ridesharingSpeed` | Ridesharing speed | `Float` | `null` |
| `taxiSpeed` | Taxi speed | `Float` | `null` |
| `timeframeDuration` | Taxi speed | `Int` | `null` |
| `travelerType` | Traveler type | [`TravelerType`](#travelertype) | `TravelerType.STANDARD` |
| `walkingSpeed` | Walking speed | `Float` | `null` |
| `wheelchair` | Check on [Navitia](https://doc.navitia.io/#journeys)  | `Boolean` | `null` |

#### DataFreshness

| Enum value | Description |
| --- | --- |
| `BASE_SCHEDULE` | Get disrupted journeys with the given results |
| `REALTIME` | Avoid disrupted journeys |

#### DateTimeRepresents

| Enum value | Description |
| --- | --- |
| `ARRIVAL` | The requested datetime represents the arrival of the journey |
| `DEPARTURE` | The requested datetime represents the departure of the journey |

#### DirectPath

| Enum value | Description |
| --- | --- |
| `INDIFFERENT` | Default value |
| `NONE` | For journeys using some public transport |
| `ONLY` | For journeys without public transport |
| `ONLY_WITH_ALTERNATIVES` | For journeys with specific bike  |

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

The journeys are grouped into categories represented by different tabs: public transport, walking, bike, car and ridesharing. The visibility of each tab depends on the passed [transport categories configuration](../../getting_started/#transport-category).<br>
In the public transport tab, the journeys are grouped in two sections: recommended journeys and other journeys. The recommended journey ensures to the user that the arrival date is respected and yet, the journey is reliable.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_journeys_screen.png" alt="Journeys screen">

In the bike tab, the bike journeys are classified depending on specific criteria: the fastest, the most comfortable and the most balanced. The cycling path percentage is also displayed to the user to help him choose the right journey. In the same tab, the journeys combining only bike sharing service and walking are also added.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_journeys_screen_bike_tab.png" alt="Bike tab">

Each made itinerary request is saved and shown to the user at the screen launch. The history can be easily deleted by choosing delete from the action menu of the target item.<br>
In the same screen, we also show the list of the favorite journeys that the user has added using the bookmark button (see [Roadmap](#roadmap) section below). To enable this feature, the `bookmark_mode`parameter should be set to `true` in [Journey features](../../getting_started/#journey-features).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_journeys_screen_history_favorite_journeys.png" alt="Journey - History and favorites">

### Search

The search feature can be enabled in the configuration by setting the parameter `search_only` to `false` as mentioned in the [Journey features](../../getting_started/#journey-features) section.<br>
In this screen, the user can choose the departure and the arrival of his itinerary. While typing in the target field, a list of options is shown below the field. The user can simply choose one of the suggested options and mark it as a departure or as an arrival point.<br>

The suggested options are grouped in sections, it's whether a station, an address or a place.
In this screen, a geolocation service is used to get the user location. Therefore, another option is given and it allows the user to set his position as a departure or an arrival of the itinerary.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

If `bookmark_mode` feature is enabled in the [Journey features](../../getting_started/#journey-features), a bookmark section appears in the same screen allowing the user to choose from his favorite addresses/places. A shortcut button is also available for Home and Work favorites.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_autocompletion_screen.png" alt="Autocompletion screen">

### Roadmap

We believe that the user needs more useful details about his journey and that's where the roadmap screen comes in. In this page, the user gets a visual overview about the selected itinerary with a simple colorful drawing on a map. Departure and arrival markers are also shown on the map along with the user location and itinerary segments delimiters.

The screen also includes a draggable bottom sheet which offers a step-by-step journey sections. Each section is represented in a way that it makes it easier to the user to follow the given instructions. The public transport section is also well detailed when it comes to explain to the user how to take different means of transport from the departure to the arrival point.

A customized button can be added in case an external action needs to be made from outside this screen. To enable this button, the parameter `buy_tickets` should be set in [Journey features](../../getting_started/#journey-features).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_roadmap_screen.png" alt="Roadmap screen">

### Ridesharing offers

This screen lists the different ridesharing offers for the selected journey. Regardless of the fact that the journey can propose a full ridesharing trip or a partial ride, the user can select among different third party offers. He has all the information needed to choose the best offer that fits his needs including the departure time, the available seats, the price and some data about the driver offering the ride.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_ridesharing_offers_screen.png" alt="Ridesharing offers screen">

### Navigation

This screen shows the different steps that the user should go through to reach his destination. Those steps are designed to be simple and easily readable for the user and focuses on the most important information during his journey.
Along with the user location, an interaction between the map and the step card is also added to zoom over the current portion of path that refers to the current selected card.

The journey duration and the estimated arrival time are realtime-updated variables which depend on various parameters such as the highlighted step, the next departure of each public transport mode...

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_android_navigation_screen.png" alt="Navigation screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/journey_android_screen_flow.png" alt="Screen flow">

## 🎨 Theming

### App theme

The module utilizes graphical components from Material Design 3. To ensure these components function correctly and display properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!--replace by the specific theme. For example: Theme.Material3.Light.NoActionBar-->
    ...
</style>
```

### Date time picker

The date time picker theme in the Journeys screen is set by the system and cannot really offer yet some flexibility. If a dark mode is applied on the phone, the system will apply predefined colors regardless of the configured colors.<br>
If you want to theme the date time picker, you can only add the following in your style or theme file of your app:

```xml
<style name="Journey.DateTimePicker" parent="ThemeOverlay.Material3.MaterialCalendar">
    <item name="colorAccent">#251942</item> <!--header background-->
    <item name="android:windowBackground">#FFFFFF</item> <!--calendar background-->
    <item name="android:colorControlActivated">#251942</item> <!--selected day-->
</style>
```

## 📢 Communicating with other modules

### Application

Some routes or callbacks are delegated to the application. 
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

#### Roadmap actions

You can add some actions to the roadmap screen which can be configured using this appropriate delegate:

``` kotlin
JourneyUI.getInstance().setRoadmapDelegate(this)
```

The implemented interface offers the following methods:

| Method | Required | Description |
| --- |:---:| --- |
| `allowedRoadmapScreenActionsFor(inputData: SharedRoadmapScreenData): AllowedRoadmapScreenActions` | :material-check: | Define the allowed actions on the roadmap screen |
| `onPrimaryButtonActionTriggered(inputData: SharedRoadmapScreenData)` | :material-check: | Tap callback on the primary button |
| `onSecondaryButtonActionTriggered(inputData: SharedRoadmapScreenData)` | :material-check: | Tap callback on the secondary button |

#### External view injection

You can inject some external view that will be shown inside the journey module screens. In order to make it happen, you need to add the reference to the `injectableViewDelegate` as follows:

``` kotlin
JourneyUI.getInstance().setInjectableViewDelegate(this)
```

The interface provides the following methods:

| Method | Required | Description |
| --- |:---:| --- |
| `allowExternalViewInjectionFor(screen: InjectableScreen, inputData: Any?): ExternalViewInjectionState` | :material-check: | Allow or not the external view injection |
| `buildExternalViewFor(screen: InjectableScreen, inputData: Any?): View?` | :material-check: | Requests the instance of the view that needs to be injected in the injectable screen |

The `inputData` can be of type:

- `SharedJourneysScreenData`: if the injectable screen is `LIST_JOURNEYS`
- `SharedRoadmapScreenData`: if the injectable screen is `ROADMAP`

###### SharedJourneysScreenData

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `hasResults` | Whether the request has results or not | `Boolean` |
| `selectedFilterType` | The selected tab | `TransportModesFilterType` |

###### SharedRoadmapScreenData

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `selectedJourney` | The selected journey data | `SharedSelectedJourneyModel` |

###### SharedSelectedJourneyModel

| Name | Description | Type |
| --- | --- | :---: |
| `departureTime` | The departure time | `LocalDateTime` |
| `arrivalTime` | The arrival time | `LocalDateTime` |
| `departureAddress` | The departure address | `String` |
| `arrivalAddress` | The arrival address | `String` |
| `departureCoordinates` | The departure coordinates | `LatLng` |
| `arrivalCoordinates` | The arrival coordinates | `LatLng` |
| `sections` | The list of journey sections | `[SectionModel]` |

###### SectionModel

| Name | Description | Type |
| --- | --- | :---: |
| `departureTime` | The departure time | `LocalDateTime` |
| `arrivalTime` | The arrival time | `LocalDateTime` |
| `departureAddress` | The departure address | `String` |
| `arrivalAddress` | The arrival address | `String` |
| `departureCoordinates` | The departure coordinates | `LatLng?` |
| `arrivalCoordinates` | The arrival coordinates | `LatLng?` |
| `mobilityType` | The mobility type | `MobilityType` |
| `distance` | The distance in meters | `Int` |
| `duration` | The duration in seconds | `Int` |
| `additionalInformation` | The extra section information if the mobility type allows it | `Any?` |

Please note that the `additionalInformation` object in `SectionModel` can be of type:

- `StreetNetworkSectionModel`: if the `mobilityType` is `STREET_NETWORK`
- `PublicTransportSectionModel`: if the `mobilityType` is `PUBLIC_TRANSPORT`
- `CarParkingSectionModel`: if the `mobilityType` is `CAR_PARKING`
