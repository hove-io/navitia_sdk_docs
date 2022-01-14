---
layout: main
title: Getting started
parent: Around Me iOS
grand_parent: Around Me
nav_order: 2
permalink: /aroundme/ios/getting-started
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

The access to `Around Me` module and its dependencies requires valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Around Me podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'AroundMeSDK', '~> 0.2.0' # Around Me Pod definition
end
```

## 👨‍💻  Implementation

This module is set up by calling `AroundMe.shared`. The singleton has attributes which allow you to configure the module. 
Then, you need to call the `initialize()` method at the end. \

### Parameters of `AroundMe.shared.initialize()`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `coverage`| ✓ | To define the coverage of Navitia | `String` | `fr-idf`
| `token`| ✓ | To define the token of Navitia | `String` | `0de19ce5-e0eb-4524-a074-bda3c6894c19`
| `env`| ✓ | To define the environment of Navitia | `String` | `PROD`
| `colors`| ✓ | To define the color configuration | `AroundMeColorsConfiguration` |
| `lineResources`| ✗ | To define the transport lines | `[LineResource]` | 
| `modeResources`| ✗ | To define the transport modes | `[ModeResource]` | 
| `transportCategories`| ✗ | To define the transport configuration | `[TransportCategory]` | 
| `poiCategories`| ✗ | To define the configuration of the POI's | `[PoiCategory]` | 
| `providerResources`| ✗ | To define the configuration of the providers | `[ProviderResources]` | 
| `bookingResources`| ✗ | To define the booking informations | `AroundMeBookingResources` | 
| `titleResources`| ✗ | To define the different titles for the filter page | `AroundMeTitlesResources` | 
| `features`| ✓ | To activate some options (goFrom/goTo, booking, defaultLocation)  | `AroundMeFeaturesConfiguration` | 

</div>

### Example of initialization

```swift
do {
    let transportCategories = [TransportCategory(modules: ["aroundme"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 physicalModes: [TransportPhysicalMode(physicalModeId: "physical_mode:Metro",
                                                                                       nameRes: "metro")
                                                                ],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"],
                                                 addPoiInfos: [])
                              ]
                              
    let aroundmeColorsConfiguration = AroundMeColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                    
    let aroundMeFeaturesConfiguration = AroundMeFeaturesConfiguration(goFromGoTo: false,
                                                                      bookingInfo: true,
                                                                      defaultLocation: AroundMeLocation(lat: "48.846790", lon: "2.377090"))
                                                                      
    try AroundMe.shared.initialize(coverage: "fr-idf",
                                   token: "0de19ce5-e0eb-4524-a074-bda3c6894c19",
                                   env: "PROD",
                                   colors: aroundmeColorsConfiguration,
                                   transportCategories: transportCategories,
                                   features: aroundMeFeaturesConfiguration)                                                                  
} catch {
    Logger.error("%@", String(format: "Around me SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

### Example of initialization with JSON file

```swift
do {
    try AroundMe.shared.initialize(configurationJsonFile: "aroundme_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Around me SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. 

```swift
guard let aroundMeViewController = AroundMe.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(aroundMeViewController, animated: false)
```

## 🛠 Configuration

### Colors

The object `AroundMeColorsConfiguration` allow you to configure the colors of the SDK.

#### Parameters of `AroundMeColorsConfiguration`

<div markdown="1">

| Name | Required | Description | Type | Default | Example
| --- |:---:| --- | --- |--- |
| `primaryColor`| ✗ | To define the primary color of the SDK | `String` | `""` | `#88819f`
| `secondaryColor`| ✗ | To define the secondary color of the SDK | `String` | `""` | `#8faa96`

</div>

#### Example of initialization

```swift
    let aroundmeColorsConfiguration = AroundMeColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
```

### Icons
​
The module offers the possibility to customize the icons of modes of transport and lines. You may need to request Navitia first to get your available list of lines and commercial modes for your coverage:<br> `https://api.navitia.io/v1/coverage/<COVERAGE>/lines`
​
- Transport lines

The `lineResource` is an object of transport lines datas.

#### Parameters of `lineResource`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `code`| ✓ | To define the code of a transport line | `String` | `123`
| `iconRes`| ✓ | To define the name of the icon resource of a transport line | `String` | `ic_bus_123`
| `commercial`| ✓ | To define the commercial mode | `CommercialMode` | `CommercialMode(id: "id", name: "Bus 123")`

</div>

#### Example of initialization

```swift
    let commercialMode = CommercialMode(id: "id", name: "Bus")
    let lineResource = [LineResource(code: "123", iconRes: "ic_bus_123", commercial: commercialMode)]  
```

- Transport modes

The `ModeResource` is an object of transport modes datas.

#### Parameters of `ModeResource`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `iconRes`| ✓ | To define the name of the icon resource of a transport mode | `String` | `ic_bus`
| `commercial`| ✓ | To define the commercial mode | `CommercialMode` | `CommercialMode(id: "id", name: "Bus")`

</div>

#### Example of initialization

```swift
    let commercialMode = CommercialMode(id: "id", name: "Bus")
    let modeResource = ModeResource(iconRes: "ic_bus", commercial: commercialMode)]  
```

- POI's

The `PoiCategory` is an object that content POI informations.

#### Parameters of `PoiCategory`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `nameRes`| ✓ | To define the name of a POI category | `String` | `free floatings`
| `subcategories`| ✓ | To define the severals subcategories of POI's with there properties | `[PoiSubcategory]` | 

</div>

#### Parameters of `PoiSubcategory`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `iconRes`| ✓ | To define the name of the icon resource of a POI subcategory | `String` | `ic_bike`
| `nameRes`| ✓ | To define the name of the POI | `String` | `bike`
| `selected`| ✓ | To define the default value of selection in filter page | `Bool` | `true`
| `group`| ✓ | Is an enum that define the group of POI it belongs to | `SubcategoryGroup` | `.freeFloating`
| `types`| ✓ | To define the type of subcategory it belongs to | `[PoiTypeSubcategory]` | `[PoiTypeSubcategory(nameRes: "bike", poiTypeId: "BIKE")]`

</div>

#### Example of initialization

```swift
    let poiTypeSubCategory = PoiTypeSubcategory(nameRes: "bike", 
                                                poiTypeId: "BIKE")
                                                
    let subcategory = PoiSubcategory(iconRes: "ic_bike",
                                      nameRes: "bike",
                                      selected: true,
                                      group: .freeFloating,
                                      types: [poiTypeSubCategory])
                                      
    let poiCategory = PoiCategory(nameRes: "free floating",
                                   subcategories: [subcategorie]) 
```

- Providers

The `ProviderResource` is an object that content the provider informations.

#### Parameters of `ProviderResource`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `typeId`| ✓ | To define the identifier of a poi type | `String` | `SCOOTER`
| `providerId`| ✓ | To define the identifier of a provider | `String` | `Lime`
| `iconRes`| ✓ | To define the name of the icon resource for a poi that belongs to the specific provider | `String` | `ic_lime`

</div>

#### Example of initialization

```swift
    let providerResource = ProviderResource(typeId: "SCOOTER",
                                            providerId: "Lime",
                                            iconRes: "ic_lime") 
```

### Text customisation

The module offers the possibility to customize some texts like titles or booking informations. 

- Booking informations

The `AroundMeBookingResources` is an object that content booking informations.

#### Parameters of `AroundMeBookingResources`

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `bssRes`| ✓ | To define the localizable string id of BSS informations | `String` | `book_bss`
| `carParkRes`| ✓ | To define the localizable string id of car park informations | `String` | `car_park_bss`
| `stopPointRes`| ✓ | To define the localizable string id of stop point informations  | `String` | `stop_point_bss`

</div>

#### Example of initialization

```swift
    let bookingResources = AroundMeBookingResources(bssRes: "book_bss",
                                                    carParkRes: "car_park_bss",
                                                    stopPointRes: "stop_point_bss")
```

- Titles

The `AroundMeTitlesResources` is an object that content titles.

#### Parameters of `AroundMeTitlesResources` :  

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `filters`| ✓ | To define the localizable string id of the filter page title | `String` | `filters_screen_title`

</div>

#### Example of initialization :  

```swift
    let titlesResources = AroundMeTitlesResources(filters: "filters_screen_title")
```

### Transport categories and filters

The object `TransportCategory` allow you to define a category of transport. It is also used to be displayed in the filters page.

#### Parameters of `TransportCategory` :  

<div markdown="1">

| Name | Required | Description | Type | Example
| --- |:---:| --- | --- |
| `modules`| ✓ | To define the modules to implement | `[String]` | `["aroundme", "traffic", "journey"]`
| `iconRes`| ✓ | To define the name of the icon resource | `String` | `ic_bus`
| `nameRes`| ✓ | To define the name of the transport | `String` | `bus`
| `selected`| ✓ | To define the default value of selection in filter| `Bool` | `true`
| `physicalModes`| ✓ | To define the commercial mode | `[TransportPhysicalMode]` | `[TransportPhysicalMode(physicalModeId: "physical_mode:Bus", nameRes: "bus")]`
| `firstSectionModes`| ✓ | To define the first section modes | `[String]` | `["walking"]`
| `lastSectionModes`| ✓ | To define the last section modes | `[String]` | `["walking"]`
| `addPoiInfos`| ✓ | To define the last section modes | `[String]` | 

</div>

#### Example of initialization : 

```swift
    let physicalModes = [TransportPhysicalMode(physicalModeId: "physical_mode:Metro", nameRes: "metro")]
    let transportCategorie = TransportCategory(modules: ["aroundme"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 physicalModes: physicalModes,
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"],
                                                 addPoiInfos: [])
```

### Features

The object `AroundMeFeaturesConfiguration` allow you to enable or not some features.

#### Parameters of `AroundMeFeaturesConfiguration` :  

<div markdown="1">

| Name | Required | Description | Type | Default | Example
| --- |:---:| --- | --- |--- |
| `goFromGoTo`| ✗ | To enable the possibility of "go from/go to" feature if Journey is implemented too | `Bool` | `false` | `true`
| `bookingInfo`| ✗ | Sets up the label to be displayed on the booking button when different UI components are shown on the screen | `Bool` | `false` | `true`
| `defaultLocation`| ✗ | To add a default location if user don't allow his location | `AroundMeLocation` | `AroundMeLocation(lat: "48.846790", lon: "2.377090")`

</div>

#### Example of initialization : 

```swift
   let aroundMeLocation = AroundMeLocation(lat: "48.846790", lon: "2.377090")
   let featureConfiguration = AroundMeFeaturesConfiguration(goFromGoTo: false, 
                                                            bookingInfo: true, 
                                                            defaultLocation: aroundMeLocation)
```

### Configuring with JSON file
​
- Using JSON file

The JSON file should be added to the `Resources` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

```json
    {
  "coverage": "fr-idf",
  "token": "0de19ce5-e0eb-4524-a074-bda3c6894c19",
  "env": "PROD",
  "colors": {
    "aroundme": {
      "primary_color": "#251942",
      "secondary_color": "#0EBDAB"
    },
    "traffic":{
        "primary_color": "#251942",
        "secondary_color": "#0EBDAB"
    },
    "journey":{
        "primary_color": "#251942",
        "secondary_color": "#0EBDAB",
        "destination_color": "#2ecc71",
        "destination_background_color": "#2ecc71",
        "destination_icon_color": "#2ecc71",
        "origin_color": "#c0392b",
        "origin_background_color": "#c0392b",
        "origin_icon_color": "#c0392b"
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
      },
      {
        "code": "3",
        "icon_res": "ic_metro_3",
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
      },
      {
        "code": "B",
        "icon_res": "ic_rer_b",
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
        "aroundme", "traffic", "journey"
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
          "aroundme", "traffic", "journey"
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
  "poi_categories": [
    {
      "name_res": "free_floatings",
      "subcategories": [
        {
          "name_res": "scooter",
          "icon_res": "ic_scooter",
          "selected": true,
          "group": "FREE_FLOATING",
          "types": [
            {
              "name_res": "scooter",
              "poi_type_id": "SCOOTER"
            }
          ]
        },
        {
          "name_res": "motorscooter",
          "icon_res": "ic_motorscooter",
          "selected": true,
          "group": "FREE_FLOATING",
          "types": [
            {
              "name_res": "motor scooter",
              "poi_type_id": "MOTORSCOOTER"
            }
          ]
        },
        {
          "name_res": "bike",
          "icon_res": "ic_bike",
          "selected": true,
          "group": "FREE_FLOATING",
          "types": [
            {
              "name_res": "bike",
              "poi_type_id": "BIKE"
            }
          ]
        },
        {
          "name_res": "car",
          "icon_res": "ic_car",
          "selected": true,
          "group": "FREE_FLOATING",
          "types": [
            {
              "name_res": "car",
              "poi_type_id": "CAR"
            }
          ]
        }
      ]
    },
    {
      "name_res": "mobility_services",
      "subcategories": [
        {
          "name_res": "vls_station",
          "icon_res": "ic_amenity_bicycle_rental",
          "selected": true,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "vls_station",
              "poi_type_id": "poi_type:amenity:bicycle_rental"
            }
          ]
        },
        {
          "name_res": "parking",
          "icon_res": "ic_amenity_parking",
          "selected": true,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "parking",
              "poi_type_id": "poi_type:amenity:parking"
            }
          ]
        },
        {
          "name_res": "bike_station",
          "icon_res": "ic_amenity_bicycle_parking",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "bike_station",
              "poi_type_id": "poi_type:amenity:bicycle_parking"
            }
          ]
        }
      ]
    },
    {
      "name_res": "other_services",
      "subcategories": [
        {
          "name_res": "mairie",
          "icon_res": "ic_amenity_townhall",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "mairie",
              "poi_type_id": "poi_type:amenity:townhall"
            }
          ]
        },
        {
          "name_res": "hospital",
          "icon_res": "ic_amenity_hospital",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "hospital",
              "poi_type_id": "poi_type:amenity:hospital"
            }
          ]
        },
        {
          "name_res": "poste",
          "icon_res": "ic_amenity_post_office",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "poste",
              "poi_type_id": "poi_type:amenity:post_office"
            }
          ]
        },
        {
          "name_res": "theatre",
          "icon_res": "ic_amenity_theatre",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "theatre",
              "poi_type_id": "poi_type:amenity:theatre"
            }
          ]
        },
        {
          "name_res": "university",
          "icon_res": "ic_amenity_university",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "school",
              "poi_type_id": "poi_type:amenity:university"
            }
          ]
        },
        {
          "name_res": "garden",
          "icon_res": "ic_leisure_garden",
          "selected": false,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "garden",
              "poi_type_id": "poi_type:leisure:garden"
            }
          ]
        }
      ]
    }
  ],
  "providers_resources": [
    {
      "type_id": "MOTORSCOOTER",
      "provider_id": "Cityscoot",
      "icon_res": "ic_motorscooter_cityscoot"
    },
    {
      "type_id": "SCOOTER",
      "provider_id": "Lime",
      "icon_res": "ic_lime"
    },
    {
      "type_id": "SCOOTER",
      "provider_id": "Lime",
      "icon_res": "ic_scooter_lime"
    },
    {
      "type_id": "SCOOTER",
      "provider_id": "Tier",
      "icon_res": "ic_scooter_tier"
    }
  ],
  "booking_resources": {
    "booking_bss_res": "book_bss",
    "booking_car_park_res": "book_car_park",
    "booking_stop_point_res": "book_stop_point"
  },
  "titles_resources": {
    "aroundme": {
      "filters": "filters_screen_title"
    },
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
    },
    "aroundme": {
      "go_from_go_to": true,
      "booking_info": true,
      "default_location": {
        "lat": "48.846790",
        "lon": "2.377090"
      }
    }
  }
}

```

Please note that calling `AroundMe.shared.resetUserPreferences()` will reset filters configuration and the content of the [filters](/navitia_sdk_docs/aroundme/ios/screen#filters) screen.
