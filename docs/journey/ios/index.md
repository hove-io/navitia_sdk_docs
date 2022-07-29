# Journey iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

```ruby
platform :ios, '13.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'JourneySDK', '~> 5.0.0' # Journey Pod definition
end
```

Using your CLI, run `pod install` in your project directory.

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `JourneySdk.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage`| :material-check: | Navitia coverage | `String` | `fr-idf` |
| `token`| :material-check: | Navitia token | `String` | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `env`| :material-check: | Navitia environment | `String` | `PROD` |
| `colors`| :material-check: | Define the custom colors | [`JourneyColorsConfiguration`](../../getting_started/#journey-color) | - |
| `fonts`| :material-close: | Use custom fonts | [`JourneyFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources`| :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources`| :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories`| :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `providerResources`| :material-close: | Transport providers configuration | [`[ProviderResource]`](../../getting_started/#provider-resource) | - |
| `titleResources`| :material-close: | Screens titles customization | [`JourneyTitlesResources`](../../getting_started/#journey-title-resource) | - |
| `features`| :material-close: | Enable/disable some features  | [`JourneyFeaturesConfiguration`](../../getting_started/#journey-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile`| :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

```swift
do {
    let transportCategories = [TransportCategory(modules: ["journey"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 modes: [TransportCategoryMode(physical: TransportPhysicalMode(id: "physical_mode:Metro", nameRes: "metro"),
                                                 commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"])
                              ]
                              
    let journeyColorsConfiguration = JourneyColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                                                                      
    try JourneySdk.shared.initialize(coverage: "fr-idf",
                                    token: "0de19ce5-e0eb-4524-a074-bda3c6894c19",
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
    try JourneySdk.shared.initialize(configurationJsonFile: "journey_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. 

```swift
guard let journeyViewController = JourneySdk.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(journeyViewController, animated: false)
```

## 📱 Screens

### Journeys

The journeys screen is fundamental and offers the solutions to the user for the requested itinerary.
After defining all the required parameters, this screen will popup with multiple results combining public transport, personal bikes/cars, bike sharing system and even ridesharing possibilities.

Each result gives the needed information to the user in order to planify his journey. He can check the duration, the suggested means of transport, the next departure datetimes and many other useful details. This combination of data, being served by <a href="https://doc.navitia.io" target="_blank">Navitia</a> servers and translated into a comprehensible/user friendly interface, is perfectly shaped to the user profile and needs.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_journeys_screen.png" alt="Journeys screen">

### Search

The search feature can be enabled in the configuration by setting the parameter `search` to `true` as mentioned in the [Journey features](../../getting_started/#journey-features) section.<br>
In this screen, the user can choose the departure and the arrival of his itinerary. While typing in the target field, a list of options is shown below the field. The user can simply choose one of the suggested options and mark it as a departure or as an arrival point.<br>

The suggested options are grouped in sections, it's whether a station, an address or a place.
In this screen, a geolocation service is used to get the user location. Therefore, another option is given and it allows the user to set his position as a departure or an arrival of the itinerary.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_autocompletion_screen.png" alt="Autocompletion screen">

### Roadmap

We believe that the user needs more useful details about his journey and that's where the roadmap screen comes in. In this page, the user gets a visual overview about the selected itinerary with a simple colorful drawing on a map. Departure and arrival markers are also shown on the map along with the user location and itinerary segments delimiters.

The screen also includes a draggable bottom sheet which offers a step-by-step journey sections. Each section is represented in a way that it makes it easier to the user to follow the given instructions. The public transport section is also well detailed when it comes to explain to the user how to take different means of transport from the departure to the arrival point.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_roadmap_screen.png" alt="Roadmap screen">

### Ridesharing offers

This screen lists the different ridesharing offers for the selected journey. Regardless of the fact that the journey can propose a full ridesharing trip or a partial ride, the user can select among different third party offers. He has all the information needed to choose the best offer that fits his needs including the departure time, the available seats, the price and some data about the driver offering the ride.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/journey_ios_ridesharing_offers_screen.png" alt="Ridesharing offers screen">

## 🗺 Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/journey_ios_navigating.png" alt="Navigating">
