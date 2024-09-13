---
title: Around Me iOS - Navitia SDK Docs
---

# Around Me iOS

## :computer: Setup

In your project, add the following lines to your `Podfile`:

``` ruby
source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Around Me podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'AroundMeSDK', '3.7.0' # Around Me Pod definition
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

=== "Configuration with file"

    ```swift
    do {
        try AroundMe.shared.initialize(
            token: "your_token", 
            configurationJsonFile: "aroundme_configuration.json"
        )                                                               
    } catch {
        Logger.error("%@", String(
            format: "Around Me SDK cannot be initialized! %@", 
            error.localizedDescription)
        )
    }                                   
    ```

=== "Manual configuration"

    ```swift
    do {
        let transportCategories = [TransportCategory(
            modules: ["aroundme"],
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
        let aroundmeColorsConfiguration = AroundMeColorsConfiguration(
            primaryColor: "#88819f", 
            secondaryColor: "#8faa96"
        )
                                                                          
        try AroundMe.shared.initialize(
            coverage: "fr-idf",
            token: "your_token",
            env: "PROD",
            colors: aroundmeColorsConfiguration,
            transportCategories: transportCategories
        )                                                                  
    } catch {
        Logger.error("%@", String(
            format: "Around Me SDK cannot be initialized! %@", 
            error.localizedDescription
        ))
    }                                   
    ```

### Events tracking

In order to receive the list of generated events within Around Me module, you have to assign the instance of the tracker to the Around Me module instance as follows and implement the required methods:

```swift
AroundMe.shared.tracker = self
```

## :rocket: Launching

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.

``` swift
guard let aroundMeViewController = AroundMe.shared.rootViewController else {
  return nil
}
aroundMeViewController.showBack = false // Hide back button embedded in the first screen
```

If you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`. 

=== "Using a `NavigationController`"

    ```swift
    navigationController?.pushViewController(
        trafficViewController,
        animated: false
    )
    ```

=== "Using a `ChildViewController`"

    ```swift
    yourViewController.addChild(UINavigationController(
        rootViewController: trafficViewController
    ))
    ```

### Filters

This screen content is a visual version of the passed transport categories and POI categories configuration (check [modules configuration](../../getting_started/#modules-configuration) section for more information). The selected elements will be used to filter the data received and drawn within the map. One filter should at least be selected or else the user can't apply the current filters configuration.<br><br>
If you want to reset the user filters configuration, you can simply call `AroundMeUI.getInstance().resetUserPreferences()` and the current configuration will be deleted and the screen will be updated according to the new passed configuration.

## :mega: Communicating with other modules or the app

Around Me module can exchange data with or navigate to either other modules or the host application.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules or the app. Communication will not occur unless those are registered beforehand:

``` swift
try Router.shared
          .register(aroundMe: AroundMe.shared.aroundMeRouter)
          ... // Register modules and/or app
          .initialize()
```

### Modules

#### Bookmark

:octicons-arrow-right-24: Enabling<br>

`Around Me` module communicates with [Bookmark](../../bookmark/ios) module in order to vizualize favorite stations, POIs and journeys. You should enable the `bookmark_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

Bookmark module must be registered in the `Router` to build the connection between these modules:

``` swift
Router.shared.register(bookmark: Bookmark.shared.bookmarkRouter)
```

:octicons-arrow-right-24: Methods<br>

The following methods from the `CustomAroundMeBookmarkDelegate` interface should be implemented by the host application to enable navigation to the Bookmark module or any other custom screen. Note that the parameters of these methods can be omitted as needed. If you don't implement this protocol, the Bookmark module will be shown.

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
    // launch the bookmark module screen or your custom screen if the favorite work address is empty
}
```

| Param | Type | Description | Value |
| --- | --- | --- | --- |
| `module` | `Router.BookmarkLinkedModule` | Module triggering the method call | `Router.BookmarkLinkedModule.aroundMe` or `Router.BookmarkLinkedModule.journey` |

``` swift
func onSeeAllFavoritesClicked() {
    // launch the bookmark module screen or your custom screen
  }
```

#### Journey

:octicons-arrow-right-24: Enabling<br>

`Around me` module communicates with [Journey](../../journey/ios) module in order to get directions for a chosen itinerary. You should enable the `journey_mode` and the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
Another way to communicate with is through the [Map](../screens/#map) screen and precisely the _Where are we going?_ button, this feature should also be enabled by setting the `where_shall_we_go` in the [features configuration](../../getting_started/#around-me-features) to `true`.<br>

Journey module must also be registered in the `Router` to build the connection between these modules:
``` swift
Router.shared.register(journey: JourneySdk.shared.journeyRouter)
```

#### Traffic

:octicons-arrow-right-24: Enabling<br>

`Around me` module communicates with [Traffic](../../traffic/ios) module in order to easily access traffic information. You should enable the `traffic_mode` parameter in the [features configuration](../../getting_started/#around-me-features).<br>

Traffic module must also be registered in the `Router` to build the connection between these modules:

``` swift
Router.shared.register(traffic: Traffic.shared.trafficRouter)
```
