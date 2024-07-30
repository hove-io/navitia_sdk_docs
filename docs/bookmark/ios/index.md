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

In case you want to use your own screen to display favorites, it is possible to call data based methods.<br>
The following are available methods:

##### Add favorites
| Name | Description | Parameters | Result |
| --- | --- | --- | --- |
| `func addFavoriteAddress(_ address: SharedData.FavoriteAddress)` | Save a new favorite address | [`SharedData.FavoriteAddress`](#favorite-address) | `Bool`: success |
| `func addFavoriteJourney(_ journey: SharedData.FavoriteJourney)` | Save a new favorite journey | [`SharedData.FavoriteJourney`](#favorite-journey) | `Bool`: success |
| `func addFavoritePoi(_ poi: SharedData.FavoritePoi)` | Save a new favorite POI | [`SharedData.FavoritePoi`](#favorite-poi) | `Bool`: success |
| `func addFavoriteStation(_ station: SharedData.FavoriteStation)` | Save a new favorite station | [`SharedData.FavoriteStation`](#favorite-station) | `Bool`: success |

##### Delete favorites
| Name | Description | Parameters | Result |
| --- | --- | --- | --- |
| `func fetchFavoriteAddress(id: String)` | Delete an existing address | `id`: address id | `Bool`: success |
| `func deleteFavoriteJourney(id: String)` | Delete an existing journey | `id`: journey id | `Bool`: success |
| `func deleteFavoritePoi(id: String)` | Delete an existing POI | `id`: POI id | `Bool`: success |
| `func deleteFavoriteStation(id: String)` | Delete an existing station | `id`: station id | `Bool`: success |

##### Fetch favorites data
| Name | Description | Parameters | Result |
| --- | --- | --- | --- |
| `func fetchFavoriteAddress(id: String)` | Fetch an existing address data | `id`: address id | [`SharedData.FavoriteAddress?`](#favorite-address) or `null` if not found |
| `func fetchFavoriteAddresses(max: Int)` | Fetch all saved favorite addresses | `max`: limit the result count, `0` for all data | [`[SharedData.FavoriteAddress]`](#favorite-address) |
| `func fetchFavoriteJourneys(max: Int)` | Fetch all saved favorite journeys | `max`: limit the result count, `0` for all data | [`[SharedData.FavoriteJourney]`](#favorite-journey) |
| `func fetchFavoritePoi(id: String)` | Fetch an existing poi data | `id`: poi id | [`SharedData.FavoritePoi?`](#favorite-poi) |
| `func fetchFavoritePois(max: Int)` | Fetch all saved favorite POIs | `max`: limit the result count, `0` for all data | [`[SharedData.FavoritePoi]`](#favorite-poi) |
| `func fetchFavoriteStation(stopAreaId: String, lineId: String)` | Fetch an existing station data | `stopAreaId`: Navitia stop area ID, `lineId`: Navitia line ID | [`SharedData.FavoriteStation?`](#favorite-station) |
| `func fetchFavoriteStations(max: Int)` | Fetch all saved favorite stations | `max`: limit the result count, `0` for all data | [`[SharedData.FavoriteStation]`](#favorite-station) |
| `func isJourneyInBookmark(journeyId: String) -> Bool` | Fetch if a journey is added to favorites | `journeyId`: journey id | `Bool` |

#### Favorite Address

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique address ID | `String` |
| `name` | :material-check: | Address name | `String` |
| `houseNumber` | :material-check: | House number | `Int` |
| `address` | :material-check: | Address label | `String` |
| `city` | :material-check: | Address city | `String` |
| `zipCode` | :material-check: | Address zip code | `String` |
| `addressTypeId` | :material-check: | Address type `home`, `work` or `custom` | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

#### Favorite Journey

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique journey ID | `String` |
| `fromName` | :material-check: | Departure name | `String` |
| `fromId` | :material-check: | Departure Navitia ID | `String` |
| `toName` | :material-check: | Arrival name | `String` |
| `toId` | :material-check: | Arrival Navitia ID | `String` |
| `connectionModes` | :material-check: | Array of connection modes. For example: `["bike", "walking"]` | `[String]` |
| `sections` | :material-check: | Array of included journey sections | [`[SharedData.FavoriteJourneySection]`](#favorite-journey-section) |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

##### Favorite Journey Section

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `type` | :material-check: | Section type. Example: `public_transport` | `String` |
| `mode` | :material-check: | Section mode. Example: `walking` | `String` |
| `lineId` | :material-check: | Navitia line ID | `String` |
| `lineCode` | :material-check: | Navitia line code | `String` |
| `lineTextColor` | :material-check: | Navitia line text color in HEX format | `String` |
| `lineColor` | :material-check: | Navitia line color in HEX format | `String` |
| `commercialMode` | :material-check: | Navitia public transport commercial mode. Example: `commercial_mode:Bus` | `String` |
| `physicalMode` | :material-check: | Navitia public transport physical mode. Example: `physical_mode:Bus` | `String` |
| `duration` | :material-check: | Section duration in seconds | `Int` |

#### Favorite Poi

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique POI ID | `String` |
| `coords` | :material-check: | POI coordinates | `CLLocationCoordinate2D` |
| `name` | :material-check: | POI name | `String` |
| `address` | :material-check: | POI address | `String` |
| `type` | :material-check: | POI type | `String` |
| `typeId` | :material-check: | Navitia POI type ID. Example: `poi_type:amenity:hospital` | `String` |
| `network` | :material-check: | Navitia POI network | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

#### Favorite Station

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `stopAreaId` | :material-check: | Navitia stop area ID | `String` |
| `coords` | :material-check: | Station coordinates | `CLLocationCoordinate2D` |
| `name` | :material-check: | Station name | `String` |
| `lineId` | :material-check: | Navitia line ID | `String` |
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
