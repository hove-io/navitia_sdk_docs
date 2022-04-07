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

source 'https://github.com/hove-io/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'JourneySDK', '~> 4.0.0' # Journey Pod definition
end
```

## 👨‍💻 Implementation

Each module are configurable with a unique configuration.
This module is set up by calling `JourneySdk.shared`. The singleton has attributes which allow you to configure the module. Then, you need to call the `initialize()` method at the end. 

#### Parameters 
{: .no_toc }

<div markdown="1">

| Name | Required | Description | Type | Default | 
| --- |:---:| --- | --- | --- | 
| `coverage`| ✓ | Your Navitia coverage | `String` | none | 
| `token`| ✓ | Your Navitia token | `String` | none  | 
| `env`| ✓ | Your Navitia environment | `String` | none | 
| `colors`| ✓ | To set colors of this module | `JourneyColorsConfiguration` | none | 
| `lineResources`| ✗ | To set an array of transport lines resources | `[LineResource]` | [] | 
| `modeResources`| ✗ | To set an array of transport modes resources | `[ModeResource]` | [] | 
| `providers`| ✗ | To set an array of external providers resources | `[ProviderResources]` | [] | 
| `titleResources`| ✗ | To set an array of different screen titles | `JourneyTitlesResources` | JourneyTitlesResources() | 
| `transportCategories` | ✗ | To set an array of transport modes | `[TransportCategory]` | [] |
| `disruptionContributors` | ✗ | To set an array of disruptions contributors | `[String]` | [] |
| `autocompleteHistoryMaxCount` | ✗ | To set the maximum elements to save in the history of autocomplete | `Int` | `10` |
| `features`| ✗ | To set an array of different screen titles | `JourneyFeaturesConfiguration` | JourneyFeaturesConfiguration() | 

</div>

- Example

```swift
do {
    let transportCategories = [
      TransportCategory(
        modules: ["journey"],
        iconRes: "ic_section_mode_metro",
        nameRes: "metro",
        selected: true,
        physicalModes: [
          TransportPhysicalMode(
            physicalModeId: "physical_mode:Metro",
            nameRes: "metro"
          )
        ],
        firstSectionModes: ["walking"],
        lastSectionModes: ["walking"],
        addPoiInfos: []
      )
    ]
                              
    let journeyColorsConfiguration  = JourneyColorsConfiguration(
      primaryColor: "#251942",
      secondaryColor: "#c0392v",
      destinationColor: "#0EBDAB",
      destinationBackgroundColor: "#2ecc71",
      destinationIconColor: "#2ecc71",
      originColor: "#2ecc71",
      originBackgroundColor: "#c0392b",
      originIconColor: "#c0392b",
      navBarBackgroundColor: "#c0392b"
    )

    // This module has two entry points: Journeys screen (value = "journeys") and Form screen (value = "form").                
    let journeyFeaturesConfiguration = JourneyFeaturesConfiguration(
      entryPoint: "form",
      nextDepartures: true,
      transportNetworks: true,
      earlierLater: true,
      enableAutocomplete: true,
      maxHistory: 30,
      disruptionContributors: []
    )

    let lineResources = [
      LineResource(
        code: "1",
        iconRes: "ic_metro_1",
        commercial: CommercialMode(name: "Métro", id: "commercial_mode:Metro")
      )
    ]   
                                                                 
    let modeResources = [
      ModeResource(
        iconRes: "ic_metro", 
        commercial: CommercialMode(name: "Métro", id: "commercial_mode:Metro")
      )
    ] 

    let providers = [
      ProviderResource(
        typeId: "providerTypeId", 
        providerId: "providerID", 
        iconRes: "provider_icon_res"
      )
    ]
                                                                      
    try JourneySdk.shared.initialize(
      coverage: "fr-idf",
      token: "0de19ce5-e0eb-4524-a074",
      env: "PROD",
      colors: journeyColorsConfiguration,
      lineResources: lineResources,
      modeResources: modeResources,
      providers: providers,
      titleResources: JourneyTitlesResources(form: "Formulaire"),
      transportCategories: transportCategories,
      disruptionContributors: ["contributors_id1", "contributors_id2"],
      autocompleteHistoryMaxCount: 15,
      features: journeyFeaturesConfiguration
    )                                                                  
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

- Example with JSON file

```swift
do {
    try JourneySdk.shared.initialize(configurationJsonFile: "configuration-file.json")                                                               
} catch {
    Logger.error("%@", String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
}
```

## 🚀 Launching


```swift
guard let journeyViewController = JourneySdk.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(journeyViewController, animated: false)
```


## 🛠 Configuration

### Colors

The object `JourneyColorsConfiguration` allow you to configure the colors of the SDK.

#### `JourneyColorsConfiguration`
{: .no_toc }

<div markdown="1">

| Name | Required | Description | Type | Default |
| --- |:---:| --- | --- | --- | 
| `primaryColor`| ✗ | To define the primary color of the SDK | `String` | `""` | 
| `secondaryColor`| ✗ | To define the secondary color of the SDK | `String` | `""` | 
| `destinationColor`| ✗ | To set the color of the destination pin icon color on the map and the roadmap arrival block | `String` | `""` | 
| `destinationBackgroundColor`| ✗ | To set the color of the roadmap arrival block. destination value will be ignored | `String` | `""` | 
| `destinationIconColor`| ✗ | To set the color of the destination pin icon color on the map. destination value will be ignored | `String` | `""` |
| `originColor`| ✗ | To set the color of the origin pin icon color on the map. origin value will be ignored | `String` | `""` | 
| `originBackgroundColor`| ✗ | To set the color of the roadmap departure block. origin value will be ignored | `String` | `""` |
| `originIconColor`| ✗ | To set the color of the origin pin icon color on the map. origin value will be ignored | `String` | `""` |
| `navBarBackgroundColor`| ✗ | To set the color of the navigationbarBackground if it exists | `String?` | `nil` | 

</div>

- Example

```swift
    let journeyColorsConfiguration = JourneyColorsConfiguration(
        primaryColor: "#251942",
        secondaryColor: "#c0392v",
        destinationColor: "#0EBDAB",
        destinationBackgroundColor: "#2ecc71",
        destinationIconColor: "#2ecc71",
        originColor: "#2ecc71",
        originBackgroundColor: "#c0392b",
        originIconColor: "#c0392b",
        navBarBackgroundColor: "#c0392b"
    )
```

### Features

The object `JourneyFeatureConfiguration` allow you to configure the features of the SDK.

#### `JourneyFeatureConfiguration` 
{: .no_toc }

<div markdown="1">

| Name | Required | Description | Type | Default | 
| --- |:---:| --- | --- | --- | 
| `entryPoint`| ✗ | To define the entry point : journeys screen or form screen | `JourneyEntryPoint` | `form` | 
| `nextDepartures`| ✗ | This feature allows to see the next departures of a transport | `Bool` | `false` | 
| `transportNetworks`| ✗ | This feature allows to show the networks informations | `Bool` | `false` | 
| `earlierLater`| ✗ | This feature allows to make a new search with earlier or later timestamp in one clic  | `Bool` | `false` | 
| `enableAutocomplete`| ✗ | This feature allows a smart autocomplete in the search text fields | `Bool` | `false` |

</div>

- Example

```swift
    let journeyFeaturesConfiguration = JourneyFeaturesConfiguration(
        entryPoint: "journeys",
        nextDepartures: true,
        transportNetworks: true,
        earlierLater: true,
        enableAutocomplete: true
    )
```

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

<div markdown="1">

| Context | Resource name |
| --- | --- |
| Parking availability | `journey_realtime_park` |
| Departure | `journey_departure` |
| Arrival | `journey_arrival` |
| My position | `journey_my_position` |
| Address | `journey_address` |
| POI | `journey_poi` |
| Station | `journey_stop_area` |
| Ridesharing pin | `journey_ridesharing_pin` |

</div>

### Configuring with JSON file
​
The JSON file should be added to the `Resources` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

```json
{
  "coverage": "fr-idf",
  "token": "0de1-9ce5bd-a3c689-4c19",
  "env": "PROD",
  "colors": {
    "journey":{
        "primary_color": "#251942",
        "secondary_color": "#0EBDAB",
        "destination_color": "#2ecc71",
        "destination_background_color": "#2ecc71",
        "destination_icon_color": "#2ecc71",
        "origin_color": "#c0392b",
        "origin_background_color": "#c0392b",
        "origin_icon_color": "#c0392b",
        "nav_bar_background_color": "#ffffff"
    }
  },
  "lines_resources": [
      {
        "code": "1",
        "icon_res": "ic_metro_1",
        "commercial": {
            "name": "Métro",
            "id": "commercial_mode:Metro"
        }
      },
      {
        "code": "A",
        "icon_res": "ic_rer_a",
        "commercial": {
            "name": "RER",
            "id": "commercial_mode:RER"
        }
      }
    ],
  "modes_resources": [
    {
      "icon_res": "ic_metro",
      "commercial": {
        "name": "Métro",
        "id": "commercial_mode:Metro"
      }
    },
    {
      "icon_res": "ic_rer",
      "commercial": {
        "name": "RER",
        "id": "commercial_mode:RER"
      }
    }
  ],
  "transport_categories": [
    {
      "modules": [
        "journey"
      ],
      "icon_res": "ic_section_mode_metro",
      "name_res": "metro",
      "selected": true,
      "physical_modes": [
        {
          "physical_mode_id": "physical_mode:Metro",
          "name_res": "metro"
        }
      ]
    },
    {
      "modules": [
          "journey"
      ],
      "icon_res": "ic_section_mode_train",
      "name_res": "train",
      "selected": true,
      "physical_modes": [
        {
          "name_res": "train",
          "physical_mode_id": "physical_mode:Train"
        },
        {
          "name_res": "long_distance_train",
          "physical_mode_id": "physical_mode:LongDistanceTrain"
        }
      ]
    }
  ],
  "titles_resources": {
    "journey": {
      "form": "journey_form_screen_title",
      "journeys": "journey_journeys_screen_title",
      "roadmap": "journey_form_roadmap_title",
      "ridesharing": "journey_form_ridesharing_title",
      "autocomplete": "journey_form_autocomplete_title",
    }
  },
  "features_configuration": {
    "max_history": 10,
    "disruption_contributors": [
        "shortterm.tr_idfm"
    ],
    "journey": {
      "entry_point": "form",
      "enable_autocomplete": true
    }
  }
}
```