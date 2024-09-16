---
title: Journey iOS - Navitia SDK Docs
---

# Journey iOS

## :computer: Setup

In your project, add the following lines to your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'JourneySDK', '5.13.0' # Journey Pod definition
end

# Required for XCFramework
post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
    end
  end
end
```

Using your CLI, run `pod install` in your project directory.

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!

This module is set up by calling `JourneySdk.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `colors` | :material-check: | Define the custom colors | [`JourneyColorsConfiguration`](../../getting_started/#journey-color) | - |
| `fonts` | :material-close: | Use custom fonts | [`JourneyFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories` | :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `providerResources` | :material-close: | Transport providers configuration | [`[ProviderResource]`](../../getting_started/#provider-resource) | - |
| `titleResources` | :material-close: | Screens titles customization | [`JourneyTitlesResources`](../../getting_started/#journey-title-resource) | - |
| `features` | :material-close: | Enable/disable some features  | [`JourneyFeaturesConfiguration`](../../getting_started/#journey-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile` | :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

=== "Configuration with file"

    ```swift
    do {
        try JourneySdk.shared.initialize(
            token: "your_token", 
            configurationJsonFile: "journey_configuration.json"
        )                                                               
    } catch {
        Logger.error("%@", String(
            format: "Journey SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }                                   
    ```

=== "Manual configuration"

    ```swift
    do {
        let transportCategories = [TransportCategory(
            modules: ["journey"],
            iconRes: "ic_section_mode_metro",
            nameRes: "metro",
            selected: true,
            modes: [TransportCategoryMode(
                physical: TransportPhysicalMode(id "physical_mode:Metro"),
                commercial: TransportCommercialMode(
                    id: "commercial_mode:Metro", 
                    name: "Metro"
                )
            )],
            networks: [],
            firstSectionModes: ["walking"],
            lastSectionModes: ["walking"],
            directPathModes: ["walking"],
            addPoiInfos: []
        )]
        let journeyColorsConfiguration = JourneyColorsConfiguration(
            primary: "#88819f", 
            secondary: "#8faa96"
        )
                                                                          
        try JourneySdk.shared.initialize(
            coverage: "fr-idf",
            token: "your_token",
            env: "PROD",
            colors: journeyColorsConfiguration,
            transportCategories: transportCategories
        )                                                                  
    } catch {
        Logger.error("%@", String(
            format: "Journey SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }                                   
    ```

### Events tracking

In order to receive the list of generated events within Journey module, you have to assign the instance of the tracker to the Journey module instance as follows and implement the required methods:

```swift
JourneySdk.shared.tracker = self
```

## :rocket: Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.

```swift
guard let journeyViewController = JourneySdk.shared.rootViewController else {
  return nil
}
journeyViewController.showBack = false // Hide back button embedded in the first screen
```

If you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`. 

=== "Using a `NavigationController`"

    ```swift
    navigationController?.pushViewController(journeyViewController, animated: false)
    ```

=== "Using a `ChildViewController`"

    ```swift
    yourViewController.addChild(UINavigationController(
      rootViewController: journeyViewController
    ))
    ```

### :fontawesome-solid-file-code: `JourneysRequest`

The `JourneysRequest` object allows to configure the first itinerary search at screen launch. It has the following parameters:

| Name | Description | Type | Default |
| --- | --- | --- | --- |
| `additionalTimeAfterFirstSectionTaxi` | Additional time after first taxi section | `Int` | `nil` |
| `additionalTimeBeforeLastSectionTaxi` | Additional time before last taxi section | `Int` | `nil` |
| `allowedId` | Allowed Navitia object IDs | `Set<String>` | `[]` |
| `bikeSpeed` | Bike speed | `Float` | `nil` |
| `bssSpeed` | BSS speed | `Float` | `nil` |
| `carNoParkSpeed` | Car no park speed | `Float` | `nil` |
| `carSpeed` | Car speed | `Float` | `nil` |
| `count` | The number of journeys to be displayed | `Int` | `nil` |
| `dataFreshness` | To indicate if theoretical or realtime data are requested | [`DataFreshness`](#datafreshness) | `.base_schedule` |
| `dateTime` | Requested date and time for journey results | `DateTime` | `nil` |
| `dateTimeRepresents` | Whether the datetime represents the departure or arrival | [`DateTimeRepresents`](#datetimerepresents) | `.departure` |
| `depth` | The request depth | `Int` | `nil` |
| `destinationId` | Destination Navitia ID | `String` | `""` |
| `destinationLabel` | Destination label, if not set the address will be displayed | `String` | `""` |
| `directPath` | Set the direct path of the journey | [`DirectPath`](#directpath) | `.indifferent` |
| `disruptionActive` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Bool` | `nil` |
| `equipmentDetails` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Bool` | `nil` |
| `freeRadiusFrom` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `freeRadiusTo` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `isJourneySchedules` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Bool` | `nil` |
| `maxBikeDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxBikeDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxBssDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxBssDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxCarDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxCarDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxCarNoParkDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxCarNoParkDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxNbJourneys` | The max number of journeys to be displayed | `Int` | `nil` |
| `maxNbTransfers` | The max number of public transport transfers | `Int` | `nil` |
| `maxRidesharingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxRidesharingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxTaxiDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxTaxiDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWaitingDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWalkingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWalkingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `minNbJourneys` | The min number of journeys to be displayed | `Int` | `nil` |
| `minNbTransfers` | The min number of public transport transfers | `Int` | `nil` |
| `originId` | Origin Navitia ID | `String` | `""` |
| `originLabel` | Origin label, if not set the address will be displayed | `String` | `""` |
| `ridesharingSpeed` | Ridesharing speed | `Float` | `nil` |
| `taxiSpeed` | Taxi speed | `Float` | `nil` |
| `timeframeDuration` | Taxi speed | `Int` | `nil` |
| `travelerType` | Traveler type | [`TravelerType`](#travelertype) | `.standard` |
| `walkingSpeed` | Walking speed | `Float` | `nil` |
| `wheelchair` | Check on [Navitia](https://doc.navitia.io/#journeys)  | `Bool` | `nil` |

#### :fontawesome-solid-file-code: `DataFreshness`

| Enum value | Description |
| --- | --- |
| `base_schedule` | Get disrupted journeys with the given results |
| `realtime` | Avoid disrupted journeys |

#### :fontawesome-solid-file-code: `DateTimeRepresents`

| Enum value | Description |
| --- | --- |
| `arrival` | The requestd datetime represents the arrival of the journey |
| `departure` | The requested datetime represents the departure of the journey |

#### :fontawesome-solid-file-code: `DirectPath`

| Enum value | Description |
| --- | --- |
| `indifferent` | Default value |
| `none` | For journeys using some public transport |
| `only` | For journeys without public transport |
| `onlyWithAlternatives` | For journeys with specific bike |

#### :fontawesome-solid-file-code: `TravelerType`

| Enum value | Description |
| --- | --- |
| `fast_walker` | Fast walker |
| `luggage` | With luggage |
| `slow_walker` | Slow walker |
| `standard` | Standard profile |
| `wheelchair` | Using wheelchair |

## :mega: Communicating with other modules or the app

Bookmark module can exchange data with or navigate to either other modules or the host application.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules or the app. Communication will not occur unless those are registered beforehand:

``` swift
try Router.shared
    .register(journey: JourneySdk.shared.journeyRouter)
    ... // Register modules and/or app
    .initialize()
```

### Application

#### Result journeys / Roadmap view injection

You can inject some external view that will be shown inside the journey module screens. In order to make it happen, you need to add the reference to the `injectableViewDelegate` as follows:

``` swift
JourneySdk.shared.injectableViewDelegate = self
```

The protocol provides the following methods:

``` swift
func allowExternalViewInjectionFor(screen: InjectableScreen, inputData: Any?) -> ExternalViewInjectionState {
  // Allow or not the external view injection
}
```

``` swift
func buildExternalViewFor(screen: InjectableScreen, inputData: Any?) -> UIView? {
  // Put the view that needs to be injected in the injectable screen
}
```

!!! info "Note"

	The `inputData` can be of type:

	- `SharedJourneysScreenData` if the injectable screen is `listJourneys`
	- `SharedRoadmapScreenData` if the injectable screen is `roadmap`

:fontawesome-solid-file-code: `SharedJourneysScreenData`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `hasResults` | Whether the request has results or not | `Bool` |
| `selectedFilterType` | The selected tab | `TransportModesFilterType` |

:fontawesome-solid-file-code: `SharedRoadmapScreenData`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `journeysRequest` | The request parameters object | `JourneysRequest` |
| `selectedJourney` | The selected journey data | `SharedSelectedJourneyModel` |

:fontawesome-solid-file-code: `SharedSelectedJourneyModel`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `departureTime` | The departure time | `Date` |
| `arrivalTime` | The arrival time | `Date` |
| `departureAddress` | The departure address | `String` |
| `arrivalAddress` | The arrival address | `String` |
| `departureCoordinates` | The departure coordinates | `CLLocationCoordinate2D` |
| `arrivalCoordinates` | The arrival coordinates | `CLLocationCoordinate2D` |
| `sections` | The list of journey sections | `[SectionModel]` |

:fontawesome-solid-file-code: `SectionModel`<br>

| Name | Description | Type |
| --- | --- | :---: |
| `departureTime` | The departure time | `Date` |
| `arrivalTime` | The arrival time | `Date` |
| `departureAddress` | The departure address | `String` |
| `arrivalAddress` | The arrival address | `String` |
| `departureCoordinates` | The departure coordinates | `CLLocationCoordinate2D` |
| `arrivalCoordinates` | The arrival coordinates | `CLLocationCoordinate2D` |
| `mobilityType` | The mobility type | `MobilityType` |
| `distance` | The distance in meters | `Int` |
| `duration` | The duration in seconds | `Int` |
| `additionalInformation` | The extra section information if the mobility type allows it | `Any?` |

!!! info "Note"

	Please note that the `additionalInformation` object can be of type:

	- `StreetNetworkSectionModel` if the `mobilityType` is `streetNetwork`
	- `PublicTransportSectionModel` if the `mobilityType` is `public_transport`
	- `CarParkingSectionModel` if the `mobilityType` is `carParking`


#### Roadmap actions

You can add some actions to the roadmap screen which can be configured using this appropriate delegate:

``` swift
JourneySdk.shared.delegate = self
```

The designated protocol offers the following methods:

``` swift
func allowedRoadmapScreenActionsFor(inputData: SharedRoadmapScreenData) -> AllowedRoadmapScreenActions {
	// Define the allowed actions on the roadmap screen
}

func onPrimaryButtonActionTriggered(inputData: SharedRoadmapScreenData) {
	// Handle primary action button click
}

func onSecondaryButtonActionTriggered(inputData: SharedRoadmapScreenData) {
	// Handle secondary action button click
}
```

#### Roadmap navigation

A journey may include sections for driving, walking, or cycling. This module provides the option in the Roadmap screen to enhance navigation accuracy using data from an external service.<br>
To enable this feature, first enable the `external_navigation` parameter in the [features configuration](../../getting_started/#journey-features). Then, implement the following method:

``` swift
func onLaunchExternalNavigationApp(from: CLLocationCoordinate2D, to: CLLocationCoordinate2D, navigationMode: JourneyExternalNavigationMode) {
	// launch your external navigation service screen or your custom screen
}
```

| Param | Type | Description |
| --- | --- | --- |
| `from` | `LatLng` | Section departure coordinates |
| `toCoords` | `LatLng` | Section arrival coordinates |
| `navigationMode` | `JourneyExternalNavigationMode` | Section navigation mode |

!!! info "Note"

    `JourneyExternalNavigationMode` has 3 modes of transportation that describe the section: `bike`, `car`, and `walking`.

### Modules

#### Bookmark

:octicons-arrow-right-24: Enabling<br>

Journey module communicates with [Bookmark](../../bookmark/ios) module in order to display favorite stations, journeys and POIs. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#journey-features).<br>

:octicons-arrow-right-24: Methods<br>

The following methods from the `CustomJourneyBookmarkDelegate` interface should be implemented by the host application to enable navigation to the Bookmark module or any other custom screen. Note that the parameters of these methods can be omitted as needed.f you don't implement this protocol, the Bookmark module will be shown.

This method is called after click on the favorite home shortcut button, in case it is empty.

``` swift
func onHomeAddressCompletionRequested(module: Router.BookmarkLinkedModule) {
    // launch the bookmark module screen or your custom screen
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `module` | `Router.BookmarkLinkedModule` | Module triggering the method call | `Router.BookmarkLinkedModule.aroundMe` or `Router.BookmarkLinkedModule.journey` |

This method is called after click on the favorite work shortcut button, in case it is empty.

``` swift
func onWorkAddressCompletionRequested(module: Router.BookmarkLinkedModule) {
    // launch the bookmark module screen or your custom screen
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `module` | `Router.BookmarkLinkedModule` | Module triggering the method call | `Router.BookmarkLinkedModule.aroundMe` or `Router.BookmarkLinkedModule.journey` |
