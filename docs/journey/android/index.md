---
title: Journey Android - Navitia SDK Docs
---

# Journey Android

## :computer: Setup

Add the following dependencies in the `build.gradle` file of your application:

```kotlin
dependencies {
    implementation("com.kisio.navitia.sdk.ui:journey:5.17.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

``` xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Journey must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!

This module is set up by calling `JourneyUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" style="text-decoration: underline">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`JourneyConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

=== "Configuration with file"

    ``` kotlin
    JourneyUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configurationJsonFile = "config.json"
        )
    }
    ```

=== "Manual configuration"

    ``` kotlin
    JourneyUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configuration = JourneyConfiguration(
                coverage = "your_coverage",
                timezone = "Europe/Paris",
                env = JourneyEnvironment.PROD,
                colors = JourneyColors(
                    primary = "#88819f"
                ),
                transportCategories = listOf<JourneyTransportCategory>()
            )
        )
    }
    ```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

``` kotlin
JourneyUI.getInstance()
    .setNavigationListener(journeyNavigationListenerImpl) // (1)
```

1.  `journeyNavigationListenerImpl` should be the class instance implementing `JourneyNavigationListener` interface.

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `JourneyNavigationListener.Event` parameter you can rely on.

``` kotlin
// Navigation events
EXTERNAL_TO_JOURNEYS
EXTERNAL_TO_ROADMAP
GUIDANCE_BACK_TO_ROADMAP
JOURNEYS_BACK_TO_EXTERNAL
JOURNEYS_TO_RIDESHARING
JOURNEYS_TO_ROADMAP
RIDESHARING_BACK_TO_JOURNEYS
RIDESHARING_TO_ROADMAP
ROADMAP_TO_GUIDANCE
ROADMAP_BACK_TO_EXTERNAL
ROADMAP_BACK_TO_JOURNEYS
ROADMAP_BACK_TO_RIDESHARING
```

### Events tracking

In order to receive the list of generated events within Journey module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

``` kotlin
JourneyUI.getInstance()
    .attachTracker(journeyTrackerImpl) // (1)
```

1.  `journeyTrackerImpl` should be the class instance implementing `JourneyTracker` interface.

## :rocket: Launching

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

### :fontawesome-solid-file-code: `JourneysRequest`

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

#### :fontawesome-solid-file-code: `DataFreshness`

| Enum value | Description |
| --- | --- |
| `BASE_SCHEDULE` | Get disrupted journeys with the given results |
| `REALTIME` | Avoid disrupted journeys |

#### :fontawesome-solid-file-code: `DateTimeRepresents`

| Enum value | Description |
| --- | --- |
| `ARRIVAL` | The requested datetime represents the arrival of the journey |
| `DEPARTURE` | The requested datetime represents the departure of the journey |

#### :fontawesome-solid-file-code: `DirectPath`

| Enum value | Description |
| --- | --- |
| `INDIFFERENT` | Default value |
| `NONE` | For journeys using some public transport |
| `ONLY` | For journeys without public transport |
| `ONLY_WITH_ALTERNATIVES` | For journeys with specific bike  |

#### :fontawesome-solid-file-code: `TravelerType`

| Enum value | Description |
| --- | --- |
| `FAST` | Fast walker |
| `LUGGAGE` | With luggage |
| `SLOW` | Slow walker |
| `STANDARD` | Standard profile |
| `WHEELCHAIR` | Using wheelchair |

## :mega: Communicating with other modules or the app

Journey module can exchange data with or navigate to either other modules or the host application.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules or the app. Communication will not occur unless those are registered beforehand:

``` kotlin
Router.getInstance()
    ... // Register modules and/or app
    .init()
```

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

#### Result journeys / Roadmap view injection

You can inject some external view that will be shown inside the journey module screens. In order to make it happen, you need to add the reference to the `injectableViewDelegate` as follows:

``` kotlin
JourneyUI.getInstance().setInjectableViewDelegate(this)
```

The interface provides the following methods:

```kotlin
override fun allowExternalViewInjectionFor(screen: InjectableScreen, inputData: Any?): ExternalViewInjectionState {
    // Allow or not the external view injection
}

override fun buildExternalViewFor(screen: InjectableScreen, inputData: Any?): View? {
    // Put the view that needs to be injected in the injectable screen
}
```

!!! info "Note"

    `inputData` can be of type:

    - `SharedJourneysScreenData` if the injectable screen is `LIST_JOURNEYS`
    - `SharedRoadmapScreenData` if the injectable screen is `ROADMAP`

:fontawesome-solid-file-code: `SharedJourneysScreenData`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `hasResults` | Whether the request has results or not | `Boolean` |
| `selectedFilterType` | The selected tab | `TransportModesFilterType` |

:fontawesome-solid-file-code: `SharedRoadmapScreenData`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `selectedJourney` | The selected journey data | `SharedSelectedJourneyModel` |

:fontawesome-solid-file-code: `SharedSelectedJourneyModel`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `departureTime` | The departure time | `LocalDateTime` |
| `arrivalTime` | The arrival time | `LocalDateTime` |
| `departureAddress` | The departure address | `String` |
| `arrivalAddress` | The arrival address | `String` |
| `departureCoordinates` | The departure coordinates | `LatLng` |
| `arrivalCoordinates` | The arrival coordinates | `LatLng` |
| `sections` | The list of journey sections | `List<SectionModel>` |

:fontawesome-solid-file-code: `SectionModel`<br>

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

!!! info "Note"

    `additionalInformation` object in `SectionModel` can be of type:

    - `StreetNetworkSectionModel` if the `mobilityType` is `STREET_NETWORK`
    - `PublicTransportSectionModel` if the `mobilityType` is `PUBLIC_TRANSPORT`
    - `CarParkingSectionModel` if the `mobilityType` is `CAR_PARKING`

#### Roadmap actions

You can add some actions to the roadmap screen which can be configured using this appropriate delegate:

``` kotlin
JourneyUI.getInstance().setRoadmapDelegate(this)
```

The implemented interface offers the following methods:

```kotlin
override fun allowedRoadmapScreenActionsFor(inputData: SharedRoadmapScreenData) {
    // Define the allowed actions on the roadmap screen
}

override fun onPrimaryButtonActionTriggered(inputData: SharedRoadmapScreenData) {
    // Handle primary action button click
}

override fun onSecondaryButtonActionTriggered(inputData: SharedRoadmapScreenData) {
    // Handle secondary action button click
}
```

#### Roadmap navigation

A journey may include sections for driving, walking, or cycling. This module provides the option in the Roadmap screen to enhance navigation accuracy using data from an external service.<br>
To enable this feature, first enable the `external_navigation` parameter in the [features configuration](../../getting_started/#journey-features). Then, implement the following method:

```kotlin
override fun openExternalNavigation(
    fromCoords: LatLng,
    fromLabel: String,
    toCoords: LatLng,
    toLabel: String,
    mode: ExternalNavigationMode
) {
    // launch your external navigation service screen or your custom screen
}
```

| Param | Type | Description |
| --- | --- | --- |
| `fromCoords` | `LatLng` | Section departure coordinates |
| `fromLabel` | `String` | Section departure label |
| `toCoords` | `LatLng` | Section arrival coordinates |
| `toLabel` | `String` | Section arrival label |
| `mode` | `ExternalNavigationMode` | Section navigation mode |

!!! info "Note"

    `ExternalNavigationMode` has 3 modes of transportation that describe the section: `BIKE`, `CAR`, and `WALKING`.

### Modules

#### Bookmark

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Bookmark](../../bookmark/android) module in order to display favorite stations, journeys and POIs. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#journey-features).<br>

:octicons-arrow-right-24: Methods<br>

The following methods from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Bookmark module or any other custom screen. Note that the parameters of these methods can be omitted as needed.

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
| `linkedModule` | `BookmarkLinkedModule ` | Module triggering the method call  | `BookmarkLinkedModule.AROUND_ME` or `BookmarkLinkedModule.JOURNEY` |

## :art: Theming

### App theme

The module uses graphical components from Material Design 3. To ensure these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`

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
