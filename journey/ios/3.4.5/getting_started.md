---
layout: main
title: Getting started
parent: Journey iOS
grand_parent: Journey
nav_order: 1
permalink: /journey/ios/getting-started
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

- [Cocoapods](https://cocoapods.org): this module is available through Cocoapods.
- Minimum iOS deployment target: 10.0

## 💻  Setup

The access to `Journey` module and its dependencies require valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'NavitiaSDKUI', '~> 3.4.5' # Journey Pod definition
end
```

## 👨‍💻 Implementation

This module needs to be initialized before launching the main `ViewController`. Therefore, You need to call the `JourneySdk.shared.initialize()` method.\
The `initialize` method takes the following parameters:

<div markdown="1">

| Configuration | Required | Type | Description | Example |
| --- |:---:| --- | --- | --- |
| `token` | ✓ | `String` | Your Navitia token | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `coverage` | ✓ | `String` | Your Navitia coverage | `fr-idf` |
| `colorConfiguration` | ✓ | `JourneyColorConfiguration` | To set colors of Journey | `JourneyColorConfiguration(background: .blue, origin: .red, destination: .green)` |

</div>

- Example

```swift     
do {
    let colorConfiguration = JourneyColorConfiguration(background: UIColor(red: 64.0/255, green: 149.0/255, blue: 142.0/255, alpha: 1),
                                                       origin: UIColor(red: 0, green: 187.0/255, blue: 117.0/255, alpha: 1),
                                                       originIcon: UIColor(red: 0, green: 187.0/255, blue: 117.0/255, alpha: 1),
                                                       destination: UIColor(red: 176.0/255, green: 3.0/255, blue: 83.0/255, alpha: 1),
                                                       destinationIcon: UIColor(red: 176.0/255, green: 3.0/255, blue: 83.0/255, alpha: 1))
    
    try JourneySdk.shared.initialize(token: navitia_token, coverage: navitia_coverage, colorConfiguration: colorConfiguration)
} catch {
    if let error = error as? MissingColorConfigurationError {
        Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
    }
}
```

## 🚀 Launching

The Journey module has two entry points: Journeys screen and Form screen.

- Example with journeys screen

```swift
let journeysRequest = JourneysRequest()
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.originLabel = "Home"
journeysRequest.destinationId = "2.2979169;48.8848719"
journeysRequest.destinationLabel = "Work"
journeysRequest.datetime = Date()
journeysRequest.datetime!.addTimeInterval(7200)
journeysRequest.datetimeRepresents = .departure
journeysRequest.forbiddenUris = ["physical_mode:Bus"]
journeysRequest.firstSectionModes = [.walking, .car, .bike, .bss, .ridesharing]
journeysRequest.lastSectionModes = [.walking, .car, .bike, .bss, .ridesharing]

JourneySdk.shared.formJourney = false
guard var journeyResultsViewController = JourneySdk.shared.rootViewController else {
    return nil
}

journeyResultsViewController.journeysRequest = journeysRequest
if let listJourneysViewController = journeyResultsViewController as? UIViewController {
    navigationController?.pushViewController(listJourneysViewController, animated: true)
}
```

- Example with form screen

```swift
let metroButton = ModeButtonModel(title: "Metro",
                                  type: "metro",
                                  selected: true,
                                  firstSectionMode: ["walking"],
                                  lastSectionMode: ["walking"],
                                  physicalMode: ["physical_mode:Metro"])
let busButton = ModeButtonModel(title: "Bus",
                                type: "bus",
                                selected: true,
                                firstSectionMode: ["walking"],
                                lastSectionMode: ["walking"],
                                physicalMode: ["physical_mode:Bus"])
let tramButton = ModeButtonModel(title: "Tramway",
                                 type: "tramway",
                                 selected: false,
                                 firstSectionMode: ["walking"],
                                 lastSectionMode: ["walking"],
                                 physicalMode: ["physical_mode:Tramway"])
let trainButton = ModeButtonModel(title: "Train",
                                  type: "train",
                                  selected: false,
                                  firstSectionMode: ["walking"],
                                  lastSectionMode: ["walking"],
                                  physicalMode: ["physical_mode:LocalTrain", "physical_mode:Train"])
let bikeButton = ModeButtonModel(title: "Bike",
                                 type: "bike",
                                 selected: false,
                                 firstSectionMode: ["bike"],
                                 lastSectionMode: ["bike"],
                                 physicalMode: ["physical_mode:Bike"])
let carButton = ModeButtonModel(title: "Car",
                                type: "car",
                                selected: false,
                                firstSectionMode: ["car"],
                                lastSectionMode: ["car"],
                                physicalMode: ["physical_mode:Car"],
                                realTime: true)
JourneySdk.shared.modeForm = [metroButton, busButton, tramButton, trainButton, bikeButton, carButton]
journeyResultsViewController.journeysRequest = JourneysRequest()
JourneySdk.shared.formJourney = true

guard var journeyResultsViewController = JourneySdk.shared.rootViewController else {
    return nil
}

if let listJourneysViewController = journeyResultsViewController as? UIViewController {
    navigationController?.pushViewController(listJourneysViewController, animated: true)
}
```

## 🛠 Configuration

The table below explains the different parameters that you are able to set before launching the `Journey` Module.

| Parameters | Type | Description | Default |
| --- | --- |:----| --- |
| `formJourney` | `Bool` | To display the journey form screen | `false` |
| `advancedSearchMode` | `Bool` | To enable advanced search mode | `false` (If `formJourney` is set to true, this is automatically switched to true) |
| `maxHistory` | `Int` | To set the maximum number of history inputs for autocompletion | 10 |
| `multiNetwork` | `Bool` | To enable the display of the network name in the roadmap | `false` |
| `isEarlierLaterFeatureEnabled` | `Bool` | To use shortcuts for next and previous journeys | `false` |
| `modeForm` | `[ModeButtonModel]` | To set the shown physical modes, regroup them, set their default selection state | Coverage default value |
| `titlesConfig` | `TitlesConfig?` | To set view controllers titles in navigation view controller | ✗ |
| `disruptionContributor` | `String` | To filter disruption based on source contributor | ✗ |

- Example:

```swift
JourneySdk.shared.formJourney = false
JourneySdk.shared.advancedSearchMode = false
JourneySdk.shared.maxHistory = 12
JourneySdk.shared.multiNetwork = true
JourneySdk.shared.isEarlierLaterFeatureEnabled = true
JourneySdk.shared.modeForm = [ModeButtonModel(title: "Metro",
                                              type: "metro",
                                              selected: true,
                                              firstSectionMode: ["walking"],
                                              lastSectionMode: ["walking"],
                                              physicalMode: ["physical_mode:Metro"]),
                              ModeButtonModel(title: "Bus",
                                              type: "bus",
                                              selected: true,
                                              firstSectionMode: ["walking"],
                                              lastSectionMode: ["walking"],
                                              physicalMode: ["physical_mode:Bus"])]
JourneySdk.shared.titlesConfig = TitlesConfig(formTitle: "Form",
                                              journeysTitle: "Journeys",
                                              roadmapTitle: "Roadmap",
                                              ridesharingOffersTitle: "Ridesharing offers",
                                              autocompleteTitle: "Autocomplete")]
JourneySdk.shared.disruptionContributor = "shortterm.tr_idfm"
```

### Journeys request

<div markdown="1">

| Parameters | Type | Required | Description | Example |
| --- | --- | :---: | --- | --- |
| `originId` | `String` | ✓ | Origin coordinates, following the format `lon;lat` | "2.3665844;48.8465337" |
| `destinationId` | `String` | ✓ | Destination coordinates, following the format `lon;lat` | "2.2979169;48.8848719" |
| `originLabel` | `String` | ✗ | Origin label, if not set the address will be displayed | "Home" |
| `destinationLabel` | `String` | ✗ | Destination label, if not set the address will be displayed | "Work" |
| `datetime` | `Date` | ✗ | Requested date and time for journey results | Date() |
| `datetimeRepresents` | `String` | ✗ | Can be `.departure` (journeys after datetime) or `.arrival` (journeys before datetime). | .departure |
| `forbiddenUris` | `[String]` | ✗ | Used to avoid lines, modes, networks, etc in the Journey search (List of navitia uris) | ["commercial_mode:Bus", "line:1"] |
| `allowedId` | `[String]` | ✗ | If you want to use only a small subset of the public transport objects in the Journey search (List of navitia uris) | ["commercial_mode:Bus", "line:1"] |
| `allowedPhysicalModes` | `[String]` | ✗ | List of allowed physical modes | ["physical_mode:Bus", "physical_mode:Metro"] |
| `firstSectionModes` | [`Enum]` | ✗ | List of modes to use at the begining of the journey | [.walking, .car, .bike, .bss, .ridesharing] |
| `lastSectionModes` | `[Enum]` | ✗ | List of modes to use at the end of the journey | [.walking, .car, .bike, .bss, .ridesharing] |
| `count` | `Integer` | ✗ | The number of journeys that will be displayed | 3 |
| `minNbJourneys` | `Integer` | ✗ | The minimum number of journeys that will be displayed | 3 |
| `maxNbJourneys` | `Integer` | ✗ | The maximum number of journeys that will be displayed | 10 |
| `addPoiInfos ` | `[Enum]` | ✗ | Allow the display of the availability in real time for bike share and car park | [.bss\_stands, .car\_park] |
| `directPath` | `Enum` | ✗ | To indicate if the journey is direct | .only |
| `dataFreshness` | `Enum` | ✗ | To indicate if theoretical or realtime data are requested | .baseSchedule |
| `travelerType` | `Enum` | ✗ | To give extra information about the traveler state | .standard |

</div>

### Colors

In order to configurate SDK colors, you have to create a `JourneyColorConfiguration` object which takes the following parameters:

<div markdown="1">

| Configuration | Type | Required | Description |
| --- | --- | :---: | --- |
| `primary` | `UIColor?` | ✗ | To set primary colors of Journey. This is used as text color that are highlighted in the module. |
| `background` | `UIColor?` | ✓ | To set background colors of Journey as NavigationController backgroundColor for example. This will be the main color of the module. |
| `origin` | `UIColor?` | ✓ | To set the color of the origin pin icon color on the map and the roadmap departure block. |
| `originIcon` | `UIColor?` | ✗ | To set the color of the origin pin icon color on the map. *origin* value will be ignored. |
| `originBackground` | `UIColor?` | ✗ | To set the color of the roadmap departure block. *origin* value will be ignored. |
| `destination` | `UIColor?` | ✓ | To set the color of the destination pin icon color on the map and the roadmap arrival block. |
| `destinationIcon` | `UIColor?` | ✗ | To set the color of the destination pin icon color on the map. *destination* value will be ignored. |
| `destinationBackground` | `UIColor?` | ✗ | To set the color of the roadmap arrival block. *destination* value will be ignored. |

</div>

### Icons

Customizing transport mode icons and other resources is made possible. To use this feature, you should rename your image resource to match the resource name found below.

##### Transport modes

<div markdown="1">

| Mode | Resource name |
| --- | --- |
| Air | journey_mode_air |
| Bike | journey_mode_bike |
| BSS | journey_mode_bss |
| Bus | journey_mode_bus |
| Car | journey_mode_car |
| Coach | journey_mode_coach |
| Crow fly | journey_mode_crow_fly |
| Ferry | journey_mode_ferry |
| Funicular | journey_mode_funicular |
| Metro | journey_mode_metro |
| Rapid transit | journey_mode_rapidtransit |
| Ridesharing | journey_mode_ridesharing |
| Shuttle | journey_mode_shuttle |
| Taxi | journey_mode_taxi |
| Train | journey_mode_train |
| Tramway | journey_mode_tramway |
| Walking | journey_mode_walking |

</div>

##### Generic

- Realtime

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Parking availability | journey_realtime_park |

</div>

- And more...

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Departure | journey_departure |
| Arrival | journey_arrival |
| My position | journey_my_position |
| Address | journey_address |
| POI | journey_poi |
| Stop area | journey_stop_area |
| Ridesharing pin | journey_ridesharing_pin |

</div>
