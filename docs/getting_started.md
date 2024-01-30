---
title: Getting started - Navitia SDK Docs
---

# Getting started

## 🧰 Requirements

- Get an access to <a href="https://navitia.io/inscription/" target="_blank">Navitia.io</a> API. A token will be provided later and will be used to configure all the modules.
- The SDKs are accessible privately, so you should request an access to our private <a href="https://kisiodigital.jfrog.io/" target="_blank">artifactory</a>. Those credentials will be used later to configure your machine to be able to download our dependencies.

<h4>Android</h4>

- Minimum Android SDK version: `23`

<h4>iOS</h4>

- [Cocoapods](https://cocoapods.org): All modules are available through Cocoapods.
- Minimum iOS deployment target: `14.0`

## 💻 Artifactory Setup

The access to the SDK requires valid credentials to our private artifactory. Please see [Requirements](#requirements) for more information. 

<h4>Android</h4>

Please add the following maven repository in the `build.gradle` of your project and replace `USERNAME` and `PASSWORD` with your credentials:

``` groovy
repositories {
    maven {
        credentials {
            username = USERNAME // (1)
            password = PASSWORD // (2)
        }
        url("https://kisiodigital.jfrog.io/kisiodigital/android-release")
    }
}
```

1.  Replace `USERNAME` with your artifactory username
2.  Replace `PASSWORD` with your artifactory password

<h4>iOS</h4>

Create a `.netrc` file in the `$HOME` directory of your machine.<br>
Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

``` ruby
machine kisiodigital.jfrog.io login USERNAME password PASSWORD # (1)
```

1.  Replace `USERNAME` and `PASSWORD` with your artifactory username and password

## 🛠 Modules Configuration

The Navitia SDKs should be configured before usage. Within a specific module, the customization can affect data or graphical components.<br>
Since your application can integrate one or more Navitia modules, you can use a single JSON file to configure all the modules at once.<br>
The following are the possible configuration parameters:

| Name | Required | Description | Type | Possible values | Target modules |
| --- | :-: | --- | :--: | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` | All |
| `timezone` | :material-check: | Timezone | `String` | `Europe/Paris` | All |
| `env` | :material-check: | Navitia environment | `String` | `PROD`, `CUSTOMER` | All |
| `colors` | :material-check: | Colors configuration | [`Colors`](#colors) | - | UI modules |
| `transport_categories` | :material-check: | List of supported transport modes | [`[Transport category]`](#transport-category) | - | UI modules |
| `poi_categories` | :material-close: | List of supported POIs | [`[Poi category]`](#poi-category) | - | Around Me, Bookmark |
| `features_configuration` | :material-close: | Enable/disable different module features | [`Features`](#features) | - | All |
| `fonts` | :material-close: | Override the fonts used in UI modules | [`Fonts`](#fonts) | - | UI modules |
| `lines_resources` | :material-close: | Resources ids for transport lines | [`[Line resource]`](#line-resource) | - | UI modules |
| `modes_resources` | :material-close: | Resources ids for transport modes | [`[Mode resource]`](#mode-resource) | - | UI modules |
| `providers_resources` | :material-close: | Resources ids for data providers | [`[Provider resource]`](#provider-resource) | - | UI modules |
| `networks_resources` | :material-close: | Resources ids for data networks | [`[Network resource]`](#network-resource) | - | UI modules |
| `icons_resources` | :material-close: | Resources ids for some specific icons | [`Icon resource`](#icon-resource) | - | UI modules |
| `titles_resources` | :material-close: | Resources ids for screen titles | [`Title resource`](#title-resource) | - | UI modules |

### Colors

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `account` | :material-check: | [`Account color`](#account-color) | Account |
| `aroundme` | :material-check: | [`Around Me color`](#around-me-color) | Around Me |
| `bookmark` | :material-check: | [`Bookmark color`](#bookmark-color) | Bookmark |
| `crowdsourcing` | :material-check: | [`Crowdsourcing color`](#crowdsourcing-color) | Crowdsourcing |
| `journey` | :material-check: | [`Journey color`](#journey-color) | Journey |
| `schedule` | :material-check: | [`Schedule color`](#schedule-color) | Schedule |
| `traffic` | :material-check: | [`Traffic color`](#traffic-color) | Traffic |

#### Account color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Around Me color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary` | :material-close: | To set the color of more UI components | `String` | `#efa59f` |
| `map` | :material-close: | To set colors of the markers on map | [`Map color`](#around-me-map-color) | - |

##### Around me map color
| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `poi` | :material-check: | To set the marker color of pois | `String` | `#9b59B6` |
| `transport` | :material-check: | To set the marker color of stations | `String` | `#2980B9` |

#### Bookmark color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Crowdsourcing color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Journey color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary` | :material-close: | To set the color of more UI components | `String` | `#efa59f` |
| `origin` | :material-close: | To set colors of the journey origin | [`Journey origin color`](#journey-origin-color) | - |
| `destination` | :material-close: | To set colors of the journey destination | [`Journey destination color`](#journey-destination-color) | - |
| `bike` | :material-close: | To set colors of the specific bike journey | [`Journey bike color`](#journey-bike-color) | - |
| `nav_bar_background` | :material-close: | To set the color of the navigation bar. iOS only.  | `String` | `#efa59f` |

##### Journey origin color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `icon` | :material-check: | To set the icon color of the itinerary origin | `String` | `#88819f` |

##### Journey destination color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the color of the arrival block | `String` | `#8faa96` |
| `icon` | :material-close: | To set the icon color of the itinerary destination | `String` | `#88819f` |

##### Journey bike color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the specific bike journey | `String` | `#8faa96` |
| `non_cyclable` | :material-close: | To set the color of the non cyclable part for a specific bike journey | `String` | `#88819f` |

#### Schedule color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Traffic color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

### Transport category

| Name | Required | Description | Type | Example | Target modules |
| --- |:---:| --- | :---: | :---: | :---: |
| `modules` | :material-check: | To set the target modules | `[String]` | `["aroundme","journey"]` | `ALL` |
| `name_res` | :material-check: | To set the localized resource id | `String` | `transport_name_res` | `ALL` |
| `icon_res` | :material-check: | To set the icon resource id | `String` | `ic_metro` | `ALL` |
| `selected` | :material-close: | Whether the transport mode is selected by default or not | `Boolean` | `true` | `ALL` |
| `modes` | :material-close: | List of supported transport modes | [`Transport Mode`](#transport-mode) | - | `ALL` |
| `networks` | :material-close: | List of supported networks | `[String]` | `["network:BIL:27"]` | `Schedule` |
| `first_section_modes` | :material-close: | List of first section modes | `[String]` | `["bike", "car"]` | `Journey` |
| `last_section_modes` | :material-close: | List of last section modes | `[String]` | `["ridesharing", "bss"]` | `Journey` |
| `direct_path_modes` | :material-close: | List of direct path modes | `[String]` | `["taxi", "car_no_park"]` | `Journey` |
| `add_poi_infos` | :material-close: | List of requested extra POI data | `[String]` | `["bss_stands", "car_park"]` | `Journey` |

#### Transport mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `physical` | :material-check: | To set the transport physical mode | [`Transport Physical Mode`](#transport-physical-mode) | `["aroundme","journey"]` |
| `commercial` | :material-check: | To set the transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

##### Transport physical mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `id` | :material-check: | Navitia physical mode id | `String` | `"physical_mode:Bus"` |
| `name_res` | :material-check: | Localized name resource id | `String` | `"transport_bus"` |

##### Transport commercial mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `id` | :material-check: | Navitia commercial mode id | `String` | `"commercial_mode:Bus"` |
| `name` | :material-check: | Navitia commercial mode name | `String` | `"Bus"` |

### POI category

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized POI category name id | `String` | `"stations"` |
| `subcategories` | :material-check: | List of POI subcategories | [`[POI subcategory]`](#poi-subcategory) | - |

#### POI subcategory

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized POI subcategory name id | `String` | `"bike_stations"` |
| `icon_res` | :material-check: | POI subcategory icon id | `String` | `"ic_bike_stations"` |
| `selected` | :material-close: | Whether the subcategory is selected by default or not | `Boolean` | `true` |
| `group` | :material-check: | Subcategory POI group | `String` | `STANDARD`, `TRANSPORT_MODE`, `FREE_FLOATING` |
| `types` | :material-check: | Subcategory POI types | [`[POI Subcategory Type]`](#poi-subcategory-type) | - |
| `booking` | :material-close: | POI booking resources | [POI booking resources](#poi-booking-resources) | - |

##### POI subcategory type

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized POI subcategory type name id | `String` | `"scooter"` |
| `poi_type_id` | :material-check: | Navitia POI subcategory type id | `String` | `"poi_type:amenity:bicycle_rental"` |

##### POI booking resources

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `title_res` | :material-check: | Localized POI booking button title id | `String` | `"book_a_bike"` |

### Fonts

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `account` | :material-close: | [`Account fonts`](#account-fonts) | Account |
| `aroundme` | :material-close: | [`Around Me fonts`](#around-me-fonts) | Around Me |
| `bookmark` | :material-close: | [`Bookmark fonts`](#bookmark-fonts) | Bookmark |
| `journey` | :material-close: | [`Journey fonts`](#journey-fonts) | Journey |
| `schedule` | :material-close: | [`Schedule fonts`](#schedule-fonts) | Schedule |
| `traffic` | :material-close: | [`Traffic fonts`](#traffic-fonts) | Traffic |

### Features

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `account` | :material-close: | [`Account features`](#account-features) | Account |
| `aroundme` | :material-close: | [`Around Me features`](#around-me-features) | Around Me |
| `bookmark` | :material-close: | [`Bookmark features`](#bookmark-features) | Bookmark |
| `journey` | :material-close: | [`Journey features`](#journey-features) | Journey |
| `schedule` | :material-close: | [`Schedule features`](#schedule-features) | Schedule |
| `traffic` | :material-close: | [`Traffic features`](#traffic-features) | Traffic |

#### Account features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `my_account_menu_items` | :material-check: | To set the My Account menu items | [`My account menu item`](#my-account-menu-item) |
| `signup_form_fields` | :material-check: | To set Sign up screen form fields | [`Account form field`](#account-form-field) |
| `edit_form_fields` | :material-check: | To set Edit screen form fields | [`Account form field`](#account-form-field) |

##### My account menu item

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized menu item title id | `String` | `"bookmarks"` |
| `icon_res` | :material-check: | Menu item icon resource id | `String` | `"ic_bookmarks"` |

##### Account form field

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `hint_res` | :material-check: | Localized field hint id | `String` | `"name_hint"` |
| `type` | :material-check: | Field type | `String` | `"TEXT" OR "DATE" OR "EMAIL" OR "PASSWORD" OR "NUMBER" OR "PHONE"` |
| `min_date` | :material-close: | Set the min datepicker date in this format dd/MM/yyyy | `String` | `"01/01/2022"` |
| `max_date` | :material-close: | Set the max datepicker date in this format dd/MM/yyyy | `String` | `"01/01/2050"` |
| `max_length` | :material-close: | Set the max allowed number of characters | `Int` | `0` |
| `required` | :material-close: | Whether the field is mandatory | `Boolean` | `false` |

⚠️ Please note that `PASSWORD` type is only available for signup screen!

#### Around Me features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `bookmark_mode` | :material-close: | Enable/disable the bookmarks feature | `Boolean` |
| `default_location` | :material-close: | The default location on first launch | [`Default location`](#default-location) |
| `go_from_go_to` | :material-close: | Show/hide the go from/go to buttons | `Boolean` |
| `journey_mode` | :material-close: | Enable/disable the journey search mode | `Boolean` |
| `max_history` | :material-close: | Define the max history items | `Int` |
| `min_zoom_level` | :material-close: | Define the min zoom level of map. Android only | `Int` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) |
| `stop_point_search` | :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` |
| `traffic_mode` | :material-close: | Show/hide the traffic button | `Boolean` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on map | [`Vehicle positions`](#vehicle-positions) |

##### Default location

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `lat` | :material-check: | The latitude of the default location | `String` | `"48.846790"` |
| `lon` | :material-check: | The longitude of the default location | `String` | `"2.377090"` |

#### Next departures

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `frequency`| :material-check: | frequency of the next departures request in seconds | `Int` | `30` |

##### Vehicle positions

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `frequency` | :material-check: | frequency of the vehicle positions request in seconds | `String` | 30 |

#### Bookmark features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `go_from_go_to` | :material-close: | Show/hide the go from/go to buttons | `Boolean` | `true` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) | - |
| `tabs` | :material-close: | Enable/disable tabs | [`Bookmark tabs`](#bookmark-tabs) | - |

##### Bookmark tabs

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `transports` | :material-check: | Enable/disable transport tab | `Boolean` | `true` |
| `journeys` | :material-check: | Enable/disable journeys tab  | `Boolean` | `true` |
| `addresses` | :material-check: | Enable/disable addresses tab  | `Boolean` | `true` |

#### Journey features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `bookmark_mode` | :material-close: | Enable/disable the bookmark feature | `Boolean` | - |
| `calories` | :material-close: | Show/hide the itinerary calories summary | `Boolean` | `false` |
| `carbon` | :material-close: | Show/hide the itinerary carbon summary | `Boolean` | `true` |
| `car_parking_highlight` | :material-close: | Show/hide the car parking in the journey solution | `Boolean` | `true` |
| `disruption_contributors` | :material-close: | Define the list of disruption contributors id | `[String]` | `["shortterm.tr_idfm"]` |
| `external_navigation` | :material-close: | Enable/disable the navigation using external applications | `Boolean` | `true` |
| `max_favorite_addresses` | :material-close: | Define the max favorite addresses | `Int` | `10` |
| `max_favorite_pois` | :material-close: | Define the max favorite POIs | `Int` | `10` |
| `max_history` | :material-close: | Define the max history items | `Int` | `10` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) | - |
| `price` | :material-close: | Show/hide the itinerary price | `Boolean` | `true` |
| `ridesharing_price` | :material-close: | Show/hide the itinerary ridesharing price | `Boolean` | `true` |
| `search_only` | :material-close: | Enable/disable a direct search without input from user | `Boolean` | `false` |
| `step_by_step_guidance` | :material-close: | Enable/disable the step by step guidance | `Boolean` |
| `stop_point_search_mode` | :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` | `false` |
| `traffic` | :material-close: | Define Traffic module options | [`Traffic options`](#traffic-options-journey) | - |
| `transport_networks` | :material-close: | Show/hide the public transport network | `Boolean` | `false` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on roadmap | [`Vehicle positions`](#vehicle-positions) | - |

##### Traffic options (Journey)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `alert_subscription` | :material-close: | Enable Traffic alert subscriptions | `Boolean` | `false` |

#### Schedule features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `bookmark_mode` | :material-close: | Enable/disable the bookmarks feature | `Boolean` |
| `max_history` | :material-close: | Define the max history items | `Int` |
| `networks_filter` | :material-close: | Show/hide the networks selector | `Boolean` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) |
| `transport_networks` | :material-close: | Enable/disable grouping lines by network | `Boolean` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on map | [`Vehicle positions`](#vehicle-positions) |

#### Traffic features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `alert_subscription` | :material-close: | Alert subscription environment configuration | [`Alert subscription`](#alert-subscription) | - |
| `disruption_contributors` | :material-close: | Define the list of disruption contributors id | `[String]` | `["shortterm.tr_idfm"]` |
| `networks_first` | :material-close: | Show networks before line disruptions | `Boolean` |
| `transport_networks` | :material-close: | Enable/disable showing network on lines | `Boolean` | - |

##### Alert subscription

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `env` | :material-check: | Kronos environment | `String` | `PROD` |
| `timezone` | :material-check: | Subscriptions timezone | `String` | `Europe/Paris` |

### Fonts

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `account` | :material-close: | [`Custom font`](#custom-font) | Account |
| `aroundme` | :material-close: | [`Custom font`](#custom-font) | Around Me |
| `bookmark` | :material-close: | [`Custom font`](#custom-font) | Bookmark |
| `journey` | :material-close: | [`Custom font`](#custom-font) | Journey |
| `schedule` | :material-close: | [`Custom font`](#custom-font) | Schedule |
| `traffic` | :material-close: | [`Custom font`](#custom-font) | Traffic |

#### Custom font

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `numeric` | :material-close: | Custom numeric font | [`Font category`](#font-category) |
| `alphanumeric` | :material-close: | Custom alphanumeric font | [`Font category`](#font-category) |

##### Font category

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `regular` | :material-close: | Custom numeric font for regular typeface | [`Font Typeface`](#font-typeface) |
| `italic` | :material-close: | Custom numeric font for italic typeface | [`Font Typeface`](#font-typeface) |
| `semi_bold` | :material-close: | Custom numeric font for semi bold typeface | [`Font Typeface`](#font-typeface) |
| `semi_bold_italic` | :material-close: | Custom numeric font for semi bold italic typeface | [`Font Typeface`](#font-typeface) |
| `bold` | :material-close: | Custom numeric font for bold typeface | [`Font Typeface`](#font-typeface) |
| `bold_italic` | :material-close: | Custom numeric font for bold italic typeface | [`Font Typeface`](#font-typeface) |
| `light` | :material-close: | Custom numeric font for light typeface | [`Font Typeface`](#font-typeface) |
| `light_italic` | :material-close: | Custom numeric font for light italic typeface | [`Font Typeface`](#font-typeface) |

##### Font Typeface

| Name | Required | Description | Type | Platform | Example |
| --- |:---:| --- | :---: | :---: | :---: |
| `font_res` | :material-check: | The font resource name | `String` | Android | `source_sans_pro_semi_bold` |
| `ttf_file` | :material-check: | The TTF file name | `String` | iOS | `"SourceSansPro"` |
| `font_name` | :material-check: | The font name | `String` | iOS | `"SourceSansPro-Bold"` |

### Line resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `code` | :material-check: | Navitia line code | `String` | `1` |
| `icon_res` | :material-check: | Line icon resource id | `String` | `ic_metro_1` |
| `commercial` | :material-check: | Transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

### Mode resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `icon_res` | :material-check: | Transport mode icon resource id | `String` | `ic_bus` |
| `commercial` | :material-check: | Transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

### Provider resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `type_id` | :material-check: | Navitia provider type id | `String` | `SCOOTER` |
| `provider_id` | :material-check: | Navitia provider id | `String` | `ridesharing_provider` |
| `icon_res` | :material-check: | Provider icon resource id | `String` | `ic_lime` |

### Network resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `network_id` | :material-check: | Navitia network id | `String` | `network:BIL:27` |
| `name_res` | :material-check: | Localized network name resource id | `String` | `sncf` |
| `icon_res` | :material-check: | Network icon resource IidD | `String` | `ic_sncf` |

### Icon resource

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `journey` | :material-close: | [`Journey icon resource`](#journey-icon-resource) | Journey |

### Journey icon resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `departure` | :material-close: | Departure icon resource id | `String` | `ic_departure` |
| `arrival` | :material-close: | Arrival icon resource id  | `String` | `ic_departure` |
| `indoor_parking` | :material-close: | Indoor parking icon resource id  | `String` | `ic_indoor_parking` |
| `outdoor_parking` | :material-close: | Outdoor parking icon resource id  | `String` | `ic_outdoor_parking` |

### Title resource

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `aroundme` | :material-close: | [`Around Me title resource`](#around-me-title-resource) | Around Me |
| `journey` | :material-close: | [`Journey title resource`](#journey-title-resource) | Journey |

#### Around Me title resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `filters` | :material-close: | Localized filters screen title resource id | `String` | `filters_screen_title` |

#### Journey title resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `journeys` | :material-close: | Localized journeys screen title resource id | `String` | `journeys_screen_title` |
| `roadmap` | :material-close: | Localized roadmap screen title resource id | `String` | `roadmap_screen_title` |
| `ridesharing` | :material-close: | Localized ridesharing screen title resource id | `String` | `ridesharing_screen_title` |

### Global configuration JSON structure

You can refer to the JSON below to generate your own configuration.<br>
Please note that this is the complete version of the configuration, remove unused objects and adapt the values as needed.

``` javascript
{
  "coverage": "",
  "timezone": "",
  "env": "PROD",
  "osm_region": {
    "id": "",
    "name_res": ""
  },
  "colors": {
    "account": {
      "primary": "",
      "secondary": ""
    },
    "aroundme": {
      "primary": "",
      "secondary": "",
      "tertiary": "",
      "map": {
        "poi": "",
        "transport": ""
      }
    },
    "bookmark": {
      "primary": "",
      "secondary": ""
    },
    "crowdsourcing": {
      "primary": "",
      "secondary": ""
    },
    "journey": {
      "primary": "",
      "secondary": "",
      "tertiary": "",
      "destination": {
        "primary": "",
        "icon": ""
      },
      "origin": {
        "icon": ""
      },
      "bike": {
        "primary": "",
        "non_cyclable": ""
      },
      "nav_bar_background": ""
    },
    "schedule": {
      "primary": "",
      "secondary": ""
    },
    "traffic": {
      "primary": "",
      "secondary": ""
    },
    "disruptions": {
      "information": "",
      "non_blocking": "",
      "blocking": ""
    }
  },
  "fonts": {
    "aroundme": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      }
    },
    "bookmark": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      }
    },
    "crowdsourcing": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      }
    },
    "journey": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
    },
    "schedule": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      }
    },
    "traffic": {
      "alphanumeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      },
      "numeric": {
        "regular": {
          "file": "",
          "font_name": ""
        },
        "italic": {
          "file": "",
          "font_name": ""
        },
        "bold": {
          "file": "",
          "font_name": ""
        },
        "bold_italic": {
          "file": "",
          "font_name": ""
        },
        "semi_bold": {
          "file": "",
          "font_name": ""
        },
        "semi_bold_italic": {
          "file": "",
          "font_name": ""
        },
        "light": {
          "file": "",
          "font_name": ""
        },
        "light_italic": {
          "file": "",
          "font_name": ""
        }
      }
    }
  },
  "lines_resources": [
    {
      "code": "",
      "icon_res": "",
      "commercial": {
        "id": "",
        "name": ""
      }
    }
  ],
  "modes_resources": [
    {
      "icon_res": "",
      "commercial": {
        "id": "",
        "name": ""
      }
    }
  ],
  "transport_categories": [
    {
      "modules": [
        "aroundme",
        "crowdsourcing",
        "journey",
        "schedule",
        "traffic"
      ],
      "icon_res": "",
      "name_res": "",
      "selected": true,
      "modes": [
        {
          "physical": {
            "id": "",
            "name_res": ""
          },
          "commercial": {
            "id": "",
            "name": ""
          }
        }
      ],
      "networks": [
        ""
      ],
      "direct_path_modes": [
        "car",
        "car_no_park",
        "bss",
        "bike",
        "rideharing",
        "taxi",
        "walking"
      ],
      "first_section_modes": [
        "car",
        "car_no_park",
        "bss",
        "bike",
        "rideharing",
        "taxi",
        "walking"
      ],
      "last_section_modes": [
        "car",
        "car_no_park",
        "bss",
        "bike",
        "rideharing",
        "taxi",
        "walking"
      ],
      "add_poi_infos": [
        "bss_stands",
        "car_park"
      ]
    }
  ],
  "poi_categories": [
    {
      "name_res": "",
      "subcategories": [
        {
          "icon_res": "",
          "name_res": "",
          "zoom_level": 16.5,
          "selected": true,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "",
              "poi_type_id": ""
            }
          ],
          "booking": {
            "title_res": ""
          }
        }
      ]
    }
  ],
  "providers_resources": [
    {
      "type_id": "",
      "provider_id": "",
      "icon_res": ""
    }
  ],
  "networks_resources": [
    {
      "network_id": "",
      "icon_res": "",
      "name_res": ""
    }
  ],
  "icons_resources": {
    "aroundme": {
      "traffic_button": ""
    },
    "journey": {
      "departure": "ic_departure",
      "arrival": "ic_arrival",
      "indoor_parking": "ic_custom_indoor_parking",
      "outdoor_parking": "ic_custom_outdoor_parking"
    }
  },
  "titles_resources": {
    "journey": {
      "journeys": "journeys_screen_title",
      "roadmap": "roadmap_screen_title",
      "ridesharing": "ridesharing_screen_title"
    },
    "aroundme": {
      "filters": "filters_screen_title"
    }
  },
  "features_configuration": {
    "account": {
      "my_account_menu_items": [
        {
          "icon_res": "",
          "name_res": ""
        }
      ],
      "sign_up_form_fields": [
        {
          "hint_res": "",
          "type": "TEXT",
          "min_date": "dd/MM/yyyy",
          "max_date": "dd/MM/yyyy",
          "max_length": 0,
          "required": true
        }
      ],
      "edit_form_fields": [
        {
          "hint_res": "",
          "type": "DATE",
          "min_date": "dd/MM/yyyy",
          "max_date": "dd/MM/yyyy",
          "max_length": 0,
          "required": true
        }
      ]
    },
    "aroundme": {
      "booking": {
        "title_res": ""
      },
      "bookmark_mode": true,
      "crowdsourcing_mode": true,
      "default_location": {
        "lat": "48.846790",
        "lon": "2.377090"
      },
      "go_from_go_to": true,
      "journey_mode": true,
      "max_history": 10,
      "min_zoom_level": 15,
      "next_departures": {
        "frequency": 30
      },
      "stop_point_search": true,
      "traffic_mode": true,
      "vehicle_positions": {
        "frequency": 30
      }
    },
    "bookmark": {
      "go_from_go_to": true,
      "next_departures": {
        "frequency": 30
      },
      "tabs": {
        "transports": true,
        "journeys": true,
        "addresses": true
      }
    },
    "journey": {
      "bookmark_mode": true,
      "calories": true,
      "carbon": true,
      "car_parking_highlight": true,
      "disruption_contributors": [
        ""
      ],
      "external_navigation": true,
      "max_favorite_addresses": 10,
      "max_favorite_pois": 10,
      "max_history": 10,
      "next_departures": {
        "frequency": 30
      },
      "price": true,
      "ridesharing_price": true,
      "search_only": false,
      "step_by_step_guidance": true,
      "stop_point_search_mode": true,
      "traffic": {
        "alert_subscription": true
      },
      "transport_networks": true,
      "vehicle_positions": {
        "frequency": 30
      }
    },
    "schedule": {
      "bookmark_mode": true,
      "max_history": 10,
      "networks_filter": true,
      "next_departures": {
        "frequency": 30
      },
      "transport_networks": true,
      "vehicle_positions": {
        "frequency": 30
      }
    },
    "traffic": {
      "alert_subscription": {
        "env": "",
        "timezone": ""
      },
      "disruption_contributors": [
        ""
      ],
      "networks_filter": true,
      "severity": [
        {
          "icon_res": "",
          "name_res": "",
          "color": "",
          "effects": [
            ""
          ],
          "selected": true
        }
      ],
      "transport_networks": true
    }
  }
}
```

## 📈 Modules events tracking

The events triggered within Navitia UI modules can be traced and forwarded to the application module. Each generated event is served with other information allowing to identify the target object on the module screen.<br>
You can refer to the table below for possible generated events.

| Event name | Possible object types | Description |
| --- | --- | --- |
| `drag` | `map`, `bottomSheet`, `chart`, `map` | The user performs a drag action |
| `edit` | `field` | The user has changed the input value of an object |
| `pull` | `list` | The user has pulled the object |
| `tap` | `button`, `item`, `switch`, `tab` | The user performs a tap action |
| `scroll` | `bottomSheet`, `list` | The user started a scroll on an object |
| `show` | - | A screen is displayed |
| `swipe` | `bottomSheet` | The user performs a swipe action |
| `zoom` | `map` | The user performs whether a pinch, a double tap action to zoom on an object |

You can find in the following table the list of UI modules that support the event tracking features

<h4>Android</h4>

| Module name | Available | Implementation |
| --- | ---- | :---: |
| Around me | :material-close: | [Around me events tracking](../around_me/android/#events-tracking) |
| Bookmark | :material-close: | [Bookmark events tracking](../bookmark/android/#events-tracking) |
| Journey | :material-check: | [Journey events tracking](../journey/android/#events-tracking) |
| Schedule | :material-close: | [Schedule events tracking](../schedule/android/#events-tracking) |
| Traffic | :material-close: | [Traffic events tracking](../traffic/android/#events-tracking) |

<h4>iOS</h4>

| Module name | Available | Implementation |
| --- | ---- | :---: |
| Around me | :material-close: | [Around me events tracking](../around_me/ios/#events-tracking) |
| Bookmark | :material-close: | [Bookmark events tracking](../bookmark/ios/#events-tracking) |
| Journey | :material-check: | [Journey events tracking](../journey/ios/#events-tracking) |
| Schedule | :material-close: | [Schedule events tracking](../schedule/ios/#events-tracking) |
| Traffic | :material-close: | [Traffic events tracking](../traffic/ios/#events-tracking) |
