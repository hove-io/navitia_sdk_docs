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
    implementation("com.kisio.navitia.sdk.ui:journey:4.0.0")
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
| `context` | `Context` | ✓ | Context in which the module is launched | ✗ |
| `colors` | `AroundMeColors` | ✓ | Module colors configuration | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `configuration` | `Configuration` | Only if `configurationJsonFile` is not set | Data configuration of the module | `null` |
| `configurationJsonFile` | `String` | Only if `Configuration` is not set | Json file name in `assets` folder | `null` |
| `env` | `AroundMeEnvironment` | ✓ | Navitia API environment | ✗ |
| `onNavigate` | `Unit` | ✗ | Listener for the navigation between module screens | `{ _ -> }` |
| `onBack` | `Unit` | ✗ | Listener for the navigation back button click event | `{ _ -> }` |

</div>

- Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `primaryColor` | ✓ | To set the main color of the screens | ✗ |
| `secondaryColor` | ✗ | To set the color of some UI components | `primaryColor` |
| `originColor` | ✗ | To set the color of the origin pin icon color on the map and the roadmap departure block | `#D24D57` |
| `originBackgroundColor` | ✗ | To set the color of the roadmap departure block. *originColor* value will be ignored | `#D24D57` |
| `originIconColor` | ✗ | To set the color of the origin pin icon color on the map and the roadmap departure block  | `#D24D57` |
| `destinationColor` | ✗ | To set the color of the destination icon on the map and the roadmap arrival block | `#26A65B` |
| `destinationBackgroundColor` | ✗ | To set the color of the roadmap arrival block. *destinationColor* value will be ignored | `#D24D57` |
| `destinationIconColor` | ✗ | To set the color of the destination icon on a arrival search field and on the map. *destinationColor* value will be ignored | `#26A65B` |

</div>

#### Example
{: .no_toc }

```kotlin
JourneyUI.getInstance().let { instance ->
    instance.init(
      context = this,
      colors = JourneyColors(
          primaryColor = "#0277BD",
          secondaryColor = "#FF4081"
      ).originColor(R.color.origin)
        .destinationColor(R.color.origin),
      coverage = "YOUR_COVERAGE",
      token = "YOUR_TOKEN",
      configurationJsonFile = "config.json",
      env = AroundMeEnvironment.PROD
   )
   instance.attachActivity(this)
}
```

### Activity delegation

Since the module launches its fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `JourneysUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.\
You can call this method before or after `init()`.

<div markdown="1">

| Method | Description |
| --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Schedule fragments |

</div>

Then, you can call `JourneysUI.getInstance().getActivityDelegate()` to obtain the delegate.
If you try to access it without attaching an activity before, an exception will be thrown.

```kotlin
JourneysUI.getInstance().attachActivity(AppCompatActivity)
...
JourneysUI.getInstance().delegate.onBackPressed()
```

## 🚀 Launching

This module has two entry points: `JourneysFragment` or `FormFragment`.
You have to instantiate the target fragment with the required parameters.<br>

### Launching fragments
{: .no_toc }

Assuming you have an `Activity` with a fragment container, refer to the following examples to launch a entry screen fragment.

#### Launching with Form
{: .no_toc }

```kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, FormFragment.newInstance(), "TAG")
    addToBackStack("TAG")
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
    replace(R.id.container_id, JourneysFragment.newInstance(journeysRequest), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## 🛠 Configuration

The table below explains the different methods of the builder that you are able to use within the `Journey` Module.

<div markdown="1">

| Method | Description | Default |
| --- | --- | --- |
| `.autoCompleteTitle(String)`<br>`.autoCompleteTitle(StringRes)`  | To set the title of the auto completion screen | Localized resource `R.string.journeys` |
| `.formTitle(String)`<br>`.formTitle(StringRes)` | To set the title of the form screen | Localized resource  `R.string.journeys` |
| `.journeysTitle(String)`<br>`.journeysTitle(StringRes)` | To set the title of the list of journeys screen | Localized resource  `R.string.journeys` |
| `.ridesharingTitle(String)`<br>`.ridesharingTitle(StringRes)` | To set the title of the list of ridesharings screen | Localized resource  `R.string.ridesharing_noun` |
| `.roadmapTitle(String)`<br>`.roadmapTitle(StringRes)` | To set the title of the roadmap screen | Localized resource  `R.string.roadmap` |
| `.disruptionContributor(String)` | To filter disruption based on source contributor | ✗ |
| `.maxHistory(Int)` | To set up the maximum number of items you can find in autocompletion search history | `10` |
| `.withAdvancedSearchMode()` | To enable advanced search mode | `false`. Calling the method put it to `true`. If `FormFragment` is the enrtry point, this is automatically switched to `true` |
| `.withBooking()` | Some UI can have a different behaviour for this using in a Maas project | `false`. Calling the method put it to `true` |
| `.withEarlierLaterFeature()` | To use shortcuts for next and previous journeys | `false`. Calling the method put it to `true` |
| `.withMultiNetwork()` | To set the display of the network name in the roadmap  | `false`. Calling the method put it to `true` |
| `.withNextDepartures()`| To display 3 next departures of the journey | `false`. Calling the method put it to `true` |

</div>

#### Transport Mode

A transport mode is used to filter a journeys query. It is necessary to add a list of transport mode to `JourneysRequest` in order to obtain the desired results.
`TransportModeModel` represents a transport mode. You need to request Navitia first to get your available list of physical modes for your coverage:
`https://api.navitia.io/v1/coverage/<COVERAGE>/physical_modes`

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| titleRes | `@StringRes Int` | ✓ | String resource ID of the mode | `R.string.ic_tramway` |
| iconRes | `@DrawableRes Int` | ✗ | Icon resource ID of the mode | `R.id.ic_tramway` |
| firstSectionModes | `Set<String>` | ✗ | List of modes to use at the begining of the journey | `setOf("walking", "bike", "car", "bss", "ridesharing")` |
| lastSectionModes | `Set<String>` | ✗ | List of modes to use at the end of the journey | `setOf("walking", "bike", "car", "bss", "ridesharing")` |
| directPathMode | `Set<String>` | ✗ | List of modes to use at the end of the journey | `setOf("walking", "bike", "car", "bss", "ridesharing")` |
| physicalModes | `Set<String>` | ✗ | Physical modes of the mode | `setOf("physical_mode:Bike", "physical_mode:Train")` |
| isRealTime | `Boolean` | ✗ | To indicate if real time is enabled | `false` |
| isSelected | `Boolean` | ✗ | To indicate if the transport mode is selected | `true` |

</div>

#### Example
{: .no_toc }
```kotlin
val transportModes = listOf(
    TransportMode(
        titleRes = R.string.mode_bus_metro,
        iconRes = R.drawable.ic_bus_metro,
        firstSectionModes = setOf(SectionMode.WALKING.modeName),
        lastSectionModes = setOf(SectionMode.WALKING.modeName),
        physicalModes = setOf(PhysicalMode.BUS, PhysicalMode.METRO),
        isSelected = true
    ),
    TransportMode(
        titleRes = R.string.mode_bike,
        iconRes = R.drawable.ic_bike,
        firstSectionModes = setOf(SectionMode.BSS.modeName),
        lastSectionModes = setOf(SectionMode.BSS.modeName),
        physicalModes = setOf(PhysicalMode.BIKE, PhysicalMode.BIKE_SHARING_SERVICE),
        isRealTime = true
    )
)
```

### Journeys request

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| `originId` | `String` | ✓ | Origin coordinates, following the format `lon;lat` | `"2.3665844;48.8465337"` |
| `originLabel` | `String` | ✗ | Origin label, if not set the address will be displayed | `"Home"` |
| `originAddress` | `String` | ✗ | Origin address | `"20 Rue Hector Malot, 75012, Paris"` |
| `destinationId` | `String` | ✓ | Destination coordinates, following the format `lon;lat` | `"2.2979169;48.8848719"` |
| `destinationLabel` | `String` | ✗ | Destination label, if not set the address will be displayed | `"Work"` |
| `destinationAddress` | `String` | ✗ | Destination address| `"20 Rue Hector Malot, 75012, Paris"` |
| `datetime` | `DateTime` | ✗ | Requested date and time for journey results | `DateTime.now()` |
| `datetimeRepresents` | `String` | ✗ | Can be `.DEPARTURE` (journeys after datetime) or `.ARRIVAL` (journeys before datetime). | `JourneysRequest.DEPARTURE` |
| `forbiddenUris` | `Set<String>` | ✗ | Used to avoid lines, modes, networks, etc in the Journey search (List of navitia uris) | `setOf("commercial_mode:Bus", "line:1")` |
| `allowedId` | `Set<String>` | ✗ | If you want to use only a small subset of the public transport objects in the Journey search (List of navitia uris) | `listOf("commercial_mode:Bus", "line:1")` |
| `firstSectionModes` | `Set<String>` | ✗ | List of modes to use at the begining of the journey | `setOf("walking", "bike", "car", "bss", "ridesharing")` |
| `lastSectionModes` | `Set<String>` | ✗ | List of modes to use at the end of the journey | `setOf("walking", "bike", "car", "bss", "ridesharing")` |
| `count` | `Int` | ✗ | The number of journeys that will be displayed | `3` |
| `minJourneys` | `Int` | ✗ | The minimum number of journeys that will be displayed | `3` |
| `maxJourneys` | `Int` | ✗ | The maximum number of journeys that will be displayed | `10` |
| `addPoiInfos` | `Set<String>` | ✗ | Allow the display of the availability in real time for bike share and car park | `setOf("bss_stands", "car_park")` |
| `directPathMode` | `Set<String>` | ✗ | Allow full journeys with section modes | `setOf("car", "bike")` |
| `physicalModes` | `Set<String>` | ✗ | Allowed physical modes in the coverage | `setOf("physical_mode:Metro", "physical_mode:Bus")` |
| `dataFreshness` | `String` | ✗ | To indicate if theoretical or realtime data are requested | `"realtime"` |
| `travelerType` | `String` | ✗ | To give extra information about the traveler state| `Constant.TRAVELER_TYPE_STANDARD` |

</div>

### Lines

The `lines` is a JSON array of a line configuration.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `code` | String | ✓ | Line code identifier |
| `icon_res` | String | ✓ | String resource ID of the line icon |
| `mode_id` | String | ✓ | Navitia commercial name of the line |

</div>

### Modes

The `modes` is a JSON array of a transport mode configuration.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `id` | String | ✓ | Navitia commercial name of the transport mode |
| `icon_res` | String | ✓ | String resource ID of the mode icon |

</div>

- Using JSON file

The JSON file should be added to the `assets` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

```json
{
  "lines": [
    {
      "code": "a",
      "icon_res": "ic_metro_a",
      "commercial": "Metro"
    },
    {
      "code": "C1",
      "icon_res": "ic_bus_c1",
      "commercial": "Bus"
    },
    {
      "code": "C2",
      "icon_res": "ic_bus_c2",
      "commercial": "Bus"
    }
  ],
  "modes": [
    {
      "commercial": "Metro",
      "icon_res": "ic_metro"
    },
    {
      "commercial": "Bus",
      "icon_res": "ic_bus"
    },
    {
      "commercial": "Coach",
      "icon_res": "ic_bus"
    }
  ]
}
```

- Using Configuration object

```kotlin
// Configure lines
val linesConfiguration = listOf(
    ConfigurationLine(
        code = "a",
        iconRes = "ic_metro_a",
        modeId = "Metro"
    ),
    ConfigurationLine(
        code = "C2",
        iconRes = "ic_bus_c1",
        modeId = "Bus"
    ),
    ConfigurationLine(
        code = "a",
        iconRes = "ic_bus_c2",
        modeId = "Bus"
    )
)

// Configure modes
val modesConfiguration = listOf(
    ConfigurationMode(
        id = "Metro",
        iconRes = "ic_metro"
    ),
    ConfigurationMode(
        id = "Bus",
        iconRes = "ic_bus"
    ),
    ConfigurationMode(
        id = "Coach",
        iconRes = "ic_bus"
    )
)

val iconsConfiguration = JourneyConfiguration(
    lines = linesCnonfiguration,
    modes = modesConfiguration
)

JourneyUI.getInstance().let { instance ->
    instance.init(
      context = this,
      colors = JourneyColors(
          primaryColor = "#0277BD",
          secondaryColor = "#FF4081"
      ).originColor(R.color.origin)
        .destinationColor(R.color.origin),
      coverage = "YOUR_COVERAGE",
      token = "YOUR_TOKEN",
      configuration = iconsConfiguration,
      env = AroundMeEnvironment.PROD
   )
   instance.attachActivity(this)
}
```
