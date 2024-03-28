---
title: Around Me iOS - Navitia SDK Docs
---

# Around Me iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

``` ruby
platform :ios, '14.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Around Me podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'AroundMeSDK', '3.5.0' # Around Me Pod definition
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

This module is set up by calling `AroundMe.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `colors` | :material-check: | Define the custom colors | [`AroundMeColorsConfiguration`](../../getting_started/#around-me-color) | - |
| `fonts` | :material-close: | Use custom fonts | [`AroundMeFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories` | :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `poiCategories` | :material-close: | List of available POIs | [`[PoiCategory]`](../../getting_started/#poi-category) | - |
| `providerResources` | :material-close: | Transport providers configuration | [`[ProviderResource]`](../../getting_started/#provider-resource) | - |
| `titleResources` | :material-close: | Screens titles customization | [`AroundMeTitlesResources`](../../getting_started/#around-me-title-resource) | - |
| `features` | :material-close: | Enable/disable some features  | [`AroundMeFeaturesConfiguration`](../../getting_started/#around-me-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile` | :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

``` swift
do {
    let transportCategories = [TransportCategory(modules: ["aroundme"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 modes: [TransportCategoryMode(physical: TransportPhysicalMode(id: "physical_mode:Metro", nameRes: "metro"),
                                                 commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"])
                              ]
                              
    let aroundmeColorsConfiguration = AroundMeColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                                                                      
    try AroundMe.shared.initialize(coverage: "fr-idf",
                                   token: "your_token",
                                   env: "PROD",
                                   colors: aroundmeColorsConfiguration,
                                   transportCategories: transportCategories)                                                                  
} catch {
    Logger.error("%@", String(format: "Around me SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

<h4>Example with JSON file</h4>

``` swift
do {
    try AroundMe.shared.initialize(token: "your_token", configurationJsonFile: "aroundme_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Around me SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.
Please note that if you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`.  

``` swift
guard let aroundMeViewController = AroundMe.shared.rootViewController else {
  return nil
}

// Hide back button embedded in the first screen
aroundMeViewController.showBack = false

// With a NavigationController
navigationController?.pushViewController(aroundMeViewController, animated: false) // (1)

// With a ChildViewController
yourViewController.addChild(UINavigationController(rootViewController: aroundMeViewController)) // (2)
```

1.  Use this code if you're using your own NavigationController
2.  Use this code if you're using a ChildViewController

## 📱 Screens

### Map

The map screen represents the main screen of this module. It shows the places nearby the center of the visible region, draws them on the map and adds them to the bottom sliding panel.<br>
The shown data depend on the selected elements in the [filters](#filters) screen.

In the bottomsheet of the main screen, the last added favorite stations are shown with the next departures for each direction, as well as an All Favorites button that redirects the user to the bookmark module. In the same section, if the user has added his journeys to favorites in journey module, a favorite journeys section appears showing the list of bookmarked journeys.


<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_map_screen.png" alt="Map screen">

In the details bottomsheet of a station or a POI, there is a star button in order to save or delete it from the bookmarks.
<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_bookmark_saving_node.png" alt="Bookmark node">

### Search

The search screen allows the user to seek for a place using a built-in autocompletion. The result is a selection of addresses, stations and points of interest based on the user search input text.<br>
If an element is selected, this screen will disappear and the map will be centered over the selected item location.
Please note that a history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_search_screen.png" alt="Search screen">

### Filters

This screen content is a visual version of the passed transport categories and POI categories configuration (check [modules configuration](../../getting_started/#modules-configuration) section for more information). The selected elements will be used to filter the data received and drawn within the map. One filter should at least be selected or else the user can't apply the current filters configuration.<br><br>
If you want to reset the user filters configuration, you can simply call `AroundMeUI.getInstance().resetUserPreferences()` and the current configuration will be deleted and the screen will be updated according to the new passed configuration.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_filters_screen.png" alt="Filters screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens:

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/aroundme_ios_screen_flow.png" alt="Screen flow">

## 📢 Communicating with other modules

### Journey

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
When the user taps on a marker on the map, the buttons **Go from there** and **Go to there** should pop up as follows:

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_go_fromto.png" alt="Go from/to">

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.<br>

Another way to communicate with [Journey](../../journey/) module is through the [Map](#map) screen and precisely the **Where are we going?** button, this feature should also be enabled by setting the `journey_search_mode` in the [features configuration](../../getting_started/#around-me-features) to `true`.<br>

The `Router` module should also be initialized with the right parameters since it’s mandatory to build the connection between these modules:

``` swift
try Router.shared
          .register(journey: JourneySdk.shared.journeyRouter)
          .register(aroundMe: AroundMe.shared.aroundMeRouter)
          .register(app: self)
          .initialize()
```

### Bookmark

This module communicates with [Bookmark](../../bookmark/) module in order to vizualize favorite stations and POIs. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

The `Router` module should also be initialized with the right parameters since it’s mandatory to build the connection between these modules:

``` swift
try Router.shared
          .register(journey: JourneySdk.shared.journeyRouter)
          .register(aroundMe: Bookmark.shared.bookmarkRouter)
          .register(app: self)
          .initialize()
```

### Traffic

This module communicates with [Traffic](../../traffic/) module in order to easily access traffic information. You should enable the `traffic_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
A red traffic button will appear in the top right corner, only when the search bar is hidden.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_traffic_button.png" alt="Traffic mode">

The `Router` module should also be initialized with the right parameters since it’s mandatory to build the connection between these modules:

``` swift
try Router.shared
          .register(journey: JourneySdk.shared.journeyRouter)
          .register(aroundMe: Traffic.shared.trafficRouter)
          .register(app: self)
          .initialize()
```

### Application

Some callbacks are delegated to the application allowing it to receive some module events. To subscribe to those events, the delegate should be set as follows:

``` swift
AroundMe.shared.delegate = self
```

##### POI event

A customizable button appears in the POI details screen and the clicking event should be catched from the application. A POI ID is sent with the callback in order to identify the selected POI.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/aroundme_ios_poi_button_event.png" alt="POI button event">

### Crowdsourcing

⚠️ This section will be available soon!
