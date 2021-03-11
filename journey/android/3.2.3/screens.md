---
layout: main
title: Screens
parent: Journey Android
grand_parent: Journey
nav_order: 2
permalink: /journey/android/screens
---

# Screens
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }

1. TOC
{:toc}
</details>
---

## Launching
Journey has 2 screens acting as entry points: `FormFragment` and `JourneysFragment`.
You have to fill in the correct parameters and launch the fragment. Both need `JourneyRequest`.<br>
See [Transport Mode](/navitia_sdk_docs/journey/android/screen#transport-mode) to know how to set `JourneyRequest.transportModeListRequested`

### With Form
{: .no_toc }

#### Example
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest("fr-idf").apply {
    originLabel = "My home"
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    addPoiInfos = listOf("bss_stands", "car_park")
    count = 5
    transportModeListRequested = listOf<TransportModeModel>()
}
val title = "Example title"
val showBack = true
val formFragment = FormFragment.newInstance(journeysRequest)
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, formFragment, FormFragment.TAG)
    addToBackStack(FormFragment.TAG)
    commit()
}
```

### With Journeys
{: .no_toc }


#### Example
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest("fr-idf").apply {
    originLabel = "My home"
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    addPoiInfos = listOf("bss_stands", "car_park")
    count = 10
}
val journeysFragment = JourneysFragment.newInstance(journeysRequest)
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, journeysFragment, JourneysFragment.TAG)
    addToBackStack(JourneysFragment.TAG)
    commit()
}
```

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
| title | `String` | ✓ | The transport mode label | "Tramway" |
| textIcon | `String` | ✓ | The transport mode Icon | "\uEA1B" |
| firstSectionMode | `List<String>` | ✗ | List of modes to use at the begining of the journey | { "walking", "bike", "car", "bss", "ridesharing" } |
| lastSectionMode | `List<String>` | ✗ | List of modes to use at the end of the journey | { "walking", "bike", "car", "bss", "ridesharing" } |
| physicalModes | `List<String>` | ✗ | Used setup lines, modes, networks, etc in the Journey search (List of navitia uris) | { "physical_mode:Bike", "physical_mode:Train" } |
| realTime | `Boolean` | ✗ | To indicate if real time is enabled | false |
| selected | `Boolean` | ✗ | To indicate if the transport mode is selected | true |

</div>

#### Example
{: .no_toc }
```kotlin
val transportModes = listOf<TransportModeModel>(
    TransportModeModel(TransportMode.BUS).apply {
        setFirstSectionMode(SECTION_MODE_WALKING)
        setLastSectionMode(SECTION_MODE_WALKING)
        setPhysicalModes("physical_mode:Bus")
        isSelected = true
    },
    TransportModeModel(TransportMode.BIKE).apply {
        setFirstSectionMode(SECTION_MODE_BIKE)
        setLastSectionMode(SECTION_MODE_BIKE)
        setPhysicalModes("physical_mode:Bike")
        isSelected = true
    },
    TransportModeModel(TransportMode.CAR).apply {
        setFirstSectionMode(SECTION_MODE_CAR)
        setLastSectionMode(SECTION_MODE_CAR)
        setPhysicalModes("physical_mode:Car")
        isSelected = true
    }
)
```

### Some use cases
{: .no_toc }

##### Bike
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest("fr-idf").apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("bike")
    lastSectionModes = listOf("bike")
}               
```

##### BSS
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest("fr-idf").apply {
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
val journeysRequest = JourneysRequest("fr-idf").apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("car")
    lastSectionModes = listOf("car_park")
}       
```

##### Ridesharing
{: .no_toc }
```kotlin
val journeysRequest = JourneysRequest("fr-idf").apply {
    originId = "2.3665844;48.8465337"
    destinationId = "2.2979169;48.8848719"
    firstSectionModes = listOf("ridesharing")
    lastSectionModes = listOf("ridesharing")
}
```

## Override icons
To customize arrival, departure and transport mode icon, you need to add your vector asset in the `drawable` folder of your application.
Rename your customized transport mode icon with the same resource name as the default icon.

### Departure icon
{: .no_toc }
To customize the `departure` icon, rename your resource as `ic_departure.xml`

### Arrival icon
{: .no_toc }
To customize the `arrival` icon, rename your resource as `ic_arrival.xml`

### Transport mode icons
{: .no_toc }
You can customize icons of transport modes by overriding drawable resources or by set those up programmatically

##### Drawables resources
{: .no_toc }
Rename your customized transport mode icon with the same resource name as the default icon.
For example, if you want to customize the `bus` icon, rename your resource as `ic_transport_mode_bus.xml`
Here is the list of default icon name:
* `ic_transport_mode_air.xml`
* `ic_transport_mode_bike.xml`
* `ic_transport_mode_bss.xml`
* `ic_transport_mode_bus.xml`
* `ic_transport_mode_car.xml`
* `ic_transport_mode_coach.xml`
* `ic_transport_mode_ferry.xml`
* `ic_transport_mode_funicular.xml`
* `ic_transport_mode_metro.xml`
* `ic_transport_mode_ridesharing.xml`
* `ic_transport_mode_shuttle.xml`
* `ic_transport_mode_taxi.xml`
* `ic_transport_mode_train.xml`
* `ic_transport_mode_tramway.xml`
* `ic_transport_mode_walking.xml`

##### Setup programmatically
{: .no_toc }
```kotlin
val transportMode = TransportModeModel(TransportMode.BIKE).apply {
    ...
    resIconId = R.drawable.icon_id
}
```

### Strings resources
{: .no_toc }
<div markdown="1">

| Id | English | French |
| --- | --- | --- |
| `R.string.journeys` | Journeys | Itinéraires | 
| `R.string.ridesharing_noun` | Ridesharing | Covoiturage | 
| `R.string.roadmap` | Roadmap | Feuille de route | 

</div>
