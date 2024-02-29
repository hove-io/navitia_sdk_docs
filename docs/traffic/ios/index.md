---
title: Traffic iOS - Navitia SDK Docs
---

# Traffic iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

```ruby
platform :ios, '14.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Traffic podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'TrafficSDK', '3.4.0' # Traffic Pod definition
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
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `alertCredentials` | :material-close: | Kronos alert subscription credentials| [`TrafficAlertSubscriptionCredentials`](#traffic-alert-subscription-credentials) | - |
| `colors` | :material-check: | Define the custom colors | [`TrafficColorsConfiguration`](../../getting_started/#traffic-color) | - |
| `fonts` | :material-close: | Use custom fonts | [`TrafficFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories` | :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `networkResources` | :material-close: | List of network resource IDs | [`[NetworkResource]`](../../getting_started/#network-resource) | - |
| `features` | :material-close: | Enable/disable some features  | [`TrafficFeaturesConfiguration`](../../getting_started/#traffic-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile` | :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

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

### Alert subscription

To enable the alert subscription feature, the following instructions are required:
- Add the [environment configuration](../../getting_started/#traffic-features)
- Pass the [Kronos API credentials](#traffic-alert-subscription-credentials) to the initialization method
- Set the firebase token `Traffic.shared.firebaseToken = "token"` once received from the Firebase API at runtime

#### Traffic alert subscription credentials

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `username` | :material-check: | Kronos authentication username | `String` |
| `password` | :material-check: | Kronos authentication password | `String` |

## 🚀  Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.
Please note that if you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`. 

```swift
guard let trafficViewController = Traffic.shared.rootViewController else {
  return nil
}

// Hide back button embedded in the first screen
trafficViewController.showBack = false

// With a NavigationController
navigationController?.pushViewController(trafficViewController, animated: false) // (1)

// With a ChildViewController
yourViewController.addChild(UINavigationController(rootViewController: trafficViewController)) // (2)
```

1.  Use this code if you're using your own NavigationController
2.  Use this code if you're using a ChildViewController

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
Some disruptions have messages with included hyperlinks. Those links are also accessible to the user and will redirect him to an external browser to view the related link.<br>

If the [alert subscription](#alert-subscription) feature is enabled, a bell button appears allowing the user to subscribe/unsubscribe to/from the line alerts.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_all_disruptions_screen.png" alt="All disruptions screen">

### Line selection

This screen includes an autocompletion that enables the user to search the transport line needed for alert subscription.<br>
The parameter [`transport_networks`](../../getting_started/#traffic-features) allows to show the network providing the searched line. 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_line_selection_screen.png" alt="Line selection screen">

### Subscription schedule

After selecting a line from the autocompletion screen, this screen appears giving the ability to the user to choose/modify the periods in which the alert subscription can be received.<br>
Please verify that you have passed valid [Kronos API credentials](#traffic-alert-subscription-credentials) to the module initialization method in order to ensure a successful alert subscription process.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_subscription_schedule_screen.png" alt="Subscription schedule screen">

### Subscriptions list

This screen lists all the alert subscriptions that the user have registered. The subscriptions are also grouped by transport categories allowing to filter the subscriptions depending on the impacted line transport mode.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/traffic_ios_subscriptions_list_screen.png" alt="Subscriptions list screen">

## 🗺 Screen flow

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/traffic_ios_screen_flow.png" alt="Screen flow">
