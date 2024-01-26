---
title: Bookmark iOS - Navitia SDK Docs
---

# Bookmark iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

``` ruby
platform :ios, '13.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Around Me podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'BookmarkSDK', '1.3.0' # Around Me Pod definition
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

This module is set up by calling `Bookmark.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `env` | :material-check: | Navitia environment | `String` | `PROD` |
| `colors` | :material-check: | Define the custom colors | [`AroundMeColorsConfiguration`](../../getting_started/#around-me-color) | - |
| `fonts` | :material-close: | Use custom fonts | [`AroundMeFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources` | :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources` | :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories` | :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
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
                              
    let bookmarkColorsConfiguration = AroundMeColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                                                                      
    try Bookmark.shared.initialize(coverage: "fr-idf",
                                   token: "your_token",
                                   env: "PROD",
                                   colors: bookmarkColorsConfiguration,
                                   transportCategories: transportCategories)                                                                  
} catch {
    Logger.error("%@", String(format: "Bookmark SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

<h4>Example with JSON file</h4>

``` swift
do {
    try Bookmark.shared.initialize(token: "your_token", configurationJsonFile: "aroundme_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Bookmark SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. 

``` swift
guard let bookmarkViewController = Bookmark.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(bookmarkViewController, animated: false)
```

## 📱 Screens

### Favorites

This screen lists all the favorite stations, Bike sharing service stations, car parkings and addresses added by the user through other UI modules (Around Me, Schedule...) or from within a 3rd party application.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_ios_favorites_screen.png" alt="Favorites screen">

## 📢 Communicating with other modules

### Journey

This module communicates with [Journey](../../journey/) module in order to get directions for a chosen favorites element. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#around-me-features).<br>
When the user taps on a marker on the map, the buttons **Go from there** and **Go to there** should pop up as follows:

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_ios_go_fromto.png" alt="Go from/to">

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.<br>

The `Router` module should also be initialized with the right parameters since it’s mandatory to build the connection between these modules:

``` swift
try Router.shared
          .register(journey: JourneySdk.shared.journeyRouter)
          .register(aroundMe: Bookmark.shared.bookmarkRouter)
          .register(app: self)
          .initialize()
```
