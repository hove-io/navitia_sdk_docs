---
layout: main
title: Getting started
parent: Journey Android
grand_parent: Journey
nav_order: 2
permalink: /journey/android/getting-started
---

# Getting Started
{: .no_toc }

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 🧰  Requirements

Minimum Android SDK target: `21`

## 💻 Setup

The access to `Journey` module requires valid credentials to our private artifactory. Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials:

```ruby
repositories {
    ...
    maven {
        credentials {
            username = USERNAME
            password = PASSWORD
        }
        url("https://kisiodigital.jfrog.io/kisiodigital/android-release")
    }
}
```
 
Add the following dependency in the `build.gradle` file of your application:
```ruby
dependencies {
    ...
    implementation("com.kisio.navitia.sdk.ui:journey:3.4.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:
```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Journey must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:
```xml
<activity
    ...
    android:configChanges="orientation|screenSize"
    .../>
```
## 👨‍💻 Implementation

### Init

This module is set up by calling `JourneysUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. \
This method takes the following parameters:

<div markdown="1">

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| `context` | `Context` | ✓ | Context of the application | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `environment` | `ExpertEnvironment` | ✗ | Navitia environment| `ExpertEnvironment.PROD` |
| `configuration` | `Configuration` | Only if `configurationJsonFile` is not set | Data configuration of the module | `null` |
| `configurationJsonFile` | `String` | Only if `Configuration` is not set | Json file name in `assets` folder | `null` |
| `onNavigate` | `(Fragment, String) -> Unit` | ✗ | Callback executed when a navigation event happens within the module | `null` |
| `onBack` | `() -> Boolean` | ✗ | Callback executed when an `onBackPressed()` event happens within the module | `null` |

</div>

#### Example
{: .no_toc }

```kotlin
JourneysUI.getInstance()
    .init(
        this,
        "YOUR_TOKEN",
        "YOUR_COVERAGE",
        ExpertEnvironment.PROD,
        Configuration(filtersConfiguration, bookButtonConfiguration), // Not required if configurationJsonFile is set
        "jsonFile", // Not required if configuration object is set
        { fragment, _ ->
            // Navigate from Fragment1 to Fragment2
            // Execute some instructions
        },
        {
            // Navigate from Fragment2 to Fragment1
            // Execute some instructions
            return true
        }
    )
```

### Activity delegation

Since the module launches itself fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `JourneysUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.\
You can call this method before or after `init()`.

<div markdown="1">

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Schedule fragments |

</div>

Then, you can call `JourneysUI.getInstance().getActivityDelegate()` to obtain the delegate.
Therefore, if you try to access it without attaching an activity before, an exception will be thrown.

```kotlin
JourneysUI.getInstance().attachActivity(AppCompatActivity)
...
JourneysUI.getInstance().getActivityDelegate().onBackPressed()
```

## 🚀 Launching

This module has two entry points: `JourneysFragment` or `FormFragment`.
You have to fill in the correct parameters and launch the fragment. Both need `JourneyRequest`.<br>

### Launching fragments
{: .no_toc }

Assuming you have an `Activity` with a fragment container, refer to the following examples to launch a entry screen fragment.

#### Launching with Form
{: .no_toc }

```kotlin
val journeysRequest = JourneysRequest().apply {
    originLabel = "My home"
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    addPoiInfos = listOf("bss_stands", "car_park")
    count = 5
    transportModeListRequested = listOf<TransportModeModel>()
}
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, FormFragment.newInstance(journeysRequest), FormFragment.TAG)
    addToBackStack(FormFragment.TAG)
    commit()
}
```

#### Launching with Journeys
{: .no_toc }

```kotlin
val journeysRequest = JourneysRequest().apply {
    originLabel = "My home"
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    addPoiInfos = listOf("bss_stands", "car_park")
    count = 10
}
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, JourneysFragment.newInstance(journeysRequest), JourneysFragment.TAG)
    addToBackStack(JourneysFragment.TAG)
    commit()
}
```

## 🛠 Configuration

The table below explains the different methods of the builder that you are able to use before init the `Journey` Module.

<div markdown="1">

| Method | Description | Default |
| --- | --- | --- |
| `.autoCompleteTitle(String)`<br>`.autoCompleteTitle(StringRes)`  | To set the title of the auto completion view | Localized resource `R.string.journeys` |
| `.formTitle(String)`<br>`.formTitle(StringRes)` | To set the title of the form view | Localized resource  `R.string.journeys` |
| `.journeysTitle(String)`<br>`.journeysTitle(StringRes)` | To set the title of the list of journeys view | Localized resource  `R.string.journeys` |
| `.ridesharingTitle(String)`<br>`.ridesharingTitle(StringRes)` | To set the title of the list of ridesharings view | Localized resource  `R.string.ridesharing_noun` |
| `.roadmapTitle(String)`<br>`.roadmapTitle(StringRes)` | To set the title of the roadmap view | Localized resource  `R.string.roadmap` |
| `.disruptionContributor(String)` | To filter disruption based on source contributor | ✗ |
| `.maxHistory(Int)` | To set up the maximum number of items you can find in autocompletion search history | `10` |
| `.withAdvancedSearchMode()` | To enable advanced search mode | `false`. Calling the method put it to `true`. If `FormFragment` is the enrtry point, this is automatically switched to `true` |
| `.withBooking()` | Some UI can have a different behaviour for this using in a Maas project | `false`. Calling the method put it to `true` |
| `.withEarlierLaterFeature()` | To use shortcuts for next and previous journeys | `false`. Calling the method put it to `true` |
| `.withMultiNetwork()` | To set the display of the network name in the roadmap  | `false`. Calling the method put it to `true` |
| `.withNextDepartures()`| To display 3 next departures of the journey | `false`. Calling the method put it to `true` |

</div>

- Example

```kotlin
JourneysUI.getInstance()
    .colors(JourneysColors("#0277BD").apply {
        setPrimaryColor("#FF4081")
        setOriginBackgroundColor("#00BB75")
        setDestinationBackgroundColor("#B00353")
    })
    .maxHistory(10)
    .journeysTitle("Itineraries")
    .roadmapTitle(R.string.your_roadmap)
    .withMultiNetwork()
    .withEarlierLaterFeature()
    .init(
        this,
        "YOUR_TOKEN",
        "YOUR_COVERAGE",
        "",
        null,
        "jsonFile",
        null,
        null
    )
```

#### Transport Mode

A transport mode is used to filter a journeys query. It is necessary to add a list of transport mode to `JourneysRequest` in order to obtain the desired results.
`TransportModeModel` represents a transport mode. You need to request Navitia first to get your available list of physical modes for your coverage:
`https://api.navitia.io/v1/coverage/<COVERAGE>/physical_modes`

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| title | `String` | ✓ | Label of the mode | "Tramway" |
| resIconId | `@DrawableRes Int` | ✗ | Icon resource ID of the mode | `R.id.ic_tramway` |
| firstSectionMode | `List<String>` | ✗ | List of modes to use at the begining of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| lastSectionMode | `List<String>` | ✗ | List of modes to use at the end of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| physicalModes | `List<String>` | ✗ | Physical modes of the mode | `listOf("physical_mode:Bike", "physical_mode:Train")` |
| realTime | `Boolean` | ✗ | To indicate if real time is enabled | `false` |
| selected | `Boolean` | ✗ | To indicate if the transport mode is selected | `true` |

</div>

#### Example
{: .no_toc }
```kotlin
val transportModes = listOf<TransportModeModel>(
    TransportModeModel(TransportMode.BUS).apply {
        resIconId = R.id.ic_bus,
        setFirstSectionMode(SECTION_MODE_WALKING)
        setLastSectionMode(SECTION_MODE_WALKING)
        setPhysicalModes("physical_mode:Bus")
        isSelected = true
    },
    TransportModeModel(TransportMode.BIKE).apply {
        resIconId = R.id.ic_bike,
        setFirstSectionMode(SECTION_MODE_BIKE)
        setLastSectionMode(SECTION_MODE_BIKE)
        setPhysicalModes("physical_mode:Bike")
        isSelected = true
    },
    TransportModeModel(TransportMode.CAR).apply {
        resIconId = R.id.ic_car,
        setFirstSectionMode(SECTION_MODE_CAR)
        setLastSectionMode(SECTION_MODE_CAR)
        setPhysicalModes("physical_mode:Car")
        isSelected = true
    }
)
```

### Journeys request

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| `originId` | `String` | ✓ | Origin coordinates, following the format `lon;lat` | `"2.3665844;48.8465337"` |
| `destinationId` | `String` | ✓ | Destination coordinates, following the format `lon;lat` | `"2.2979169;48.8848719"` |
| `originLabel` | `String` | ✗ | Origin label, if not set the address will be displayed | `"Home"` |
| `destinationLabel` | `String` | ✗ | Destination label, if not set the address will be displayed | `"Work"` |
| `datetime` | `DateTime` | ✗ | Requested date and time for journey results | `DateTime.now()` |
| `datetimeRepresents` | `String` | ✗ | Can be `.DEPARTURE` (journeys after datetime) or `.ARRIVAL` (journeys before datetime). | `JourneysRequest.DEPARTURE` |
| `forbiddenUris` | `List<String>` | ✗ | Used to avoid lines, modes, networks, etc in the Journey search (List of navitia uris) | `listOf("commercial_mode:Bus", "line:1")` |
| `allowedId` | `List<String>` | ✗ | If you want to use only a small subset of the public transport objects in the Journey search (List of navitia uris) | `listOf("commercial_mode:Bus", "line:1")` |
| `firstSectionModes` | `List<String>` | ✗ | List of modes to use at the begining of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| `lastSectionModes` | `List<String>` | ✗ | List of modes to use at the end of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| `count` | `Int` | ✗ | The number of journeys that will be displayed | `3` |
| `minNbJourneys` | `Int` | ✗ | The minimum number of journeys that will be displayed | `3` |
| `maxNbJourneys` | `Int` | ✗ | The maximum number of journeys that will be displayed | `10` |
| `addPoiInfos` | `List<String>` | ✗ | Allow the display of the availability in real time for bike share and car park | `listOf("bss_stands", "car_park")` |
| `directPath` | `String` | ✗ | To indicate if the journey is direct | `"only"` |
| `dataFreshness` | `String` | ✗ | To indicate if theoretical or realtime data are requested | `"realtime"` |
| `travelerType` | `String` | ✗ | To give extra information about the traveler state| `Constant.TRAVELER_TYPE_STANDARD` |

</div>

### Colors

<div markdown="1">

In order to configurate colors, you have to create a `JourneyColors` object which takes the following parameters:

| Configuration | Required | Description |
| --- |:---:| --- |
| `JourneyColors(String)` | ✓ | To set the main color |
| `.setPrimaryColor(String)`<br>`.setPrimaryColorRes(ColorRes)` | ✗ | To set the secondary color |

| `.setOriginColor(String)`<br>`.setOriginColorRes(ColorRes)`  | ✗ | To set the color of the origin pin icon color on the map and the roadmap departure block |
| `.setOriginIconColor(String)`<br>`.setOriginIconColorRes(ColorRes)`  | ✗ | To set the color of the origin icon on a departure search field and on the map. *originColor* value will be ignored |
| `.setOriginBackgroundColor(String)`<br>`.setOriginBackgroundColorRes(ColorRes)`  | ✗ | To set the color of the roadmap departure block. *originColor* value will be ignored |

| `.setDestinationColor(String)`<br>`.setDestinationColorRes(ColorRes)` | ✗ | To set the color of the destination icon on the map and the roadmap arrival block |
| `.setDestinationIconColor(String)`<br>`.setDestinationIconColorRes(ColorRes)`  | ✗ | To set the color of the destination icon on a arrival search field and on the map. *destinationColor* value will be ignored |
| `.setDestinationBackgroundColor(String)`<br>`.setDestinationBackgroundColorRes(ColorRes)`  | ✗ | To set the color of the roadmap arrival block. *destinationColor* value will be ignored  |

</div>

### Transport modes & lines

The module offers the possibility to customize icons and names of transport modes and lines.
For your coverage, you may need to request Navitia first to get your available list of lines and commercial modes:<br>
`https://api.navitia.io/v1/coverage/<COVERAGE>/lines`<br>

###### Lines
{: .no_toc }

`lines` is a JSON array of transport lines.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `code` | String | ✓ | [Code of the line](http://doc.navitia.io/#public-transportation-objects-exploration) from Navitia |
| `icon_res` | String | ✓ | Icon resource ID of the line |
| `mode_id` | String | ✓ | Commercial mode id of the corresponding mode described below |

</div>

###### Modes
{: .no_toc }

`modes` is a JSON array of modes.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `id` | String | ✓ | [Commercial mode name](http://doc.navitia.io/#commercial-mode) from Navitia |
| `icon_res` | String | ✓ | Icon resource ID of the mode |

</div>

#### How to configure Data
{: .no_toc }

- Using JSON file

The JSON file should be added to the `assets` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

```json
{
  "lines": [
    {
      "code": "B1",
      "icon_res": "ic_bus_1",
      "mode_id": "Bus"
    },
    {
      "code": "B2",
      "icon_res": "ic_bus_2",
      "mode_id": "Bus"
    },
    {
      "code": "1",
      "icon_res": "ic_metro_1",
      "mode_id": "Metro"
    },
    {
      "code": "2",
      "icon_res": "ic_metro_2",
      "mode_id": "Metro"
    },
    {
      "code": "3",
      "icon_res": "ic_metro_3",
      "mode_id": "Metro"
    }
  ],
  "modes": [
    {
      "id": "Bus",
      "icon_res": "ic_bus"
    },
    {
      "id": "Metro",
      "icon_res": "ic_metro"
    }
  ]
}
```

- Using Configuration object

```kotlin
// Configure lines
val linesConfiguration = listOf(
    ConfigurationLine().apply {
        code = "B1"
        iconRes = "ic_bus_1"
        modeId = "Bus"
    },
    ConfigurationLine().apply {
        code = "B2"
        iconRes = "ic_bus_2"
        modeId = "Bus"
    },
    ConfigurationLine().apply {
        code = "1"
        iconRes = "ic_metro_1"
        modeId = "Metro"
    },
    ConfigurationLine().apply {
        code = "2"
        iconRes = "ic_metro_2"
        modeId = "Metro"
    },
    ConfigurationLine().apply {
        code = "3"
        iconRes = "ic_metro_3"
        modeId = "Metro"
    }
)

// Configure modes
val modesConfiguration = listOf(
    ConfigurationMode().apply {
        id = "Bus"
        iconRes = "ic_bus"
    },
    ConfigurationMode().apply {
        id = "Metro"
        iconRes = "ic_metro"
    }
)

// Setup configuration object
val configuration = ConfigurationRoot(linesConfiguration, modesConfiguration)
```

### Icons
{: .no_toc }

Customizing other icons resources is also made possible. To use this feature, you should rename your image resource to match the resource name found below.

##### Realtime
{: .no_toc }

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Parking availability | `ic_section_mode_parking_relay` |

</div>

##### And more...
{: .no_toc }

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Departure | `ic_departure` |
| Arrival | `ic_arrival` |
| My position | `ic_my_position` |
| Address | `ic_address` |
| POI | `ic_poi` |
| Station | `ic_station` |
| Ridesharing pin | `ic_ridesharing_pin` |

</div>
