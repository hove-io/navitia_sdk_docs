---
title: Around Me iOS - Navitia SDK Docs
---

# Around Me iOS

## 💻 Setup

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

## 👨‍💻  Implementation

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
        try AroundMe.shared.initialize(token: "your_token", configurationJsonFile: "aroundme_configuration.json")                                                               
    } catch {
        Logger.error("%@", String(format: "Around me SDK cannot be initialized! %@", error.localizedDescription))
    }                                   
    ```

=== "Manual configuration"

    ```swift
    do {
        let transportCategories = [TransportCategory(modules: ["aroundme"],
                                                     iconRes: "ic_section_mode_metro",
                                                     nameRes: "metro",
                                                     selected: true,
                                                     modes: [TransportCategoryMode(physical: TransportPhysicalMode(id: "physical_mode:Metro", nameRes: "metro"),
                                                     commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                     firstSectionModes: ["walking"],
                                                     lastSectionModes: ["walking"])]
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

## 🚀  Launching

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
    navigationController?.pushViewController(trafficViewController, animated: false)
    ```

=== "Using a `ChildViewController`"

    ```swift
    yourViewController.addChild(UINavigationController(rootViewController: trafficViewController))
    ```

## 📱 Screens







### Filters

This screen content is a visual version of the passed transport categories and POI categories configuration (check [modules configuration](../../getting_started/#modules-configuration) section for more information). The selected elements will be used to filter the data received and drawn within the map. One filter should at least be selected or else the user can't apply the current filters configuration.<br><br>
If you want to reset the user filters configuration, you can simply call `AroundMeUI.getInstance().resetUserPreferences()` and the current configuration will be deleted and the screen will be updated according to the new passed configuration.



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

#### Intercepting Bookmark callbacks

In case you enable Bookmark feature in this module, some actions are defined by default to show Bookmark screen.
Now, it's possible to intercept these callbacks and implement your own way of displaying user favorite data.<br>

To do so, you will need to pass a `CustomAroundMeBookmarkDelegate` to the Around Me module instance.<br>
This will allow to access to the following callbacks :

``` swift
extension YourClass: CustomAroundMeBookmarkDelegate {

  func onHomeAddressCompletionRequested(module: Router.BookmarkLinkedModule) {
    // Called when the user taps on the Home button and the home favorite address is not filled yet
  }

  func onWorkAddressCompletionRequested(module: Router.BookmarkLinkedModule) {
    // Called when the user taps on the Work button and the home favorite work is not filled yet
  }

  func onSeeAllFavoritesClicked() {
    // Called when the user taps on All Favorites button in the bottom sheet tabs
  }
}
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
