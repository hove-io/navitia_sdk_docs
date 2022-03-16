---
layout: main
title: Getting started
parent: Schedule iOS
grand_parent: Schedule
nav_order: 2
permalink: /schedule/ios/getting-started
---

# Getting Started
{: .no_toc }

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 🧰 Requirements

- [Cocoapods](https://cocoapods.org): this module is available through Cocoapods.
- Minimum iOS deployment target: 10.0

## 💻  Setup

The access to `Schedule` module and its dependencies requires valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Schedule podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'ScheduleSDK', '~> 2.0.0' # Schedule Pod definition
end
```

## 👨‍💻 Implementation

Each module are configurable with a unique configuration.
This module is set up by calling `Schedule.shared`. The singleton has attributes which allow you to configure the module. Then, you need to call the `initialize()` method at the end.

### Parameters 
{: .no_toc }

<div markdown="1">

| Name | Required | Description | Type |
| --- |:---:| --- | --- | 
| `coverage`| ✓ | Your Navitia coverage | `String` | 
| `token`| ✓ | Your Navitia token | `String` | 
| `env`| ✓ | Your Navitia environment | `String` | 
| `colors`| ✓ | To set colors of this module | `ScheduleColorsConfiguration` |
| `lineResources`| ✗ | To set an array of transport lines resources | `[LineResource]` | 
| `modeResources`| ✗ | To set an array of transport modes resources | `[ModeResource]` | 
| `transportCategories` | ✗ | To set an array of transport modes | `[TransportCategory]` | 
| `networkResources`| ✗ | To set an array of network resources | `[NetworkResource]` | 

</div>

- Example

```swift
do {
    let transportCategories = [
      TransportCategory(
        modules: ["Schedule"],
        iconRes: "ic_section_mode_metro",
        nameRes: "metro",
        selected: true,
        physicalModes: [
            TransportPhysicalMode(physicalModeId: "physical_mode:Metro", nameRes: "metro")
        ],
        firstSectionModes: ["walking"],
        lastSectionModes: ["walking"],
        addPoiInfos: []
      )
    ]
                                                 
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

    let scheduleColors = ScheduleColorsConfiguration(
      primaryColor: "#251942",
      secondaryColor: "#c0392v"
    )

    let networkResources = [
      NetworkResource(
        networkId: "ratb", 
        iconRes: "ic_ratb", 
        nameRes: "RATB"
      )
    ]
                                                                      
    try Schedule.shared.initialize(
      coverage: "fr-idf",
      token: "0de19ce5-e0eb-4524-a074",
      env: "PROD",
      colors: scheduleColorsConfiguration,
      lineResources: lineResources,
      modeResources: modeResource,
      transportCategories: transportCategories,
      networkResources: networkResources
    )                                                                  
} catch {
    Logger.error("%@", String(format: "Schedule SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

- Example with JSON file

```swift
do {
    try Schedule.shared.initialize(configurationJsonFile: "configuration-file.json")                                                               
} catch {
    Logger.error("%@", String(format: "Schedule SDK cannot be initialized! %@", error.localizedDescription))
}
```

## 🚀 Launching


```swift
guard let scheduleViewController = Schedule.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(scheduleViewController, animated: false)
```


## 🛠 Configuration

### Colors

The object `ScheduleColorsConfiguration` allow you to configure the colors of the SDK.

#### `ScheduleColorsConfiguration`
{: .no_toc }

<div markdown="1">

| Name | Required | Description | Type | Default | 
| --- |:---:| --- | --- |--- |
| `primaryColor`| ✗ | To define the primary color of the SDK | `String` | `""` |
| `secondaryColor`| ✗ | To define the secondary color of the SDK | `String` | `""` |

</div>

- Example

```swift
    let scheduleColors = ScheduleColorsConfiguration(primaryColor: "#251942",
                                                     secondaryColor: "#c0392v")
```

### Configuring with JSON file

The JSON file should be added to the main bundle of your project.
See the example below to know more about the structure of the configuration JSON file :

```json
{
  "coverage": "fr-idf",
  "token": "0de1-9ce5bd-a3c689-4c19",
  "env": "PROD",
  "colors": {
    "schedule":{
        "primary_color": "#251942",
        "secondary_color": "#0EBDAB"
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
        "code": "2",
        "icon_res": "ic_metro_2",
        "commercial": {
            "name": "Métro",
            "id": "commercial_mode:Metro"
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
        "schedule"
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
          "schedule"
      ],
      "icon_res": "ic_section_mode_train",
      "name_res": "train",
      "selected": true,
      "physical_modes": [
        {
          "name_res": "rer",
          "physical_mode_id": "physical_mode:RapidTransit"
        },
        {
          "name_res": "ter",
          "physical_mode_id": "physical_mode:LocalTrain"
        },
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
  "networks_resources": [
    {
      "network_id": "network:paris",
      "name_res": "network_paris"
    }
  ]
}
```