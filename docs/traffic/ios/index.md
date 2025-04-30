---
title: Traffic iOS - Navitia SDK Docs
---

# Traffic iOS

## :computer: Setup

In your project, add the following lines to your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Traffic podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'TrafficSDK', '4.2.0' # Traffic Pod definition
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

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding

This module is set up by calling `Traffic.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `token` | :material-check: | Navitia token | `String` | `ABCD-1234-...` |
| `timeZone` | :material-check: | Time zone | `String` | `Europe/Paris` |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `alertCredentials` | :material-close: | Kronos alert subscription credentials| [`TrafficAlertSubscriptionCredentials`](#traffic-alert-subscription-credentials) | - |
| `colors` | :material-check: | Define the custom colors | [`TrafficColorsConfiguration`](../../getting_started/#traffic-color) | - |
| `unifiedColors` | :material-close: | Define the custom colors | [`UnifiedColorsConfiguration`](../../getting_started/#unified_colors) | - |
| `fonts` | :material-close: | Use custom fonts | [`TrafficFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `providerResources` | :material-close: | Transport providers configuration | [`[ProviderResource]`](../../getting_started/#provider-resource) | - |
| `transportCategories` | :material-close: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `networkResources` | :material-close: | List of network resource IDs | [`[NetworkResource]`](../../getting_started/#network-resource) | - |
| `features` | :material-close: | Enable/disable some features  | [`TrafficFeaturesConfiguration`](../../getting_started/#traffic-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile` | :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

=== "Configuration with file"

    ```swift
    do {
        try Traffic.shared.initialize(
            token: "your_token", 
            configurationJsonFile: "traffic_configuration.json"
        )                                       
    } catch {
        Logger.error("%@", String(
            format: "Traffic SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }
    ```

=== "Manual configuration"

    ```swift
    do {
        let transportCategories = [TransportCategory(
            modules: ["traffic"],
            iconRes: "ic_section_mode_metro",
            nameRes: "metro",
            selected: true,
            modes: [TransportCategoryMode(
                physical: TransportPhysicalMode(
                    id: "physical_mode:Metro", 
                    nameRes: "metro"
                ),
                commercial: TransportCommercialMode(
                    id: "commercial_mode:Metro", 
                    name: "Metro"
                )
            )],
            firstSectionModes: ["walking"],
            lastSectionModes: ["walking"]
        )]
        let trafficColorsConfiguration = TrafficColorsConfiguration(
            primaryColor: "#88819f", 
            secondaryColor: "#8faa96"
        )
                                                                          
        try Traffic.shared.initialize(
         	coverage: "fr-idf",
            token: "your_token",
            timeZone: "your_country",
            env: "PROD",
            colors: trafficColorsConfiguration,
            transportCategories: transportCategories
        )                                                                  
    } catch {
        Logger.error("%@", String(
            format: "Traffic SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
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

### Events tracking

In order to receive the list of generated events within Traffic module, you have to assign the instance of the tracker to the Traffic module instance as follows and implement the required methods:

```swift
Traffic.shared.tracker = self
```

## :rocket: Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.

```swift
guard let trafficViewController = Traffic.shared.rootViewController else {
	return nil
}
trafficViewController.showBack = false // Hide back button embedded in the first screen
```

If you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`. 

=== "Using a `NavigationController`"

    ```swift
    navigationController?.pushViewController(trafficViewController, animated: false)
    ```

=== "Using a `ChildViewController`"

    ```swift
    yourViewController.addChild(UINavigationController(
    	rootViewController: trafficViewController
    ))
    ```
