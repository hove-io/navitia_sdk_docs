# Getting started

## 🧰 Requirements

- Get an access to <a href="https://navitia.io/inscription/" target="_blank">Navitia.io</a> API. A token will be provided later and will be used to configure all the modules.
- The SDKs are accessible privately, so you should request an access to our private <a href="https://kisiodigital.jfrog.io/" target="_blank">artifactory</a>. Those credentials will be used later to configure your machine to be able to download our dependencies.

<h4>Android</h4>

- Minimum Android SDK target: `21`

<h4>iOS</h4>

- [Cocoapods](https://cocoapods.org): All modules are available through Cocoapods.
- Minimum iOS deployment target: `13.0`

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
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf`| All |
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
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Around Me color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary`| :material-close: | To set the color of more UI components | `String` | `#efa59f` |

#### Bookmark color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Crowdsourcing color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Journey color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary`| :material-close: | To set the color of more UI components | `String` | `#efa59f` |
| `origin`| :material-close: | To set colors of the journey origin | [`Journey origin color`](#journey-origin-color) | - |
| `destination`| :material-close: | To set colors of the journey destination | [`Journey destination color`](#journey-destination-color) | - |
| `bike`| :material-close: | To set colors of the specific bike journey | [`Journey bike color`](#journey-bike-color) | - |
| `nav_bar_background` | :material-close: | To set the color of the navigation bar.iOS only.  | `String` | `#efa59f` |

##### Journey origin color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `icon`| :material-check: | To set the icon color of the itinerary origin | `String` | `#88819f` |

##### Journey destination color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the color of the arrival block | `String` | `#8faa96` |
| `icon`| :material-close: | To set the icon color of the itinerary destination | `String` | `#88819f` |

##### Journey bike color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the specific bike journey | `String` | `#8faa96` |
| `non_cyclable`| :material-close: | To set the color of the non cyclable part for a specific bike journey | `String` | `#88819f` |

#### Schedule color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |

#### Traffic color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary`| :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary`| :material-check: | To set the color of some UI components | `String` | `#8faa96` |

### Transport category

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `modules`| :material-check: | To set the target modules | `[String]` | `["aroundme","journey"]` |
| `name_res`| :material-check: | To set the localized resource id | `String` | `transport_name_res` |
| `icon_res`| :material-check: | To set the icon resource id | `String` | `ic_metro` |
| `selected`| :material-close: | Whether the transport mode is selected by default or not | `Boolean` | `true` |
| `modes`| :material-close: | List of supported transport modes | [`Transport Mode`](#transport-mode) | - |
| `networks`| :material-close: | List of supported networks | `[String]` | `["network:BIL:27"]` |
| `first_section_modes`| :material-close: | List of first section modes | `[String]` | `["bike", "car"]` |
| `last_section_modes`| :material-close: | List of last section modes | `[String]` | `["ridesharing", "bss"]` |
| `direct_path_modes`| :material-close: | List of direct path modes | `[String]` | `["taxi", "car_no_park"]` |
| `add_poi_infos`| :material-close: | List of requested extra POI data | `[String]` | `["bss_stands", "car_park"]` |

#### Transport mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `physical`| :material-check: | To set the transport physical mode | [`Transport Physical Mode`](#transport-physical-mode) | `["aroundme","journey"]` |
| `commercial`| :material-check: | To set the transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

##### Transport physical mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `id`| :material-check: | Navitia physical mode id | `String` | `"physical_mode:Bus"` |
| `name_res`| :material-check: | Localized name resource id | `String` | `"transport_bus"` |

##### Transport commercial mode

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `id`| :material-check: | Navitia commercial mode id | `String` | `"commercial_mode:Bus"` |
| `name`| :material-check: | Navitia commercial mode name | `String` | `"Bus"` |

### POI category

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res`| :material-check: | Localized POI category name id | `String` | `"stations"` |
| `subcategories`| :material-check: | List of POI subcategories | [`[POI subcategory]`](#poi-subcategory) | - |

#### POI subcategory

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res`| :material-check: | Localized POI subcategory name id | `String` | `"bike_stations"` |
| `icon_res`| :material-check: | POI subcategory icon id | `String` | `"ic_bike_stations"` |
| `selected`| :material-close: | Whether the subcategory is selected by default or not | `Boolean` | `true` |
| `group`| :material-check: | Subcategory POI group | `String` | `STANDARD`, `TRANSPORT_MODE`, `FREE_FLOATING` |
| `types`| :material-check: | Subcategory POI types | [`[POI Subcategory Type]`](#poi-subcategory-type) | - |
| `booking`| :material-close: | POI booking resources | [POI booking resources](#poi-booking-resources) | - |

##### POI subcategory type

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res`| :material-check: | Localized POI subcategory type name id | `String` | `"scooter"` |
| `poi_type_id`| :material-check: | Navitia POI subcategory type id | `String` | `"poi_type:amenity:bicycle_rental"` |

##### POI booking resources

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `title_res`| :material-check: | Localized POI booking button title id | `String` | `"book_a_bike"` |

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
| `my_account_menu_items`| :material-check: | To set the My Account menu items | [`My account menu item`](#my-account-menu-item) |
| `signup_form_fields`| :material-check: | To set Sign up screen form fields | [`Account form field`](#account-form-field) |
| `edit_form_fields`| :material-check: | To set Edit screen form fields | [`Account form field`](#account-form-field) |

##### My account menu item

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res`| :material-check: | Localized menu item title id | `String` | `"bookmarks"` |
| `icon_res`| :material-check: | Menu item icon resource id | `String` | `"ic_bookmarks"` |

##### Account form field

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `hint_res`| :material-check: | Localized field hint id | `String` | `"name_hint"` |
| `type`| :material-check: | Field type | `String` | `"TEXT" OR "DATE" OR "EMAIL" OR "PASSWORD" OR "NUMBER" OR "PHONE"` |
| `min_date`| :material-close: | Set the min datepicker date in this format dd/MM/yyyy | `String` | `"01/01/2022"` |
| `max_date`| :material-close: | Set the max datepicker date in this format dd/MM/yyyy | `String` | `"01/01/2050"` |
| `max_length`| :material-close: | Set the max allowed number of characters | `Int` | `0` |
| `required`| :material-close: | Whether the field is mandatory | `Boolean` | `false` |

⚠️ Please note that `PASSWORD` type is only available for signup screen!

#### Around Me features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `journey_mode`| :material-close: | Enable/disable the journey search mode | `Boolean` |
| `bookmark_mode`| :material-close: | Enable/disable the bookmarks feature | `Boolean` |
| `traffic_mode`| :material-close: | Show/hide the traffic button | `Boolean` |
| `stop_point_search`| :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` | `false` |
| `go_from_go_to`| :material-close: | Show/hide the go from/go to buttons | `Boolean` |
| `default_location`| :material-close: | The default location on first launch | [`Around Me location`](#around-me-location) |
| `max_history`| :material-close: | Define the max history items | `Int` |

##### Around Me location

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `lat`| :material-check: | The latitude of the default location | `String` | `"48.846790"` |
| `lon`| :material-check: | The longitude of the default location | `String` | `"2.377090"` |

#### Bookmark features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `go_from_go_to`| :material-close: | Show/hide the go from/go to buttons | `Boolean` |

#### Journey features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `bookmark_mode`| :material-close: | Enable/disable the bookmarks feature | `Boolean` |
| `buy_tickets`| :material-close: | Enable a buy button in roadmap | [Buy ticket button](#buy-ticket-button) |
| `carbon`| :material-close: | Show/hide the itinerary carbon summary | `Boolean` | `true` |
| `calories`| :material-close: | Show/hide the itinerary calories summary | `Boolean` | `false` |
| `disruption_contributors`| :material-close: | Define the list of disruption contributors id | `[String]` | `["shortterm.tr_idfm"]` |
| `disruption_contributors`| :material-close: | Define the list of disruption contributors id | `[String]` | `["shortterm.tr_idfm"]` |
| `earlier_later`| :material-close: | Enable/disable the earlier/later journeys request | `Boolean` | `false` |
| `max_favorite_addresses`| :material-close: | Define the max history items | `Int` | `0` |
| `max_favorite_pois`| :material-close: | Define the max history items | `Int` | `0` |
| `max_history`| :material-close: | Define the max history items | `Int` | `10` |
| `next_departures`| :material-close: | Show/hide the next departures | `Boolean` | `true` |
| `price`| :material-close: | Show/hide the itinerary price | `Boolean` | `true` |
| `stop_point_search`| :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` | `false` |
| `step_by_step_guidance`| :material-close: | Enable/disable the step by step guidance | `Boolean` |
| `transport_networks`| :material-close: | Show/hide the public transport network | `Boolean` | `false` |

#### Buy ticket button

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `title_res`| :material-check: | Localized buy ticket button title id | `String` | `"buy_this_journey"` |

#### Schedule features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `directions_first`| :material-close: | Show destinations before selecting the station | `Boolean` |
| `bookmark_mode`| :material-close: | Enable/disable the bookmarks feature | `Boolean` |
| `transport_networks`| :material-close: | Enable/disable grouping lines by network | `Boolean` |
| `max_history`| :material-close: | Define the max history items | `Int` |

#### Traffic features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `disruption_contributors`| :material-close: | Define the list of disruption contributors id | `[String]` | `["shortterm.tr_idfm"]` |
| `severity`| :material-close: | List of supported disruptions severities | [`[Traffic severity]`](#traffic-severity) | - |
| `alert_subscription`| :material-close: | Alert subscription environment configuration | [`Alert subscription`](#alert-subscription) | - |
| `transport_networks`| :material-close: | Enable/disable showing network on lines | `Boolean` | - |

##### Traffic severity

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res`| :material-check: | Localized severity name id | `String` | `blocking_disruptions` |
| `icon_res`| :material-check: | Severity icon resource id | `String` | `ic_blocking_disruptions` |
| `color`| :material-check: | Color of the target severity | `String` | `#E74C3C` |
| `effects`| :material-check: | List of severity effects | `[String]` | `["SIGNIFICANT_DELAYS"]` |
| `selected`| :material-close: | Whether the severity is selected by default or not | `Boolean` | `true` |

##### Alert subscription

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `env`| :material-check: | Kronos environment | `String` | `PROD` |
| `timezone`| :material-check: | Subscriptions timezone | `String` | `Europe/Paris` |

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
| `numeric`| :material-close: | Custom numeric font | [`Font category`](#font-category) |
| `alphanumeric`| :material-close: | Custom alphanumeric font | [`Font category`](#font-category) |

##### Font category

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `regular`| :material-close: | Custom numeric font for regular typeface | [`Font Typeface`](#font-typeface) |
| `semi_bold`| :material-close: | Custom numeric font for semi bold typeface | [`Font Typeface`](#font-typeface) |
| `bold`| :material-close: | Custom numeric font for bold typeface | [`Font Typeface`](#font-typeface) |
| `italic`| :material-close: | Custom numeric font for italic typeface | [`Font Typeface`](#font-typeface) |

##### Font Typeface

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `ttf_file`| :material-check: | The TTF file name | `String` | `"SourceSansPro"` |
| `fontname`| :material-check: | The font name | `String` | `"SourceSansPro-Bold"` |

### Line resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `code`| :material-check: | Navitia line code | `String` | `1` |
| `icon_res`| :material-check: | Line icon resource id | `String` | `ic_metro_1` |
| `commercial`| :material-check: | Transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

### Mode resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `icon_res`| :material-check: | Transport mode icon resource id | `String` | `ic_bus` |
| `commercial`| :material-check: | Transport commercial mode | [`Transport Commercial Mode`](#transport-commercial-mode) | - |

### Provider resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `type_id`| :material-check: | Navitia provider type id | `String` | `SCOOTER` |
| `provider_id`| :material-check: | Navitia provider id | `String` | `ridesharing_provider` |
| `icon_res`| :material-check: | Provider icon resource id | `String` | `ic_lime` |

### Network resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `network_id`| :material-check: | Navitia network id | `String` | `network:BIL:27` |
| `name_res`| :material-check: | Localized network name resource id | `String` | `sncf` |
| `icon_res`| :material-check: | Network icon resource IidD | `String` | `ic_sncf` |

### Icon resource

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `journey` | :material-close: | [`Journey icon resource`](#journey-icon-resource) | Journey |

### Journey icon resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `departure_res`| :material-close: | Departure icon resource id | `String` | `ic_departure` |
| `arrival_res`| :material-close: | Arrival icon resource id  | `String` | `ic_departure` |

### Title resource

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `aroundme` | :material-close: | [`Around Me title resource`](#around-me-title-resource) | Around Me |
| `journey` | :material-close: | [`Journey title resource`](#journey-title-resource) | Journey |

#### Around Me title resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `filters`| :material-close: | Localized filters screen title resource id | `String` | `filters_screen_title` |

#### Journey title resource

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `journeys`| :material-close: | Localized journeys screen title resource id | `String` | `journeys_screen_title` |
| `roadmap`| :material-close: | Localized roadmap screen title resource id | `String` | `roadmap_screen_title` |
| `ridesharing`| :material-close: | Localized ridesharing screen title resource id | `String` | `ridesharing_screen_title` |

### Global configuration JSON structure

You can refer to the JSON below to generate your own configuration.<br>
Please note that this is the complete version of the configuration, remove unused objects and adapt the values as needed.

``` javascript
{
  "coverage": "",
  "env": "PROD",
  "colors": {
    "account": {
      "primary": "",
      "secondary": ""
    },
    "aroundme": {
      "primary": "",
      "secondary": "",
      "tertiary": "",
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
        "primary" : "",
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
    }
  },
  "fonts": {
    "journey": {
        "numeric": {
            "regular": {
                "ttf_file": "",
                "fontname": ""
            },
            "bold": {
                "ttf_file": "",
                "fontname": ""
            },
            "semi_bold": {
                "ttf_file": "",
                "fontname": ""
            },
            "italic": {
                "ttf_file": "",
                "fontname": ""
            }
        },
        "alphanumeric": {
            "regular": {
                "ttf_file": "",
                "fontname": ""
            },
            "bold": {
                "ttf_file": "",
                "fontname": ""
            },
            "semi_bold": {
                "ttf_file": "",
                "fontname": ""
            },
            "italic": {
                "ttf_file": "",
                "fontname": ""
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
          "selected": true,
          "group": "STANDARD",
          "types": [
            {
              "name_res": "",
              "poi_type_id": ""
            }
          ],
          "booking": {
            "title_res" : ""
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
    "journey": {
      "departure_res": "ic_departure",
      "arrival_res": "ic_arrival"
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
      "signup_form_fields": [
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
      "journey_mode": true,
      "bookmark_mode": true,
      "traffic_mode": true,
      "stop_point_search": true,
      "crowdsourcing_mode": true,
      "go_from_go_to": true,
      "default_location": {
        "lat": "48.846790",
        "lon": "2.377090"
      },
      "max_history": 10
    },
    "bookmark": {
      "go_from_go_to": true
    },
    "journey": {
      "search_only": false,
      "stop_point_search": true,
      "bookmark_mode": true,
      "step_by_step_guidance": true,
      "next_departures": true,
      "price": true,
      "carbon": true,
      "calories": true,
      "transport_networks": true,
      "max_history": 10,
      "disruption_contributors": [
        ""
      ],
      "buy_tickets": {
        "title_res" : ""
      }
    },
    "schedule": {
      "directions_first": true,
      "bookmark_mode": true,
      "transport_networks": true,
      "max_history": 10
    },
    "traffic": {
      "disruption_contributors": [
        ""
      ],
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
      "alert_subscription": {
        "env": "PROD",
          "timezone": "Europe/Paris"
      },
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
| `drag`| `map`, `bottomSheet`, `chart`, `map` | The user performs a drag action |
| `edit`| `field` | The user has changed the input value of an object |
| `tap`| `button`, `item`, `switch`, `tab` | The user performs a tap action |
| `scroll`| `bottomSheet`, `list` | The user started a scroll on an object |
| `show`| - | A screen is displayed |
| `swipe`| `bottomSheet` | The user performs a swipe action |
| `zoom`| `map` | The user performs whether a pinch, a double tap action to zoom on an object |

You can find in the following table the list of UI modules that support the event tracking features

<h4>Android</h4>

| Module name | Available | Implementation |
| --- | ---- | :---: |
| Around Me | :material-close: | - |
| Bookmark | :material-close: | - |
| Journey | :material-check: | [Journey events tracking](../journey/android/#events-tracking) |
| Schedule | :material-close: | - |
| Traffic | :material-close: | - |

<h4>iOS</h4>

| Module name | Available | Implementation |
| --- | ---- | :---: |
| Around Me | :material-close: | - |
| Bookmark | :material-close: | - |
| Journey | :material-check: | [Journey events tracking](../journey/ios/#events-tracking) |
| Schedule | :material-close: | - |
| Traffic | :material-close: | - |
