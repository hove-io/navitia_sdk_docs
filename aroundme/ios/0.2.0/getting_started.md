---
layout: default
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

## 🧰 Requirements

- [Cocoapods](https://cocoapods.org): this module is available through Cocoapods.
- Minimum iOS deployment target: 10.0

## 💻 Setup

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

## 🚀 Launching

This module needs to be initialized before launching the main `ViewController`. Therefore, You need to call the `AroundMe.shared.initialize()` method.\
Please refer to the following code:

```swift
do {
    guard let aroundMeViewController = AroundMe.shared.rootViewController else {
      return
    }

    let aroundMeColorsConfiguration = AroundMeColorsConfiguration(background: .gray,
                                                                  primary: .blue)
    let aroundMeConfiguration = try AroundMeConfiguration(colorsConfiguration: aroundMeColorsConfiguration,
                                                          dataConfiguration: DataConfiguration(filtersConfiguration: filtersConfiguration, bookButtonConfiguration: bookButtonConfiguration), // If configurationJsonFile is not set
                                                          dataConfigurationJsonFile: "aroundme_data_configuration_json_filename", // If configuration is not set
                                                          enableGoFromGoTo: enableGoToGoFromOption.isOn)
    
    try AroundMe.shared.initialize(token: navitia_token,
                                   coverage: navitia_coverage,
                                   configuration: aroundMeConfiguration)
    navigationController?.pushViewController(aroundMeViewController, animated: false)
} catch {
    Logger.error("%@", String(format: "AroundMeSDK cannot be initialized! %@", error.localizedDescription))
}
```

## 🛠 Configuration

The `AroundMeConfiguration` is a mandatory element to pass to the `ìnitialize()` method. The below is the list of parameters required to build this configuration object:

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `colorsConfiguration` | ✓ | To set the module colors configuration | ✗ |
| `dataConfiguration` | Only if `dataConfigurationJsonFile`is not set | To set the data configuration | ✗ |
| `dataConfigurationJsonFile` | Only if `dataConfiguration`is not set | To set the data configuration | ✗ |
| `enableGoFromGoTo` | ✗ | To enable or disable the Go from/to feature | `false` |

</div>

### Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `background` | ✓ | To set the background color | ✗ |
| `primary` | ✗ | To set the color of some UI components | `background` |

</div>

### Data

The module has to be configured to work properly. The filters and some UI components require a configuration or else you won't be able to launch the SDK.\
There are two main sections to configure: `filters` and `book_button`.

The `filters` sets up the list of the categories/subcategories/types to be displayed in the filters page.\
The `book_button` sets up the label to be displayed on the booking button when different UI components are shown on the screen.

- Filters

The `filters` is a JSON array of categories. Each category has subcategories and each subcategory has types.

###### Category

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `category_name_res` | String | ✓ | String resource ID of the category name |
| `subcategories` | Array | ✓ | List of subcategories |

</div>

###### Subcategory

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | String resource ID of the subcategory name |
| `icon_res` | String | ✓ | Icon resource ID to be displayed within the map marker |
| `selected` | Boolean | ✓ | Whether this subcategory is selected by default or not |
| `group` | Integer | ✓ | `0`: Transport mode / `1`: POI |
| `types` | Array | ✓ | List of the subcategory types |

</div>

###### Subcategory type

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | String resource ID of the subcategory type name |
| `id` | String | ✓ | Navitia ID generally preceded by `physical_mode` or `poi_type` |

</div>

- Book Button

The `book_button` is a JSON object that contains String resource IDs for the book button label in different UI components.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `bss_res` | String | ✓ | String resource ID of the booking label when the BSS component is shown |
| `car_park_res` | String | ✓ | String resource ID of the booking label when the car park component is shown |
| `stop_point_res` | String | ✓ | String resource ID of the booking label when the stop point component is shown |

</div>

### How to configure Data?

Follow one of the steps below:

- Using JSON file

The JSON file should be added to the main bundle of your project.
Please check the example below to know more about the structure of the configuration JSON file:

```json
    {
      "filters": [
        {
          "category_name_res": "transport",
          "subcategories": [
            {
              "name_res": "metro",
              "icon_res": "ic_section_mode_metro",
              "selected": true,
              "group": 0,
              "types": [
                {
                  "name_res": "metro",
                  "id": "physical_mode:Metro"
                }
              ]
            },
            {
              "name_res": "bus",
              "icon_res": "ic_section_mode_bus",
              "selected": true,
              "group": 0,
              "types": [
                {
                  "name_res": "bus",
                  "id": "physical_mode:Bus"
                }
              ]
            }
          ]
        },
        {
          "category_name_res": "poi",
          "subcategories": [
            {
              "name_res": "bss_station",
              "icon_res": "ic_amenity_bicycle_rental",
              "selected": true,
              "group": 1,
              "types": [
                {
                  "name_res": "bss_station",
                  "id": "poi_type:amenity:bicycle_rental"
                }
              ]
            },
            {
              "name_res": "parking",
              "icon_res": "ic_amenity_parking",
              "selected": true,
              "group": 1,
              "types": [
                {
                  "name_res": "parking",
                  "id": "poi_type:amenity:parking"
                }
              ]
            }
          ]
        }
      ],
      "book_button": {
        "bss_res": "book_bss",
        "car_park_res": "book_car_park",
        "stop_point_res": "book_stop_point"
      }
    }
```

- Using Configuration object

```swift
let filtersConfiguration = [
    // Add stations category
    ConfigurationFilterCategory(categoryNameRes: "stations", subcategories: [
        ConfigurationFilterSubcategory(
            nameRes: "metro",
            iconRes: "ic_section_mode_metro",
            selected: true,
            group: SubcategoryFilterGroup.TRANSPORT_MODE,
            types: [ConfigurationFilterSubcategoryType(id: "metro", nameRes: "physical_mode:Metro")]
        ),
        ConfigurationFilterSubcategory(
            nameRes: "bus",
            iconRes: "ic_section_mode_bus",
            selected: true,
            group: SubcategoryFilterGroup.TRANSPORT_MODE,
            types: [ConfigurationFilterSubcategoryType(id: "bus", nameRes: "physical_mode:Bus")]
        )
    ]),
    // Add services category
    ConfigurationFilterCategory(categoryNameRes: "mobility_services", subcategories: [
        ConfigurationFilterSubcategory(
            nameRes: "bss_station",
            iconRes: "ic_amenity_bicycle_rental",
            selected: true,
            group: SubcategoryFilterGroup.POI,
            types: [ConfigurationFilterSubcategoryType(id: "bss_station", nameRes: "poi_type:amenity:bicycle_rental")]
        ),
        ConfigurationFilterSubcategory(
            nameRes: "parking",
            iconRes: "ic_amenity_parking",
            selected: true,
            group: SubcategoryFilterGroup.POI,
            types: [ConfigurationFilterSubcategoryType(id: "parking", nameRes: "poi_type:amenity:parking")]
        )
    ])
]

let bookButtonConfiguration = ConfigurationBookButton(bssRes: "book_bss", carParkRes: "book_car_park", stopPointRes: "book_stop_point")         
let dataConfiguration = ConfigurationRoot(filtersConfiguration: filtersConfiguration, bookButtonConfiguration: bookButtonConfiguration)
```

Please note that calling `AroundMe.shared.resetUserPreferences()` will reset filters configuration and the content of the [filters](/navitia_sdk_docs/aroundme/ios/screen#filters) screen.
