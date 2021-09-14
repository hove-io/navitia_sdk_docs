---
layout: main
title: Getting started
parent: Around Me Android
grand_parent: Around Me
nav_order: 2
permalink: /aroundme/android/getting-started
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

## 💻  Setup

The access to `Around Me` module requires valid credentials to our private artifactory. Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials:

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
    implementation("com.kisio.navitia.sdk.ui:aroundme:1.0.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key:

```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Around Me must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

```xml
<activity
    ...
    android:configChanges="orientation|screenSize"
    .../>
```

## 👨‍💻  Implementation

This module is set up by calling `AroundMeUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. \
This method takes the following parameters:

<div markdown="1">

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| `context` | `Context` | ✓ | Context in which the module is launched | ✗ |
| `colors` | `AroundMeColors` | ✓ | Module colors configuration | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `env` | `AroundMeEnvironment` | ✓ | Navitia API environment | ✗ |
| `configuration` | `Configuration` | Only if `configurationJsonFile` is not set | Data configuration of the module | `null` |
| `configurationJsonFile` | `String` | Only if `Configuration` is not set | Json file name in `assets` folder | `null` |
| `defaultLocation` | `LatLng` | ✗ | Default map center location | `DEFAULT_MALOT_LAT_LNG` |
| `onNavigate` | `Unit` | ✗ | Listener for the navigation between module screens | `{ _ -> }` |
| `onBack` | `Unit` | ✗ | Listener for the navigation back button click event | `{ _ -> }` |

</div>

- Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `primaryColor` | ✓ | To set the main color of the screens | ✗ |
| `secondaryColor` | ✗ | To set the color of some UI components | `primaryColor` |

</div>

```kotlin
AroundMeUI.getInstance().let { instance ->
    instance.init(
      context = this,
      colors = AroundMeColors(
          primaryColor = "#0277BD",
          secondaryColor = "#FF4081"
      ),
      coverage = "YOUR_COVERAGE",
      token = "YOUR_TOKEN",
      env = AroundMeEnvironment.PROD,
      defaultLocation = LatLng(48.846874, 2.377125),
      configurationJsonFile = "config.json"
   )
   instance.attachActivity(this)
}
```

## 🚀  Launching

Around Me has a single entry point `MapFragment`. \
Assuming you have an `Activity` with a fragment container, refer to the following example to launch the entry screen fragment:

```kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, MapFragment.newInstance(), "TAG")
    addToBackStack("TAG")
    commit()
}
```

## 🛠  Configuration

### Lines

The `lines` is a JSON array of a line configuration.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `code` | String | ✓ | Line code identifier |
| `icon_res` | String | ✓ | String resource ID of the line icon |
| `commercial` | String | ✓ | Navitia commercial name of the line |

</div>

### Modes

The `modes` is a JSON array of a transport mode configuration.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `commercial` | String | ✓ | Navitia commercial name of the transport mode |
| `icon_res` | String | ✓ | String resource ID of the mode icon |

</div>

### Filters

The `filters` is a JSON array of categories. Each category has subcategories and each subcategory has types.

###### Category
{: .no_toc }

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `category_name_res` | String | ✓ | String resource ID of the category name |
| `subcategories` | Array | ✓ | List of subcategories |

</div>

###### Subcategory
{: .no_toc }

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
{: .no_toc }

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | String resource ID of the subcategory type name |
| `id` | String | ✓ | Navitia ID generally preceded by `physical_mode` or `poi_type` |

</div>

### Book button

The `book_button` is a JSON object that contains string resource IDs for the book button label in different UI components.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `bss_res` | String | ✓ | String resource ID of the booking label when the bike sharing service component is shown |
| `car_park_res` | String | ✓ | String resource ID of the booking label when the car park component is shown |
| `stop_point_res` | String | ✓ | String resource ID of the booking label when the stop point component is shown |

</div>

### Example
{: .no_toc }

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
      ],
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

```kotlin
// Configure lines
val linesConfiguration = listOf(
    AroundMeConfigurationLine(
        code = "a",
        iconRes = "ic_metro_a",
        commercial = "Metro"
    ),
    AroundMeConfigurationLine(
        code = "C2",
        iconRes = "ic_bus_c1",
        commercial = "Bus"
    ),
    AroundMeConfigurationLine(
        code = "a",
        iconRes = "ic_bus_c2",
        commercial = "Bus"
    )
)

// Configure modes
val modesConfiguration = listOf(
    AroundMeConfigurationMode(
        commercial = "Metro",
        iconRes = "ic_metro"
    ),
    AroundMeConfigurationMode(
        commercial = "Bus",
        iconRes = "ic_bus"
    ),
    AroundMeConfigurationMode(
        commercial = "Coach",
        iconRes = "ic_bus"
    )
)

// Configure filters
val filtersConfiguration = listOf(
    // Add stations category
    ConfigurationFilterCategory("stations", listOf(
        ConfigurationFilterSubcategory(
            nameRes = "metro",
            iconRes = "ic_section_mode_metro",
            selected = true,
            group = SubcategoryFilterGroup.TRANSPORT_MODE,
            types = listOf(ConfigurationFilterSubcategoryType("metro", "physical_mode:Metro"))
        ),
        ConfigurationFilterSubcategory(
            nameRes = "bus",
            iconRes = "ic_section_mode_bus",
            selected = true,
            group = SubcategoryFilterGroup.TRANSPORT_MODE,
            types = listOf(ConfigurationFilterSubcategoryType("bus", "physical_mode:Bus"))
        )
    )),
    // Add services category
    ConfigurationFilterCategory("mobility_services", listOf(
        ConfigurationFilterSubcategory(
            nameRes = "bss_station",
            iconRes = "ic_amenity_bicycle_rental",
            selected = true,
            group = SubcategoryFilterGroup.POI,
            types = listOf(ConfigurationFilterSubcategoryType("bss_station", "poi_type:amenity:bicycle_rental"))
        ),
        ConfigurationFilterSubcategory(
            nameRes = "parking",
            iconRes = "ic_amenity_parking",
            selected = true,
            group = SubcategoryFilterGroup.POI,
            types = listOf(ConfigurationFilterSubcategoryType("parking", "poi_type:amenity:parking"))
        )
    ))
)

// Configure book button label
val bookButtonConfiguration = ConfigurationBookButton("book_bss", "book_car_park", "book_stop_point")

// Setup configuration object
val configuration = Configuration(linesConfiguration, modesConfiguration, filtersConfiguration, bookButtonConfiguration)
```

Please note that calling `AroundMeUI.getInstance().resetUserPreferences()` will reset filters configuration and the content of the [filters](/navitia_sdk_docs/aroundme/android/screen#filters) screen.
