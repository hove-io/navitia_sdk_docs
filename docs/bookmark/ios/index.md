---
title: Bookmark iOS - Navitia SDK Docs
---

# Bookmark iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

``` ruby
platform :ios, '14.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Bookmark podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'BookmarkSDK', '1.6.0' # Bookmark Pod definition
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

    Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!

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

This module has a single entry point. The parameter `showBack` handles the back button visibility on the first screen.
Please note that if you want to use the `rootViewController` as a `ChildViewController` of your `ViewController`, you should embed it in an `NavigationController`.

``` swift
guard let bookmarkViewController = Bookmark.shared.rootViewController else {
  return nil
}

// Hide back button embedded in the first screen
bookmarkViewController.showBack = false

// With a NavigationController
navigationController?.pushViewController(bookmarkViewController, animated: false) // (1)

// With a ChildViewController
yourViewController.addChild(UINavigationController(rootViewController: bookmarkViewController)) // (2)
```

1.  Use this code if you're using your own NavigationController
2.  Use this code if you're using a ChildViewController

## 📱 Screens

### Favorites

This screen lists all the favorite stations, Bike sharing service stations, car parkings and addresses added by the user through other UI modules (Around Me, Schedule...) or from within a 3rd party application.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/bookmark_ios_favorites_screen.png" alt="Favorites screen">

## 📖 Manipulating data

The module provides the ability to directly manipulate data for use in custom screens.

### Methods

The various CRD methods are accessed through `BookmarkUI.shared`.

<h4>Create</h4>

- Create a new favorite address. Returns a boolean if the creation has succeed or not.

``` swift
func addFavoriteAddress(_ address: SharedData.FavoriteAddress) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `address` | [`SharedData.FavoriteAddress`](#favorite-address) | Favorite address to create |

- Create a new favorite journey. Returns a boolean if the creation has succeed or not.

``` swift
func addFavoriteJourney(_ journey: SharedData.FavoriteJourney) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `journey` | [`SharedData.FavoriteJourney`](#favorite-journey) | Favorite journey to create |

- Create a new favorite POI. Returns a boolean if the creation has succeed or not.

``` swift
func addFavoritePoi(_ poi: SharedData.FavoritePoi) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `poi` | [`SharedData.FavoritePoi`](#favorite-poi)| Favorite POI to create |

- Create a new favorite station. Returns a boolean if the creation has succeed or not.

``` swift
func addFavoriteStation(_ station: SharedData.FavoriteStation) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `station` | [`SharedData.FavoriteStation`](#favorite-station)| Favorite station to create |

<h4>Read</h4>

- Fetch a favorite address data. Returns [`SharedData.FavoriteAddress`](#favorite-address) or `nil` if not found.

``` swift
func fetchFavoriteAddress(id: String) -> SharedData.FavoriteAddress?
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite address to fetch |

- Fetch all favorite addresses. Returns a list of [`SharedData.FavoriteAddress`](#favorite-address) or an empty list if there is no data.

``` swift
func fetchFavoriteAddresses(max: Int) -> [SharedData.FavoriteAddress]
```

| Param | Type | Description |
| --- | --- | --- |
| `max` | `Int` | Limit the result count. `0` for all data |

- Fetch all favorite journeys. Returns a list of [`SharedData.FavoriteJourney`](#favorite-journey) or an empty list if there is no data.

``` swift
func fetchFavoriteJourneys(max: Int) -> [SharedData.FavoriteJourney]
```

| Param | Type | Description |
| --- | --- | --- |
| `max` | `Int` | Limit the result count. `0` for all data |

- Get if a journey is added to favorites. Returns a boolean if the creation has succeed or not.

``` swift
func isJourneyInBookmark(journeyId: String) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `journeyId` | `String` | Id of the favorite journey to check |

- Fetch a favorite POI data. Returns [`SharedData.FavoritePoi`](#favorite-poi) or `nil` if not found.

``` swift
func fetchFavoritePoi(id: String) -> SharedData.FavoritePoi?
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite POI to fetch |

- Fetch all favorite POIs. Returns a list of [`SharedData.FavoritePoi`](#favorite-poi) or an empty list if there is no data.

``` swift
func fetchFavoritePois(max: Int) -> [SharedData.FavoritePoi]
```

| Param | Type | Description |
| --- | --- | --- |
| `max` | `Int` | Limit the result count. `0` for all data |

- Fetch a favorite station data. Returns [`SharedData.FavoriteStation`](#favorite-station) or `nil` if not found.

``` swift
func fetchFavoriteStation(stopAreaId: String, lineId: String) -> SharedData.FavoriteStation?
```

| Param | Type | Description |
| --- | --- | --- |
| `stopAreaId` | `String` | Navitia stop area id of the favorite station to fetch |
| `lineId` | `String` | Navitia line id of the favorite station to fetch |

- Fetch all favorite stations. Returns a list of [`SharedData.FavoriteStation`](#avorite-station) or an empty list if there is no data.

``` swift
func fetchFavoriteStations(max: Int) -> [SharedData.FavoriteStation]
```

| Param | Type | Description |
| --- | --- | --- |
| `max` | `Int` | Limit the result count. `0` for all data |

<h4>Delete</h4>

- Delete an existing favorite address. Returns a boolean if the creation has succeed or not.

``` swift
func deleteFavoriteAddress(id: String) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite address to delete |

- Delete an existing favorite journey. Returns a boolean if the creation has succeed or not.

``` swift
func deleteFavoriteJourney(id: String) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite journey to delete |

- Delete an existing favorite POI. Returns a boolean if the creation has succeed or not.

``` swift
func deleteFavoritePoi(id: String) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite POI to delete |

- Delete an existing favorite station. Returns a boolean if the creation has succeed or not.

``` swift
func deleteFavoriteStation(id: String) -> Bool
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite station to delete |

### Data

<h4>Favorite Address</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique address id | `String` |
| `name` | :material-check: | Address name | `String` |
| `houseNumber` | :material-check: | House number | `Int` |
| `address` | :material-check: | Address label | `String` |
| `city` | :material-check: | Address city | `String` |
| `zipCode` | :material-check: | Address postal code | `String` |
| `addressTypeId` | :material-check: | Address type `home`, `work` or `custom` | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4>Favorite Journey</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique journey id | `String` |
| `fromName` | :material-check: | Departure name | `String` |
| `fromId` | :material-check: | Departure Navitia id | `String` |
| `toName` | :material-check: | Arrival name | `String` |
| `toId` | :material-check: | Arrival Navitia id | `String` |
| `connectionModes` | :material-check: | Array of connection modes. For example: `["bike", "walking"]` | `[String]` |
| `sections` | :material-check: | Array of included journey sections | [`[SharedData.FavoriteJourneySection]`](#favorite-journey-section) |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4>Favorite Journey Section</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `type` | :material-check: | Section type. Example: `public_transport` | `String` |
| `mode` | :material-check: | Section mode. Example: `walking` | `String` |
| `lineId` | :material-check: | Navitia line id | `String` |
| `lineCode` | :material-check: | Navitia line code | `String` |
| `lineTextColor` | :material-check: | Navitia line text color in HEX format | `String` |
| `lineColor` | :material-check: | Navitia line color in HEX format | `String` |
| `commercialMode` | :material-check: | Navitia public transport commercial mode. Example: `commercial_mode:Bus` | `String` |
| `physicalMode` | :material-check: | Navitia public transport physical mode. Example: `physical_mode:Bus` | `String` |
| `duration` | :material-check: | Section duration in seconds | `Int` |

<h4>Favorite Poi</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique POI id | `String` |
| `coords` | :material-check: | POI coordinates | `CLLocationCoordinate2D` |
| `name` | :material-check: | POI name | `String` |
| `address` | :material-check: | POI address | `String` |
| `type` | :material-check: | POI type | `String` |
| `typeId` | :material-check: | Navitia POI type ID. Example: `poi_type:amenity:hospital` | `String` |
| `network` | :material-check: | Navitia POI network | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4>Favorite Station</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `stopAreaId` | :material-check: | Navitia stop area id | `String` |
| `coords` | :material-check: | Station coordinates | `CLLocationCoordinate2D` |
| `name` | :material-check: | Station name | `String` |
| `lineId` | :material-check: | Navitia line id | `String` |
| `lineCode` | :material-check: | Line code | `String` |
| `lineColor` | :material-check: | Line color in HEX format | `String` |
| `lineTextColor` | :material-check: | Line text color in HEX format | `String` |
| `commercialMode` | :material-check: | Navitia public transport commercial mode. Example: `commercial_mode:Bus` | `String` |
| `physicalMode` | :material-check: | Navitia public transport physical mode. Example: `physical_mode:Bus` | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

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
