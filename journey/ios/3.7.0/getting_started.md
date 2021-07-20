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
- Minimum iOS deployment target: `10.0`

## 💻  Setup

The access to `Journey` module and its dependencies requires valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'JourneySDK', '~> 3.7.0' # Journey Pod definition
end
```

## 👨‍💻 Implementation

This module is set up by calling `JourneySdk.shared`. The singleton has attributes which allow you to configure the module. Then, you need to call the `initialize()` method at the end. \
This method takes the following parameters:

<div markdown="1">

| Configuration | Required | Type | Description | Example |
| --- |:---:| --- | --- | --- |
| `token` | ✓ | `String` | Your Navitia token | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `coverage` | ✓ | `String` | Your Navitia coverage | `fr-idf` |
| `journeyConfiguration` | ✓ | `JourneyConfiguration` | To set colors of Journey and transport configuration |  |

</div>

- Example

```swift     
do {
    let colorsConfiguration = ColorsConfiguration(primary: .blue,
                                                  origin: .pink,
                                                  originIcon: .red,
                                                  destination: .yellow,
                                                  destinationIcon: .green)

    // choose between two ways of transportConfiguration
    var transportConfiguration = nil
    var transportConfigurationJson = nil
    if useJsonFile {
      transportConfigurationJson = "YOUR_CONFIGURATION_FILE.json"
    } else {
      transportConfiguration = TransportConfiguration(linesConfiguration: [], categoriesConfiguration: [])
    }

    let journeyConfiguration = try JourneyConfiguration(colorsConfiguration: colorsConfiguration,
                                                        transportConfiguration: transportConfiguration,
                                                        transportConfigurationJson: transportConfigurationJson)
                                                        .withNextDeparturesFeature(enabled: true)
                                                        .withEarlierLaterFeature(enabled: true)
                                                        .withMultiNetwork(enabled:true)
                                                        .withDisruptionContributor(disruptionContributorTextField.text ?? "")
                                                        .withForm(enabled: true)
                                                        .withFormCustomTransportModes(formButton)

    try JourneySdk.shared.initialize(token: "YOUR_TOKEN",
                                     coverage: "YOUR_COVERAGE",
                                     environment: "YOUR_ENVIRONMENT",
                                     journeyConfiguration: journeyConfiguration)
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}
```

## 🚀 Launching

This module has two entry points: Journeys screen and Form screen.

#### Launching with Form
{: .no_toc }

```swift
let metroButton = ModeButtonModel(title: "Metro",
                                  type: "metro",
                                  iconRes: "ic_metro",
                                  selected: true,
                                  firstSectionMode: ["walking"],
                                  lastSectionMode: ["walking"],
                                  physicalMode: ["physical_mode:Metro"])
let busButton = ModeButtonModel(title: "Bus",
                                type: "bus",
                                iconRes: "ic_bus",
                                selected: true,
                                firstSectionMode: ["walking"],
                                lastSectionMode: ["walking"],
                                physicalMode: ["physical_mode:Bus"])
let tramButton = ModeButtonModel(title: "Tramway",
                                 type: "tramway",
                                 iconRes: "ic_tram",
                                 selected: false,
                                 firstSectionMode: ["walking"],
                                 lastSectionMode: ["walking"],
                                 physicalMode: ["physical_mode:Tramway"])
let trainButton = ModeButtonModel(title: "Train",
                                  type: "train",
                                  iconRes: "ic_train",
                                  selected: false,
                                  firstSectionMode: ["walking"],
                                  lastSectionMode: ["walking"],
                                  physicalMode: ["physical_mode:LocalTrain", "physical_mode:Train"])
let bikeButton = ModeButtonModel(title: "Bike",
                                 type: "bike",
                                 iconRes: "ic_bike",
                                 selected: false,
                                 firstSectionMode: ["bike"],
                                 lastSectionMode: ["bike"],
                                 physicalMode: ["physical_mode:Bike"])
let carButton = ModeButtonModel(title: "Car",
                                type: "car",
                                iconRes: "ic_car",
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

#### Launching with Journeys
{: .no_toc }

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

## 🛠 Configuration

The table below explains the different parameters that you are able to set before launching the `Journey` module.

<div markdown="1">

| Parameters | Type | Description | Default |
| --- | --- |:----| --- |
| `environment` | `ExpertEnvironment` | Navitia environment | `ExpertEnvironment.prod` |
| `formJourney` | `Bool` | To display the journey form screen | `false` |
| `advancedSearchMode` | `Bool` | To enable advanced search mode | `false` (If `formJourney` is set to true, this is automatically switched to true) |
| `maxHistory` | `Int` | To set the maximum number of history inputs for autocompletion | 10 |
| `multiNetwork` | `Bool` | To enable the display of the network name in the roadmap | `false` |
| `isEarlierLaterFeatureEnabled` | `Bool` | To use shortcuts for next and previous journeys | `false` |
| `isNextDepartisNextDeparturesFeatureEnabledure` | `Bool` | To display 3 next departures of the journey | `false` |
| `modeForm` | `[ModeButtonModel]` | To set the shown physical modes, regroup them, set their default selection state | Coverage default value |
| `titlesConfig` | `TitlesConfig?` | To set view controllers titles in navigation view controller | ✗ |
| `disruptionContributor` | `String` | To filter disruption based on source contributor | ✗ |

</div>

- Example

```swift
JourneySdk.shared.enviroment = .prod
JourneySdk.shared.formJourney = false
JourneySdk.shared.advancedSearchMode = false
JourneySdk.shared.maxHistory = 12
JourneySdk.shared.multiNetwork = true
JourneySdk.shared.isEarlierLaterFeatureEnabled = true
JourneySdk.shared.modeForm = [ModeButtonModel(title: "Metro",
                                              type: "metro",
                                              iconRes: "ic_metro",
                                              selected: true,
                                              firstSectionMode: ["walking"],
                                              lastSectionMode: ["walking"],
                                              physicalMode: ["physical_mode:Metro"]),
                              ModeButtonModel(title: "Bus",
                                              type: "bus",
                                              iconRes: "ic_bus",
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

In order to configurate colors, you have to create a `JourneyColorConfiguration` object which takes the following parameters:

<div markdown="1">

| Configuration | Type | Required | Description |
| --- | --- | :---: | --- |
| `background` | `UIColor?` | ✓ | To set background colors of Journey as NavigationController backgroundColor for example. This will be the main color of the module |
| `primary` | `UIColor?` | ✗ | To set primary colors of Journey. This is used as text color that are highlighted in the module |
| `origin` | `UIColor?` | ✓ | To set the color of the origin pin icon color on the map and the roadmap departure block |
| `originIcon` | `UIColor?` | ✗ | To set the color of the origin pin icon color on the map. *origin* value will be ignored |
| `originBackground` | `UIColor?` | ✗ | To set the color of the roadmap departure block. *origin* value will be ignored |
| `destination` | `UIColor?` | ✓ | To set the color of the destination pin icon color on the map and the roadmap arrival block |
| `destinationIcon` | `UIColor?` | ✗ | To set the color of the destination pin icon color on the map. *destination* value will be ignored |
| `destinationBackground` | `UIColor?` | ✗ | To set the color of the roadmap arrival block. *destination* value will be ignored |

</div>

### Icons

Customizing transport mode icons and other resources is made possible. To use this feature, you should rename your image resource to match the resource name found below.

#### Transport modes
{: .no_toc }

<div markdown="1">

| Mode | Resource name |
| --- | --- |
| Air | `journey_mode_air` |
| Bike | `journey_mode_bike` |
| BSS | `journey_mode_bss` |
| Bus | `journey_mode_bus` |
| Car | `journey_mode_car` |
| Coach | `journey_mode_coach` |
| Crow fly | `journey_mode_crow_fly` |
| Ferry | `journey_mode_ferry` |
| Funicular | `journey_mode_funicular` |
| Metro | `journey_mode_metro` |
| Rapid transit | `journey_mode_rapidtransit` |
| Ridesharing | `journey_mode_ridesharing` |
| Shuttle | `journey_mode_shuttle` |
| Taxi | `journey_mode_taxi` |
| Train | `journey_mode_train` |
| Tramway | `journey_mode_tramway` |
| Walking | `journey_mode_walking` |

</div>

#### Generic
{: .no_toc }

##### Realtime
{: .no_toc }

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Parking availability | `journey_realtime_park` |

</div>


#### How to configure Data
{: .no_toc }

- Using JSON file

The JSON file should be added to the main bundle of your project.
Check the example below to know more about the structure of the configuration JSON file:

```
json
{
  "lines": [
    {
      "code": "1",
      "icon_res": "ic_bus_1",
      "commercial": "Bus"
    },
    {
      "code": "2",
      "icon_res": "ic_metro_2",
      "commercial": "Métro"
    },
    {
      "code": "3",
      "icon_res": "ic_local_train_3",
      "commercial": "Train"
    }
  ],
  "categories": [
    {
      "commercial": "Bus",
      "icon_res": "ic_bus",
      "name_res": "bus",
      "subcategories": [
        {
          "name_res": "bus",
          "physical_mode": "physical_mode:Bus",
          "isSelected": false
        }
      ]
    },
    {
      "commercial": "Train",
      "icon_res": "ic_train",
      "name_res": "train",
      "subcategories": [
        {
          "name_res": "RER",
          "physical_mode": "physical_mode:Rer",
          "isSelected": true
        },
        {
          "name_res": "localTrain",
          "physical_mode": "physical_mode:LocalTrain",
          "isSelected": false
        }
      ]
    }
  ],
  "networks": [
    {
      "id": "id1",
      "name": "NETWORK1"
    },
    {
      "id": "id2",
      "name": "NETWORK2"
    }
  ]
}
```

##### And more...
{: .no_toc }

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Departure | `journey_departure` |
| Arrival | `journey_arrival` |
| My position | `journey_my_position` |
| Address | `journey_address` |
| POI | `journey_poi` |
| Station | `journey_stop_area` |
| Ridesharing pin | `journey_ridesharing_pin` |

</div>
