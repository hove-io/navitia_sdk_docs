---
layout: main
title: Getting started
parent: Journey Android
grand_parent: Journey
nav_order: 2
permalink: /journey/android/getting-started
---

# Getting Started

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 💻 Setup

Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials:

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
    implementation("com.kisio.navitia.sdk.ui:journey:3.3.1")
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

- Init

This module is set up by calling `JourneysUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. You need to call the `init()` method at the end.\
The following are methods of the builder:

<div markdown="1">

| Method | Description | Example |
| --- | --- | --- |
| `.autoCompleteTitle(String)`<br>`.autoCompleteTitle(StringRes)`  | To set the title of the auto completion view | by default the localized ressource `R.string.journeys` |
| `.formTitle(String)`<br>`.formTitle(StringRes)` | To set the title of the form view | by default the localized ressource `R.string.journeys` |
| `.journeysTitle(String)`<br>`.journeysTitle(StringRes)` | To set the title of the list of journeys view | by default the localized ressource `R.string.journeys` |
| `.ridesharingTitle(String)`<br>`.ridesharingTitle(StringRes)` | To set the title of the list of ridesharings view | by default the localized ressource `R.string.ridesharing_noun` |
| `.roadmapTitle(String)`<br>`.roadmapTitle(StringRes)` | To set the title of the roadmap view | by default the localized ressource `R.string.roadmap` |
| `.maxHistory(Int)` | To set up the maximum number of items you can find in autocompletion search history | by default `10` |
| `.withBooking()` | Some UI can have a different behaviour for this using in a Maas project | by default `false`. Calling the method put it to `true` |
| `.withEarlierLaterFeature()` | ??? | by default `false`. Calling the method put it to `true` |
| `.withMultiNetwork()` | To set the display of the network name in the roadmap  | by default `false`. Calling the method put it to `true` |
| `.withNextDepartures()`| ??? | by default `false`. Calling the method put it to `true` |

</div>

And there are arguments of the `init()` method:

<div markdown="1">

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| `context` | `Context` | ✓ | Context of the application | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `navigationListener` | `NavigationListener` | ✗ | Listener the module can rely on for navigation events within the app | `null` |

</div>

#### Example
{: .no_toc }

```kotlin
JourneysUI.getInstance()
    .colors(JourneysColors("#0277BD").apply {
        setPrimaryColor("#FF4081")
        setOriginBackgroundColor("#00BB75")
        setDestinationBackgroundColor("#B00353")
    })
    .maxHistory(10)
    .withMultiNetwork()
    .init(
        this,
        "YOUR_TOKEN",
        "YOUR_COVERAGE",
        null
    )
```

- Activity delegation

Since the module launches itself fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `JourneysUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.\
You can call this method before or after `init()`.

<div markdown="1">

| Method | Description | Example |
| --- | --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Schedule fragments |

</div>

Then, you can call `JourneysUI.getInstance().getActivityDelegate()` to obtain the delegate.
Therefore, if you try to access it without attaching an activity before, an exception will be thrown.

```kotlin
JourneysUI.getInstance().attachActivity(AppCompatActivity)
...
JourneysUI.getInstance().getActivityDelegate().onBackPressed()
```

## 🛠 Configuration

<div markdown="1">

| Configuration | Required | Description |
| --- |:---:| --- |
| `JourneyColors(String)` | ✓ | To set the main color |
| `.setPrimaryColor(String)`<br>`.setPrimaryColorRes(ColorRes)` | ✗ | To set the secondary color |
| `.setOriginColor(String)`<br>`.setOriginColorRes(ColorRes)`  | ✗ | To set the color of the origin icon on the map and the roadmap departure block |
| `.setOriginBackgroundColor(String)`<br>`.setOriginBackgroundColorRes(ColorRes)`  | ✗ | To set the color of the roadmap departure block |
| `.setOriginIconColor(String)`<br>`.setOriginIconColorRes(ColorRes)`  | ✗ | To set the color of the origin icon on a departure search field and on the map  |
| `.setDestinationColor(String)`<br>`.setDestinationColorRes(ColorRes)` | ✗ | To set the color of the destination icon on the map and the roadmap arrival block |
| `.setDestinationBackgroundColor(String)`<br>`.setDestinationBackgroundColorRes(ColorRes)`  | ✗ | To set the color of the roadmap arrival block  |
| `.setDestinationIconColor(String)`<br>`.setDestinationIconColorRes(ColorRes)`  | ✗ | To set the color of the destination icon on a arrival search field and on the map |

</div>

## 🚀 Launching

Journey has two entry points: `JourneysFragment` or `FormFragment`. Please make sure to `init` the module before launching one of those fragments.<br>
You have to fill in the correct parameters and launch the fragment. Both need `JourneyRequest`.<br>

### Journeys request
{: .no_toc }

`JourneysRequest` has a multitude of parameters allowing to build a consumable request by Journey.

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

</div>

### Transport Mode
{: .no_toc }

A transport mode is used to filter a journeys query. It is necessary to add a list of transport mode to `JourneysRequest` in order to obtain the desired results.
`TransportModeModel` represents a transport mode. You need to request Navitia first to get your available list of transport modes for your coverage:
`https://api.navitia.io/v1/coverage/<COVERAGE>/physical_modes`

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| title | `String` | ✓ | Label of the mode | "Tramway" |
| resIconId | `@DrawableRes Int` | ✗ | Icon resource ID of the mode | `R.id.ic_tramway` |
| firstSectionMode | `List<String>` | ✗ | List of modes to use at the begining of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| lastSectionMode | `List<String>` | ✗ | List of modes to use at the end of the journey | `listOf("walking", "bike", "car", "bss", "ridesharing")` |
| physicalModes | `List<String>` | ✗ | [Physical modes](http://doc.navitia.io/#public-transport-objects) of the mode | `listOf("physical_mode:Bike", "physical_mode:Train")` |
| realTime | `Boolean` | ✗ | To indicate if real time is enabled | `false` |
| selected | `Boolean` | ✗ | To indicate if the transport mode is selected | `true` |

</div>

- Some use cases
{: .no_toc }

##### Bike
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest().apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("bike")
    lastSectionModes = listOf("bike")
}               
```

##### BSS
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest().apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("bss")
    lastSectionModes = listOf("bss")
    addPoiInfos = listOf("bss_stands")
}              
```

##### Car
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest().apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("car")
    lastSectionModes = listOf("car_park")
}       
```

##### Ridesharing
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest().apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("ridesharing")
    lastSectionModes = listOf("ridesharing")
}
```

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

### Launching fragments
{: .no_toc }

Assuming you have an `Activity` with a fragment container, please refer to the following examples to launch a entry screen fragment.

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
