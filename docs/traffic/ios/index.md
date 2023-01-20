# Traffic iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

```ruby
platform :ios, '13.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Traffic podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'TrafficSDK', '3.0.4' # Traffic Pod definition
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

This module is set up by calling `Traffic.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage`| :material-check: | Navitia coverage | `String` | `fr-idf` |
| `env`| :material-check: | Navitia environment | `String` | `PROD` |
| `colors`| :material-check: | Define the custom colors | [`TrafficColorsConfiguration`](../../getting_started/#traffic-color) | - |
| `fonts`| :material-close: | Use custom fonts | [`TrafficFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources`| :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources`| :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories`| :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `networkResources`| :material-close: | List of network resource IDs | [`[NetworkResource]`](../../getting_started/#network-resource) | - |
| `features`| :material-close: | Enable/disable some features  | [`TrafficFeaturesConfiguration`](../../getting_started/#traffic-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile`| :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

```swift
do {
    let transportCategories = [TransportCategory(modules: ["traffic"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 modes: [TransportCategoryMode(physical: TransportPhysicalMode(id: "physical_mode:Metro", nameRes: "metro"),
                                                 commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"])
                              ]
                              
    let trafficColorsConfiguration = TrafficColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                                                                      
    try Traffic.shared.initialize(coverage: "fr-idf",
                                    token: "your_token",
                                    env: "PROD",
                                    colors: trafficColorsConfiguration,
                                    transportCategories: transportCategories)                                                                  
} catch {
    Logger.error("%@", String(format: "Traffic SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

<h4>Example with JSON file</h4>

```swift
do {
    try Traffic.shared.initialize(token: "your_token", configurationJsonFile: "traffic_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Traffic SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. 

```swift
guard let trafficViewController = Traffic.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(trafficViewController, animated: false)
```

## 📱 Screens

### Home

The home screen allows the user to view all the line and network disruptions sorted by transport category.<br>
When clicking on a disrupted line, the message and the application period of the disruption shows up along with an **All disruptions** button. This button redirects the user to the [line disruptions](#linenetwork-disruptions) screen.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_home_screen.png" alt="Home screen">

#### Filters

The home screen integrated a menu accessible through the header right button. This menu shows the different transport categories with a default selection.<br>
If the user hits the **Apply** button after changing the selection state, the home screen will refresh and will show the disruptions according to the updated filters.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_filters_menu.png" alt="Filters menu">

### Line/network disruptions

This screen lists the disruptions related to the selected line or to all disrupted networks. Each element shows the title, the message and the application period of a target disruption.<br>
Some disruptions have messages with included hyperlinks. Those links are also accessible to the user and will redirect him to an external browser to view the related link.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_all_disruptions_screen.png" alt="All disruptions screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/traffic_ios_navigating.png" alt="Navigating">
