---
title: Bookmark Android - Navitia SDK Docs
---

# Bookmark Android

## :computer: Setup

Add the following dependencies in the `build.gradle` file of your application:

```kotlin
dependencies {
    implementation("com.kisio.navitia.sdk.ui:bookmark:1.8.0")
}
```

The activity launching Bookmark must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

``` xml
<activity
    android:configChanges="orientation|screenSize"/>
```

## :man_technologist: Implementation

!!! warning "Warning"

    Make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding

This module is set up by calling `BookmarkUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `context` | :material-check: | Context in which the module is launched | `Context` | :material-close: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" style="text-decoration: underline">Get your token</a> | `String` | :material-close: |
| `configuration` | :material-close: | Module configuration object | [`AroundMeConfiguration`](../../getting_started/#modules-configuration) | `null` |
| `configurationJsonFile` | :material-close: | Module configuration JSON file name | `String` | `null` |

<h4>Example</h4>

=== "Configuration with file"

    ``` kotlin
    BookmarkUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configurationJsonFile = "config.json"
        )
    }
    ```

=== "Manual configuration"

    ``` kotlin
    BookmarkUI.getInstance().let { instance ->
        instance.init(
            context = this,
            token = "your_token",
            configuration = BookmarkConfiguration(
                coverage = "your_coverage",
                timezone = "Europe/Paris",
                env = BookmarkEnvironment.PROD,
                colors = BookmarkColors(
                    primary = "#88819f"
                )
            )
        )
    }
    ```

### Navigation listener

Since the module launches its own fragments, you may want your application to be aware of navigation events.
For that, you have to set a navigation listener by calling this method before `init()`.

``` kotlin
BookmarkUI.getInstance()
    .setNavigationListener(bookmarkNavigationListenerImpl) // (1)
```

1.  `bookmarkNavigationListenerImpl` should be the class instance implementing `BookmarkNavigationListener` interface.

This interface gives you the method `onBack()` for any back event between two fragments and the method `onNavigate` for the reverse.
Each method has a `BookmarkNavigationListener.Event` parameter you can rely on.

``` kotlin
// Navigation events
ADD_ADDRESS_BACK_TO_FAVORITES
EXTERNAL_TO_ADD_ADDRESSES
EXTERNAL_TO_FAVORITES
FAVORITES_BACK_TO_EXTERNAL
FAVORITES_TO_JOURNEY
FAVORITES_TO_ADD_ADDRESS
FAVORITES_TO_ROADMAP
```

### Events tracking

In order to receive the list of generated events within Bookmark module, you have to attach the tracker to the module instance.<br>
You can call this method before or after `init()`.

``` kotlin
BookmarkUI.getInstance()
    .attachTracker(bookmarkTrackerImpl) // (1)
```

1.  `bookmarkTrackerImpl` should be the class instance implementing `BookmarkTracker` interface.

## :rocket: Launching

Bookmark has a single entry point `FavoriteFragment`.<br>
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

``` kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, FavoriteFragment.newInstance(), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## :book: Manipulating data

The module provides the ability to directly manipulate data for use in custom screens.

### Methods

The various CRUD methods are accessed through `BookmarkUI.getInstance().data`.

<h4>Create</h4>

:material-arrow-right: Create a new favorite address

```kotlin
fun saveAddress(address: SharedData.AddressBookmark)
```

| Param | Type | Description |
| --- | --- | --- |
| `address` | [`SharedData.AddressBookmark`](#addressbookmark) | Favorite address to create |

:material-arrow-right: Create a new favorite journey

```kotlin
fun saveJourney(journey: SharedData.JourneyBookmark)
```

| Param | Type | Description |
| --- | --- | --- |
| `journey` | [`SharedData.JourneyBookmark`](#journeybookmark) | Favorite journey to create |

:material-arrow-right: Create a new favorite POI

```kotlin
fun savePoi(poi: SharedData.PoiBookmark)
```

| Param | Type | Description |
| --- | --- | --- |
| `poi` | [`SharedData.PoiBookmark`](#poibookmark) | Favorite POI to create |

:material-arrow-right: Create a new favorite station

```kotlin
fun saveStation(station: SharedData.StationBookmark)
```

| Param | Type | Description |
| --- | --- | --- |
| `station` | [`SharedData.StationBookmark`](#stationbookmark) | Favorite station to create |

<h4>Read</h4>

:material-arrow-right: Fetch a favorite address data. Returns [`SharedData.AddressBookmark`](#addressbookmark) or `null` if not found.

```kotlin
fun fetchAddress(id: String): SharedData.AddressBookmark?
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite address to fetch |

:material-arrow-right: Fetch all favorite addresses. Returns a list of [`SharedData.AddressBookmark`](#addressbookmark) or an empty list if there is no data.

```kotlin
fun fetchAddresses(): List<SharedData.AddressBookmark>
```

:material-arrow-right: Fetch a favorite journey data. Returns [`SharedData.JourneyBookmark`](#journeybookmark) or `null` if not found.

```kotlin
fun fetchJourney(travelId: String): SharedData.JourneyBookmark?
```

| Param | Type | Description |
| --- | --- | --- |
| `travelId` | `String` | Travel id of the favorite journey to fetch |

:material-arrow-right: Fetch all favorite journeys. Returns a list of [`SharedData.JourneyBookmark`](#journeybookmark) or an empty list if there is no data.

```kotlin
fun fetchJourneys(): List<SharedData.JourneyBookmark>
```

:material-arrow-right: Fetch a favorite POI data. Returns [`SharedData.PoiBookmark`](#poibookmark) or `null` if not found.

```kotlin
fun fetchPoi(id: String): SharedData.PoiBookmark?
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite POI to fetch |

:material-arrow-right: Fetch all favorite POIs. Returns a list of [`SharedData.PoiBookmark`](#poibookmark) or an empty list if there is no data.

```kotlin
fun fetchPois(): List<SharedData.PoiBookmark>
```

:material-arrow-right: Fetch a favorite station data. Returns [`SharedData.StationBookmark`](#stationbookmark) or `null` if not found.

```kotlin
fun fetchStation(stopAreaId: String, lineId: String): SharedData.StationBookmark?
```

| Param | Type | Description |
| --- | --- | --- |
| `stopAreaId` | `String` | Navitia stop area id of the favorite station to fetch |
| `lineId` | `String` | Navitia line id of the favorite station to fetch |

:material-arrow-right: Fetch all favorite stations. Returns a list of [`SharedData.StationBookmark`](#stationbookmark) or an empty list if there is no data.

```kotlin
fun fetchStations(): List<SharedData.StationBookmark>
```

<h4>Update</h4>

:material-arrow-right: Update an existing favorite address

```kotlin
fun updateAddress(address: SharedData.AddressBookmark)
```

| Param | Type | Description |
| --- | --- | --- |
| `address` | `SharedData.AddressBookmark` | Favorite address to update |

:material-arrow-right: Update an existing favorite journey

```kotlin
fun updateJourney(travelId: String, additionalInformation: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `travelId` | `String` | Travel id of the favorite journey to update |
| `additionalInformation` | `String` | Extra data to update |

:material-arrow-right: Update an existing favorite POI

```kotlin
fun updatePoi(id: String, additionalInformation: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite POI to update |
| `additionalInformation` | `String` | Extra data to update |

:material-arrow-right: Update an existing favorite station

```kotlin
fun updateStation(id: String, additionalInformation: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `is` | `String` | Id of the favorite station to update |
| `additionalInformation` | `String` | Extra data to update |

<h4>Delete</h4>

:material-arrow-right: Delete an existing favorite address

```kotlin
fun deleteAddress(id: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite address to delete |

:material-arrow-right: Delete an existing favorite journey

```kotlin
fun deleteJourney(travelId: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `travelId` | `String` | Travel id of the favorite journey to delete |

:material-arrow-right: Delete an existing favorite POI

```kotlin
fun deletePoi(id: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Id of the favorite POI to delete |

:material-arrow-right: Delete an existing favorite station

```kotlin
fun deleteStation(stopAreaId: String, lineId: String)
```

| Param | Type | Description |
| --- | --- | --- |
| `stopAreaId` | `String` | Navitia stop area id of the favorite station to delete |
| `lineId` | `String` | Navitia line id of the favorite station to delete |

### Data

<h4 markdown>:fontawesome-solid-file-code: `AddressBookmark`</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique address id | `String` |
| `name` | :material-check: | Address name | `String` |
| `houseNumber` | :material-check: | House number | `Int` |
| `roadName` | :material-check: | Address label | `String` |
| `postalCode` | :material-check: | Address postal code | `String` |
| `city` | :material-check: | Address city | `String` |
| `type` | :material-check: | Address type `home`, `work` or `custom` | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4 markdown>:fontawesome-solid-file-code: `JourneyBookmark`</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `travelId` | :material-check: | Unique journey id | `String` |
| `from` | :material-check: | Departure name | `String` |
| `fromId` | :material-check: | Departure Navitia id | `String` |
| `to` | :material-check: | Arrival name | `String` |
| `toId` | :material-check: | Arrival Navitia id | `String` |
| `sections` | :material-check: | Array of included journey sections | [`List<SharedData.SectionBookmark>`](#sectionbookmark) |
| `isBikeSpecific` | :material-check: | Array of connection modes. For example: `["bike", "walking"]` | `Boolean` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4 markdown>:fontawesome-solid-file-code: `LineBookmark`</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Navitia line id | `String` |
| `code` | :material-check: | Navitia line code | `String` |
| `textColor` | :material-check: | Navitia line text color in hex format | `String` |
| `color` | :material-check: | Navitia line color in hex format | `String` |
| `commercialModeId` | :material-check: | Navitia public transport commercial mode. Example: `commercial_mode:Bus` | `String` |
| `commercialModeName` | :material-check: | Navitia public transport commercial name. Example: `Bus` | `String` |
| `physicalMode` | :material-check: | Navitia public transport physical mode id. Example: `physical_mode:Bus` | `String` |
| `networkId` | :material-check: | Navitia public transport network id. Example: `network:xxx:Operator_21` | `String` |
| `networkName` | :material-check: | Navitia public transport network name. Example: `Operator 21` | `String` |

<h4 markdown>:fontawesome-solid-file-code: `SectionBookmark`</h4>

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

<h4 markdown>:fontawesome-solid-file-code: `PoiBookmark`</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `id` | :material-check: | Unique POI id | `String` |
| `coords` | :material-check: | POI coordinates | `LatLng` |
| `name` | :material-check: | POI name | `String` |
| `address` | :material-check: | POI address | [`AddressBookmark`](#addressbookmark) |
| `type` | :material-check: | POI type | `String` |
| `typeId` | :material-check: | Navitia POI type id. Example: `poi_type:amenity:hospital` | `String` |
| `providerId` | :material-check: | Navitia POI provider id | `String` |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

<h4 markdown>:fontawesome-solid-file-code: `StationBookmark`</h4>

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `stopAreaId` | :material-check: | Navitia stop area id | `String` |
| `coords` | :material-check: | Station coordinates | `LatLng` |
| `name` | :material-check: | Station name | `String` |
| `lines` | :material-check: | Station lines | [`List<SharedData.LineBookmark>`](#linebookmark) |
| `additionalInformation` | :material-check: | Free field to save extra data | `String` |

## :mega: Communicating with other modules or the app

Bookmark module can exchange data with or navigate to either other modules or the host application.<br>
To do this, the host application must initialize `Router`. This singleton will ensure communication between the different modules or the app. Communication will not occur unless those are registered beforehand:

``` kotlin
Router.getInstance()
    ... // Register modules and/or app
    .init()
```

### Application

Some route or callbacks are delegated to the application.
If you have to receive some module data, the `Router` module must register a receiver with the right parameter:

``` kotlin
Router.getInstance()
    .register(appData = appRouterDataImpl) // (1)
```

1.  `appRouterDataImpl` should be the class instance implementing `AppRouter.Data` interface. We recommend using an `Application` subclass.

If you have to handle navigation between modules, the `Router` module must also register a receiver:

``` kotlin
Router.getInstance()
    .register(appUi = appRouterUiImpl) // (1)
```

1.  `appRouterUiImpl` should be the class instance implementing `AppRouter.UI` interface. We recommend using a `Application` subclass.

#### Data interface methods

```kotlin
override fun onUpdateFavoriteStations(id: String) {
    // handle the favorite station update booking
}
```

| Param | Type | Description |
| --- | --- | --- |
| `id` | `String` | Updated favorite station id |

### Modules

#### Journey

:octicons-arrow-right-24: Enabling<br>

This module communicates with [Journey](../../journey/android) module in order to get directions for a chosen itinerary. You should enable the `go_from_go_to` parameter in the [features configuration](../../getting_started/#bookmark-features).<br>

:octicons-arrow-right-24: Method<br>

The following method from the `AppRouter.UI` interface should be implemented by the host application to enable navigation to the Journey module or any other custom screens. Note that the parameters of these methods can be ignored as needed.

```kotlin
override fun openJourneysViaHost(
    origin: SharedData.JourneyPoint?,
    destination: SharedData.JourneyPoint?,
    showDirectlyAutoCompletion: Boolean,
    showDirectlyJourneysSearch: Boolean
) {
    // launch the journey module screen or your custom screen
}
```

| Param | Type | Description |
| --- | --- | --- |
| `origin` | `SharedData.JourneyPoint?` | Desired starting point of the journey. Optional |
| `destination` | `SharedData.JourneyPoint?` | Desired endpoint of the journey. Optional |
| `showDirectlyAutoCompletion` | `Boolean` | Directly displays the search for the starting point and/or endpoint. If true, `showDirectlyJourneysSearch` can only be false |
| `showDirectlyJourneysSearch` | `Boolean` | Directly displays the journey search. If true, `showDirectlyAutoCompletion` can only be false |

## :art: Theming

The module uses graphical components from Material Design 3. To ensure these components function correctly and get displayed properly on the screen, it is crucial to apply the appropriate parent theme:

```xml
<style name="Theme.App" parent="Theme.Material3.*"> <!-- (1) -->
    ...
</style>
```

1.  Replace by the specific theme. For example: `Theme.Material3.Light.NoActionBar`
