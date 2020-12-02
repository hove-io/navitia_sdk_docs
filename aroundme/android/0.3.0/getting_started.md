---
layout: default
title: Getting started
parent: Around Me Android
grand_parent: Around Me
nav_order: 2
permalink: /aroundme/android/getting-started
---

# Getting Started

---

## 💻 Setup

Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials

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
 
Add the following dependency in the `build.gradle` file of your application

```ruby
dependencies {
    ...
    implementation("com.kisio.navitia.sdk.ui:aroundme:0.2.2")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well. Replace `YOUR_API_KEY` with your key

```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching Journey must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`

```xml
<activity
    ...
    android:configChanges="orientation|screenSize"
    .../>
```

## 👨‍💻 Implementation

This module is set up by calling `AroundMeUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. You need to call the `init()` method at the end.\
The following are arguments of the `init()` method:

<div markdown="1">

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| `activity` | `WeakReference<AppCompatActivity>` | ✓ | Weak reference of the activity launching the module | ✗ |
| `colors` | `AroundMeColors` | ✓ | Module colors configuration | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `configuration` | `Configuration` | ✗ (if `configurationJsonFile` is set) | Data configuration of the module | `null` |
| `configurationJsonFile` | `String` | ✗ (if `Configuration` is set) | Json file name in `assets` folder | `null` |
| `defaultLocation` | `LatLng` | ✗ | The default map center location | `DEFAULT_MALOT_LAT_LNG` |
| `navigationListener` | `NavigationListener` | ✗ | Listener the module can rely on for navigation events within the app | `null` |

</div>

```kotlin
AroundMeUI.getInstance()
   .init(
       activity = WeakReference(this),
       colors = AroundMeColors(
           backgroundColor = "#0277BD",
           primaryColor = "#FF4081"
       ),
       coverage = "fr-idf",
       token = "0de19ce5-e0eb-4524-a074-bda3c6894c19",
       configuration = Configuration(filtersConfiguration, bookButtonConfiguration), // Not required if configurationJsonFile is set
       configurationJsonFile = "jsonFile" // Not required if configuration object is set
   )
```

## 🛠 Configuration

### Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `backgroundColor` | ✓ | To set the background color | ✗ |
| `primaryColor` | ✗ | To set the color of some UI components | `backgroundColor` |

</div>

### Data

The module has to be configured to work properly. The filters and some UI components require a configuration, otherwise, you won't be able to launch the SDK. There are two main sections to configure: `filters` and `book_button`.

The `filters` sets up the list of the categories/subcategories/types to be displayed in the filters page.\
The `book_button` sets up the label to be displayed on the booking button when different UI components are shown on the screen.

#### Filters

The `filters` is a JSON array of categories. Each category has subcategories and each subcategory has types.

###### Category
<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `category_name_res` | String | ✓ | The string resource ID of the category name |
| `subcategories` | Array | ✓ | The list of subcategories |

</div>

###### Subcategory
<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | The string resource ID of the subcategory name |
| `icon_res` | String | ✓ | The icon resource ID to be displayed within the map marker |
| `selected` | Boolean | ✓ | Whether this subcategory is selected by default or not |
| `group` | Integer | ✓ | `0`: Transport mode / `1`: POI |
| `types` | Array | ✓ | The list of the subcategory types |

</div>

###### Subcategory type
<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | The string resource ID of the subcategory type name |
| `id` | String | ✓ | The Navitia ID generally preceded by `physical_mode` or `poi_type` |

</div>

#### Book Button

The `book_button` is a JSON object that contains String resource IDs for the book button label in different UI components.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `bss_res` | String | ✓ | The string resource ID of the booking label when the BSS component is shown |
| `car_park_res` | String | ✓ | The string resource ID of the booking label when the car park component is shown |
| `stop_point_res` | String | ✓ | The string resource ID of the booking label when the stop point component is shown |

</div>

### How to configure Data?

Easy peasy, follow one of the steps below 👇😉.\
Please note that calling `resetUserPreferences()` will reset filters configuration and the content of the [filters](/navitia_sdk_docs/aroundme/android/screen#filters) screen.

#### Using JSON file

The JSON file should be added to the `assets` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

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

#### Using Configuration object

```kotlin
// Configure filters
val filtersConfiguration = mutableListOf<ConfigurationFilterCategory>()

// Add stations category
val stationsSubcategories = listOf(
    ConfigurationFilterSubcategory("metro",
        "ic_section_mode_metro",
        true,
        SubcategoryFilterGroup.TRANSPORT_MODE,
        listOf(ConfigurationFilterSubcategoryType("metro", "physical_mode:Metro"))
    ),
    ConfigurationFilterSubcategory("bus",
        "ic_section_mode_bus",
        true,
        SubcategoryFilterGroup.TRANSPORT_MODE,
        listOf(ConfigurationFilterSubcategoryType("bus", "physical_mode:Bus"))
    )
)
filtersConfiguration.add(ConfigurationFilterCategory("stations", stationsSubcategories))

// Add services category
val servicesSubcategories = listOf(
    ConfigurationFilterSubcategory("bss_station",
        "ic_amenity_bicycle_rental",
        true,
        SubcategoryFilterGroup.POI,
        listOf(ConfigurationFilterSubcategoryType("bss_station", "poi_type:amenity:bicycle_rental"))
    ),
    ConfigurationFilterSubcategory("parking",
        "ic_amenity_parking",
        true,
        SubcategoryFilterGroup.POI,
        listOf(ConfigurationFilterSubcategoryType("parking", "poi_type:amenity:parking"))
    )
)
filtersConfiguration.add(ConfigurationFilterCategory("mobility_services", servicesSubcategories))

// Configure book button label
val bookButtonConfiguration = ConfigurationBookButton("book_bss", "book_car_park", "book_stop_point")

// Setup configuration object
val configuration = Configuration(filtersConfiguration, bookButtonConfiguration)
```
