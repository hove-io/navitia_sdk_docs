---
title: Schedule iOS - Navitia SDK Docs
---

# Schedule iOS

## :computer: Setup

In your project, add the following lines to your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Schedule podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'ScheduleSDK', '3.7.0' # Schedule Pod definition
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

This module is set up by calling `Schedule.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `colors` | :material-check: | Define the custom colors | [`ScheduleColorsConfiguration`](../../getting_started/#schedule-color) | - |
| `fonts` | :material-close: | Use custom fonts | [`ScheduleFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories` | :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `networkResources` | :material-close: | List of network resource IDs | [`[NetworkResource]`](../../getting_started/#network-resource) | - |
| `features` | :material-close: | Enable/disable some features  | [`ScheduleFeaturesConfiguration`](../../getting_started/#schedule-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile` | :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

=== "Configuration with file"

    ```swift
    do {
        try Schedule.shared.initialize(
            token: "your_token", 
            configurationJsonFile: "schedule_configuration.json"
        )                                                               
    } catch {
        Logger.error("%@", String(
            format: "Schedule SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }                                   
    ```

=== "Manual configuration"

    ```swift
    do {
        let transportCategories = [TransportCategory(
            modules: ["schedule"],
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

        let scheduleColorsConfiguration = ScheduleColorsConfiguration(
            primaryColor: "#88819f", 
            secondaryColor: "#8faa96"
        )
                                                                          
        try Schedule.shared.initialize(
            coverage: "fr-idf",
            token: "your_token",
            env: "PROD",
            colors: scheduleColorsConfiguration,
            transportCategories: transportCategories
        )                                                                  
    } catch {
        Logger.error("%@", String(
            format: "Schedule SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }                                   
    ```

### Events tracking

In order to receive the list of generated events within Schedule module, you have to assign the instance of the tracker to the Schedule module instance as follows and implement the required methods:

```swift
Schedule.shared.tracker = self
```

## :rocket: Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.

```swift
guard let scheduleViewController = Schedule.shared.rootViewController else {
	return nil
}
scheduleViewController.showBack = false // Hide back button embedded in the first screen
```

If you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`. 

=== "Using a `NavigationController`"

    ```swift
    navigationController?.pushViewController(scheduleViewController, animated: false)
    ```

=== "Using a `ChildViewController`"

    ```swift
    yourViewController.addChild(UINavigationController(
        rootViewController: scheduleViewController
    ))
    ```

## :mega: Communicating with other modules

Schedule module navigate to other modules directly.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules. Communication will not occur unless those are registered beforehand:

``` swift
try Router.shared
    .register(schedule: Schedule.shared.scheduleRouter)
    ... // Register modules and/or app
    .initialize()
```

### Modules

#### Bookmark

Schedule module communicates with [Bookmark](../../bookmark/ios) module in order to display favorite stations. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#schedule-features).

Bookmark module must be registered in the `Router` to build the connection between these modules

``` swift
Router.shared.register(bookmark: Bookmark.shared.bookmarkRouter)
```

#### Journey

This module communicates with [Journey](../../journey/ios) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#schedule-features).<br>

Bookmark module must be registered in the `Router` to build the connection between these modules

``` swift
Router.shared.register(journey: JourneySdk.shared.journeyRouter)
```
