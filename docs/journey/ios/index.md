# Journey iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

```ruby
platform :ios, '13.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'JourneySDK', '5.5.0' # Journey Pod definition
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

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

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

```swift
do {
    let transportCategories = [TransportCategory(modules: ["journey"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 modes: [TransportCategoryMode(physical: TransportPhysicalMode(id "physical_mode:Metro"),
                                                                               commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                 networks: [],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"],
                                                 directPathModes: ["walking"],
                                                 addPoiInfos: [])]
            
    let journeyColorsConfiguration = JourneyColorsConfiguration(primary: "#88819f", secondary: "#8faa96")
                                                                      
    try JourneySdk.shared.initialize(coverage: "fr-idf",
                                    token: "your_token",
                                    env: "PROD",
                                    colors: journeyColorsConfiguration,
                                    transportCategories: transportCategories)                                                                  
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

<h4>Example with JSON file</h4>

```swift
do {
    try JourneySdk.shared.initialize(token: "your_token", configurationJsonFile: "journey_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

### Events tracking

In order to receive the list of generated events within Journey module, you have to assign the instance of the tracker to the Journey module instance as follows and implement the required methods:

```swift
JourneySdk.shared.tracker = self
```

## 🚀  Launching

This module has a single entry point. 

```swift
if let journeyViewController = JourneySdk.shared.rootViewController {
  navigationController?.pushViewController(journeyViewController, animated: false)
}
```

### JourneysRequest

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
| `maxNbJourneys` | The max number of journeys to be displayed | `Int` | `-1` |
| `maxNbTransfers` | The max number of public transport transfers | `Int` | `-1` |
| `maxRidesharingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxRidesharingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxTaxiDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxTaxiDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWaitingDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWalkingDirectPathDuration` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `maxWalkingDurationToPt` | Check on [Navitia](https://doc.navitia.io/#journeys) | `Int` | `nil` |
| `minNbJourneys` | The min number of journeys to be displayed | `Int` | `-1` |
| `minNbTransfers` | The min number of public transport transfers | `Int` | `-1` |
| `originId` | Origin Navitia ID | `String` | `""` |
| `originLabel` | Origin label, if not set the address will be displayed | `String` | `""` |
| `ridesharingSpeed` | Ridesharing speed | `Float` | `nil` |
| `taxiSpeed` | Taxi speed | `Float` | `nil` |
| `timeframeDuration` | Taxi speed | `Int` | `nil` |
| `travelerType` | Traveler type | [`TravelerType`](#travelertype) | `.standard` |
| `walkingSpeed` | Walking speed | `Float` | `nil` |
| `wheelchair` | Check on [Navitia](https://doc.navitia.io/#journeys)  | `Bool` | `nil` |

#### DataFreshness

| Enum value | Description |
| --- | --- |
| `base_schedule` | Get disrupted journeys with the given results |
| `realtime` | Avoid disrupted journeys |

#### DateTimeRepresents

| Enum value | Description |
| --- | --- |
| `arrival` | The requestd datetime represents the arrival of the journey |
| `departure` | The requested datetime represents the departure of the journey |

#### DirectPath

| Enum value | Description |
| --- | --- |
| `indifferent` | Default value |
| `none` | For journeys using some public transport |
| `only` | For journeys without public transport |
| `onlyWithAlternatives` | For journeys with specific bike |

#### TravelerType

| Enum value | Description |
| --- | --- |
| `fast_walker` | Fast walker |
| `luggage` | With luggage |
| `slow_walker` | Slow walker |
| `standard` | Standard profile |
| `wheelchair` | Using wheelchair |

## 📱 Screens

### Journeys

The journeys screen is fundamental and offers the solutions to the user for the requested itinerary.
After defining all the required parameters, this screen will popup with multiple results combining public transport, personal bikes/cars, bike sharing system and even ridesharing possibilities.

Each result gives the needed information to the user in order to planify his journey. He can check the duration, the suggested means of transport, the next departure datetimes and many other useful details. This combination of data, being served by <a href="https://doc.navitia.io" target="_blank">Navitia</a> servers and translated into a comprehensible/user friendly interface, is perfectly shaped to the user profile and needs.

The journeys are grouped into categories represented by different tabs: public transport, walking, bike, car and ridesharing. The visibility of each tab depends on the passed [transport categories configuration](../../getting_started/#transport-category).<br>
In the public transport tab, the journeys are grouped in two sections: recommended journeys and other journeys. The recommended journey ensures to the user that the arrival date is respected and yet, the journey is reliable.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_journeys_screen.png" alt="Journeys screen">

In the bike tab, the bike journeys are classified depending on specific criteria: the fastest, the most comfortable and the most balanced. The cycling path percentage is also displayed to the user to help him choose the right journey. In the same tab, the journeys combining only bike sharing service and walking are also added.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_journeys_screen_bike_tab.png" alt="Bike tab">

Each made itinerary request is saved and shown to the user at the screen launch. The history can be easily deleted by choosing delete from the action menu of the target item.<br>
In the same screen, we also show the list of the favorite journeys that the user has added using the bookmark button (see [Roadmap](#roadmap) section below). To enable this feature, the `bookmark_mode`parameter should be set to `true` in [Journey features](../../getting_started/#journey-features).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_journeys_screen_history_favorite_journeys.png" alt="Journey - History and favorites">

### Search

The search feature can be enabled in the configuration by setting the parameter `search_only` to `false` as mentioned in the [Journey features](../../getting_started/#journey-features) section.<br>
In this screen, the user can choose the departure and the arrival of his itinerary. While typing in the target field, a list of options is shown below the field. The user can simply choose one of the suggested options and mark it as a departure or as an arrival point.<br>

The suggested options are grouped in sections, it's whether a station, an address or a place.
In this screen, a geolocation service is used to get the user location. Therefore, another option is given and it allows the user to set his position as a departure or an arrival of the itinerary.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

If `bookmark_mode` feature is enabled in the [Journey features](../../getting_started/#journey-features), a bookmark section appears in the same screen allowing the user to choose from his favorite addresses/places. A shortcut button is also available for Home and Work favorites.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_autocompletion_screen.png" alt="Autocompletion screen">

### Roadmap

We believe that the user needs more useful details about his journey and that's where the roadmap screen comes in. In this page, the user gets a visual overview about the selected itinerary with a simple colorful drawing on a map. Departure and arrival markers are also shown on the map along with the user location and itinerary segments delimiters.

The screen also includes a draggable bottom sheet which offers a step-by-step journey sections. Each section is represented in a way that it makes it easier to the user to follow the given instructions. The public transport section is also well detailed when it comes to explain to the user how to take different means of transport from the departure to the arrival point.

A customized button can be added in case an external action needs to be made from outside this screen. To enable this button, the parameter `buy_tickets` should be set in [Journey features](../../getting_started/#journey-features).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_roadmap_screen.png" alt="Roadmap screen">

### Ridesharing offers

This screen lists the different ridesharing offers for the selected journey. Regardless of the fact that the journey can propose a full ridesharing trip or a partial ride, the user can select among different third party offers. He has all the information needed to choose the best offer that fits his needs including the departure time, the available seats, the price and some data about the driver offering the ride.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_ridesharing_offers_screen.png" alt="Ridesharing offers screen">

### Navigation

This screen shows the different steps that the user should go through to reach his destination. Those steps are designed to be simple and easily readable for the user and focuses on the most important information during his journey.
Along with the user location, an interaction between the map and the step card is also added to zoom over the current portion of path that refers to the current selected card.

The journey duration and the estimated arrival time are realtime-updated variables which depend on various parameters such as the highlighted step, the next departure of each public transport mode...

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_navigation_screen.png" alt="Navigation screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/journey_ios_screen_flow.png" alt="Screen flow">

## 📢 Communicating with other modules

### Application

Some callbacks are delegated to the application allowing it to receive some module events. To subscribe to those events, the delegate should be set as follows:

``` swift
JourneySdk.shared.delegate = self
```

##### Roadmap button event

A customizable button appears in the roadmap screen and the clicking event should be catched from the application.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_roadmap_button_event.png" alt="Roadmap button event">
