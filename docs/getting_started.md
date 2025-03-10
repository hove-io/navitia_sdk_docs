---
title: Getting started - Navitia SDK Docs
---

# Getting started

## 🧰 Requirements
- Get an access to <a href="https://navitia.io/inscription/" style="text-decoration:underline">Navitia.io</a> API. A token will be provided later and will be used to configure all the modules.
- The SDKs are accessible privately, so you should request an access to our private <a href="https://kisiodigital.jfrog.io/" style="text-decoration:underline">artifactory</a>. Those credentials will be used later to configure your machine to be able to download our dependencies.

=== "Android"

    Add the following in the `build.gradle` of your app:
    ``` kotlin
    android {
        defaultConfig {
            minSdk = 23
        }
    }
    ```

=== "iOS"

    Install <span style="text-decoration:underline">[Cocoapods](https://cocoapods.org)</span> and add the following in the `Podfile` of your project:
    ``` ruby
    platform :ios, '14.0'
    use_frameworks!
    ```

## 💻 Artifactory Setup

The access to the SDK requires valid credentials to our private artifactory. See <span style="text-decoration:underline">[Requirements](#requirements)</span> for more information. Replace `artifactoryUsername` and `artifactoryPassword` with your credentials.

=== "Android"

    Add the following in the `build.gradle` of your project:

    ``` kotlin
    repositories {
        maven {
            credentials {
                username = artifactoryUsername
                password = artifactoryPassword
            }
            url = uri("https://kisiodigital.jfrog.io/kisiodigital/android-release")
        }
    }
    ```

=== "iOS"

    Create a `.netrc` file in the `$HOME` directory of your machine and add the following line to your `.netrc` file:

    ``` ruby
    machine kisiodigital.jfrog.io login artifactoryUsername password artifactoryPassword
    ```

## 🛠 Modules Configuration

The Navitia SDKs should be configured before usage. Within a specific module, the customization can affect data or graphical components.
Since your application can integrate one or more Navitia modules, you can use a single JSON file to configure all the modules at once.<br>
The following are the possible configuration parameters:

| Name | Required | Description | Type | Possible values | Target modules |
| --- | :-: | --- | :--: | :---: | :---: |
| `coverage` | :material-check: | Navitia coverage | `String` | `fr-idf` | All |
| `timezone` | :material-check: | Timezone | `String` | `Europe/Paris` | All |
| `env` | :material-check: | Navitia environment | `String` | `PROD`, `CUSTOMER` | All |
| `colors` | :material-check: | Colors configuration | [`Colors`](#colors) | - | UI modules |
| `transport_categories` | :material-check: | List of supported transport modes | [`Transport category[]`](#transport-category) | - | UI modules |
| `poi_categories` | :material-close: | List of supported POIs | [`Poi category[]`](#poi-category) | - | Around Me, Bookmark |
| `features_configuration` | :material-close: | Enable/disable different module features | [`Features`](#features) | - | All |
| `fonts` | :material-close: | Override the fonts used in UI modules | [`Fonts`](#fonts) | - | UI modules |
| `lines_resources` | :material-close: | Resources ids for transport lines | [`Line resource[]`](#line-resource) | - | UI modules |
| `modes_resources` | :material-close: | Resources ids for transport modes | [`Mode resource[]`](#mode-resource) | - | UI modules |
| `providers_resources` | :material-close: | Resources ids for data providers | [`Provider resource[]`](#provider-resource) | - | UI modules |
| `networks_resources` | :material-close: | Resources ids for data networks | [`Network resource[]`](#network-resource) | - | UI modules |
| `icons_resources` | :material-close: | Resources ids for some specific icons | [`Icon resource`](#icon-resource) | - | UI modules |
| `titles_resources` | :material-close: | Resources ids for screen titles | [`Title resource`](#title-resource) | - | UI modules |

### Colors

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `aroundme` | :material-check: | [`Around Me color`](#around-me-color) | Around Me |
| `bookmark` | :material-check: | [`Bookmark color`](#bookmark-color) | Bookmark |
| `journey` | :material-check: | [`Journey color`](#journey-color) | Journey |
| `schedule` | :material-check: | [`Schedule color`](#schedule-color) | Schedule |
| `traffic` | :material-check: | [`Traffic color`](#traffic-color) | Traffic |
| `disruptions` | :material-check: | [`Disruption color`](#disruption-color) | All |
<!-- 
| `account` | :material-check: | [`Account color`](#account-color) | Account |
| `crowdsourcing` | :material-check: | [`Crowdsourcing color`](#crowdsourcing-color) | Crowdsourcing | 
-->

<!-- [Not yet]
#### Account color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` | 
-->

#### Around Me color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary` | :material-close: | To set the color of more UI components | `String` | `#efa59f` |
| `map` | :material-close: | To set colors of the markers on map | [`Map color`](#around-me-map-color) | - |

##### Around Me map color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `poi` | :material-check: | To set the marker color of pois | `String` | `#9b59B6` |
| `transport` | :material-check: | To set the marker color of stations | `String` | `#2980B9` |

#### Bookmark color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |

<!-- #### Crowdsourcing color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` | -->

#### Journey color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `primary` | :material-check: | To set the main color of the screens | `String` | `#88819f` |
| `secondary` | :material-check: | To set the color of some UI components | `String` | `#8faa96` |
| `tertiary` | :material-close: | To set the color of more UI components | `String` | `#efa59f` |
| `origin` | :material-close: | To set colors of the journey origin | [`Journey origin color`](#journey-origin-color) | - |
| `destination` | :material-close: | To set colors of the journey destination | [`Journey destination color`](#journey-destination-color) | - |
| `map` | :material-close: | To set colors of the map elements | [`Journey map color`](#journey-map-color) | - |
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

##### Journey map color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `path` | :material-check: | To set the color of the paths drawn on the map | [`Journey map path color`](#journey-map-path-color) | - |

##### Journey map path color

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `bike` | :material-close: | To set colors of the specific bike journey | [`Journey bike color`](#journey-bike-color) | - |
| `car` | :material-close: | To set the color of the car path | `String` | `#88819f |

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

#### Disruption color

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `information` | :material-check: | To set the color for informative disruptions | `String` | `#3FA26D` |
| `non_blocking` | :material-check: | To set the color for non blocking disruptions | `String` | `#EF662F` |
| `blocking` | :material-check: | To set the color for blocking disruptions | `String` | `#FF0000` |

### Transport category

| Name | Required | Description | Type | Example | Target modules |
| --- |:---:| --- | :---: | :---: | :---: |
| `modules` | :material-check: | To set the target modules | `String[]` | `["aroundme","journey"]` | `ALL` |
| `name_res` | :material-check: | To set the localized resource id | `String` | `transport_name_res` | `ALL` |
| `icon_res` | :material-check: | To set the icon resource id | `String` | `ic_metro` | `ALL` |
| `selected` | :material-close: | Whether the transport mode is selected by default or not | `Boolean` | `true` | `ALL` |
| `modes` | :material-close: | List of supported transport modes | [`Transport Mode`](#transport-mode) | - | `ALL` |
| `networks` | :material-close: | List of supported networks | `String[]` | `["network:BIL:27"]` | `Schedule` |
| `first_section_modes` | :material-close: | List of first section modes | `String[]` | `["bike", "car"]` | `Journey` |
| `last_section_modes` | :material-close: | List of last section modes | `String[]` | `["ridesharing", "bss"]` | `Journey` |
| `direct_path_modes` | :material-close: | List of direct path modes | `String[]` | `["taxi", "car_no_park"]` | `Journey` |
| `add_poi_infos` | :material-close: | List of requested extra POI data | `String[]` | `["bss_stands", "car_park"]` | `Journey` |

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
| `subcategories` | :material-check: | List of POI subcategories | [`POI subcategory[]`](#poi-subcategory) | - |

#### POI subcategory

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized POI subcategory name id | `String` | `"bike_stations"` |
| `icon_res` | :material-check: | POI subcategory icon id | `String` | `"ic_bike_stations"` |
| `selected` | :material-close: | Whether the subcategory is selected by default or not | `Boolean` | `true` |
| `group` | :material-check: | Subcategory POI group | `String` | `STANDARD`, `QUICK_FILTER_FREE_FLOATING`,  `QUICK_FILTER_POI` |
| `types` | :material-check: | Subcategory POI types. Can be a [POI type id](https://playground.navitia.io/play.html?request=https://api.navitia.io/v1/poi_types?) or a free floating type | `String[]`| `"poi_type:amenity:bicycle_rental"` or [one of those values](#poi-subcategory-free-floating-types) |
| `booking` | :material-close: | POI booking resources | [POI booking resources](#poi-booking-resources) | - |

##### POI subcategory free floating types

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `name_res` | :material-check: | Localized POI subcategory type name id | `String` | `"scooter"` |
| `poi_type_id` | :material-check: | Navitia POI subcategory type id | `String` | `"poi_type:amenity:bicycle_rental"` |

##### POI booking resources

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `title_res` | :material-check: | Localized POI booking button title id | `String` | `"book_a_bike"` |

### Features

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `aroundme` | :material-close: | [`Around Me features`](#around-me-features) | Around Me |
| `bookmark` | :material-close: | [`Bookmark features`](#bookmark-features) | Bookmark |
| `journey` | :material-close: | [`Journey features`](#journey-features) | Journey |
| `schedule` | :material-close: | [`Schedule features`](#schedule-features) | Schedule |
| `traffic` | :material-close: | [`Traffic features`](#traffic-features) | Traffic |
<!-- [Not yet]
| `account` | :material-close: | [`Account features`](#account-features) | Account | 
-->

<!-- [Not yet]
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

!!! info "Info"

    `PASSWORD` field type is only available for signup screen 
-->

#### Around Me features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `bookmark_mode` | :material-close: | Enable/disable the bookmarks feature | [`Bookmark mode`](#bookmark-mode-around-me) |
| `default_location` | :material-close: | The default location on first launch | [`Default location`](#default-location) |
| `go_from_go_to` | :material-close: | Show/hide the go from/go to buttons | `Boolean` |
| `journey_mode` | :material-close: | Enable/disable the journey search mode | `Boolean` |
| `max_history` | :material-close: | Define the max history items | `Int` |
| `min_zoom_level` | :material-close: | Define the min zoom level of map. Android only | `Int` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) |
| `park_availability`| :material-close: | Show/hide the bss and car parking availability | [`Park Availability`](#park-availability) |
| `schedule_mode` | :material-close: | Enable/disable redirection to schedule autocompletion screen | `Boolean` |
| `stop_point_search` | :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` |
| `traffic_mode` | :material-close: | Show/hide the traffic button | `Boolean` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on map | [`Vehicle positions`](#vehicle-positions) |
<!-- [Not yet]
| `account_mode` | :material-close: | Enable/disable the account feature | `Boolean` | 
-->

##### Bookmark Mode (Around Me)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `enabled` | :material-close: | Enable/disable to add and remove an item as favorite  | `Boolean` | `true` |
| `display` | :material-close: | Display options of favorite items on screen | [`Bookmark mode display options (Around Me)`](#bookmark-mode-display-options-around-me) | - |

##### Bookmark mode display options (Around Me)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `bss` | :material-close: | Display/hide favorite bss tab | `Boolean` | `true` |
| `journeys` | :material-close: | Display/hide favorite journeys tab  | `Boolean` | `true` |
| `stations` | :material-close: | Display/hide favorite stations tab  | `Boolean` | `true` |

##### Default location

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `lat` | :material-check: | The latitude of the default location | `String` | `"48.846790"` |
| `lon` | :material-check: | The longitude of the default location | `String` | `"2.377090"` |

#### Bookmark features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `go_from_go_to` | :material-close: | Show/hide the go from/go to buttons | `Boolean` | `true` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) | - |
| `park_availability`| :material-close: | Show/hide the bss and car parking availability | [`Park Availability`](#park-availability) |
| `schedule_mode` | :material-close: | Show/hide the "See all schedules" button | `Boolean` | `true` |
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
| `bookmark_mode` | :material-close: | Enable/disable and handle the display screens of the bookmarks feature | [`Bookmark mode`](#bookmark-mode-journey) |
| `calories` | :material-close: | Show/hide the itinerary calories summary | `Boolean` | `false` |
| `carbon` | :material-close: | Show/hide the itinerary carbon summary | `Boolean` | `true` |
| `car_parking_highlight` | :material-close: | Show/hide the car parking in the journey solution | `Boolean` | `true` |
| `car_traffic_jam` | :material-close: | Show/hide the car traffic jam in the journey solution and the roadmap | `Boolean` | `true` |
| `disruption_contributors` | :material-close: | Define the list of disruption contributors id | `String[]` | `["shortterm.tr_idfm"]` |
| `external_navigation` | :material-close: | Enable/disable the navigation using external applications | `Boolean` | `true` |
| `max_favorite_addresses` | :material-close: | Define the max favorite addresses alongside with home and work addresses | `Int` | `10` |
| `max_favorite_pois` | :material-close: | Define the max favorite POIs | `Int` | `10` |
| `max_history` | :material-close: | Define the max history items | `Int` | `10` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures (Journey)`](#next-departures-journey) | - |
| `occupancy` | :material-close: | Show/hide the occupancy of a transport section | `Boolean` | `true` |
| `park_availability`| :material-close: | Show/hide the bss and car parking availability | [`Park Availability`](#park-availability) |
| `price` | :material-close: | Show/hide the itinerary price | `Boolean` | `true` |
| `realtime_delays` | :material-close: | Show/hide the itinerary realtime delays | `Boolean` | `true` |
| `ridesharing_price` | :material-close: | Show/hide the itinerary ridesharing price | `Boolean` | `true` |
| `search_only` | :material-close: | Enable/disable a direct search without input from user | `Boolean` | `false` |
| `step_by_step_guidance` | :material-close: | Enable/disable the step by step guidance | `Boolean` |
| `stop_point_search_mode` | :material-close: | Enable/disable search by stop point instead of stop area | `Boolean` | `false` |
| `traffic` | :material-close: | Define Traffic module options | [`Traffic options`](#traffic-options-journey) | - |
| `transport_networks` | :material-close: | Show/hide the public transport network | `Boolean` | `false` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on roadmap | [`Vehicle positions`](#vehicle-positions) | - |

##### Bookmark Mode (Journey)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `enabled` | :material-close: | Enable/disable to add and remove an item as favorite  | `Boolean` | `true` |
| `display` | :material-close: | Display options of favorite items on screen | [`Bookmark mode display options (Journey)`](#bookmark-mode-display-options-journey) | - |

##### Bookmark mode display options (Journey)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `home` | :material-close: | Display/hide favorite items on home screen | `Boolean` | `true` |
| `autocompletion` | :material-close: | Display/hide favorite items on autocompletion screen  | `Boolean` | `true` |

##### Next departures (Journey)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `guidance`| :material-check: | Show/hide the next departures in the guidance screen | [`Next departures`](#next-departures) | - |
| `journeys`| :material-check: | Show/hide the next departures in the journeys screen | [`Next departures`](#next-departures) | - |
| `roadmap`| :material-check: | Show/hide the next departures in the roadmap screen | [`Next departures`](#next-departures) | - |

##### Traffic options (Journey)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `alert_subscription` | :material-close: | Enable Traffic alert subscriptions | `Boolean` | `false` |

#### Schedule features

| Name | Required | Description | Type |
| --- |:---:| --- | :---: |
| `bookmark_mode` | :material-close: | Enable/disable the bookmarks feature | [`Bookmark mode`](#bookmark-mode-schedule) |
| `go_from_go_to` | :material-close: | Show/hide the go from/go to buttons | `Boolean` | `true` |
| `line_name` | :material-close: | Show the name of the line | [`Line name`](#line-name-schedule) |
| `max_history` | :material-close: | Define the max history items | `Int` |
| `networks_filter` | :material-close: | Show/hide the networks selector | `Boolean` |
| `next_departures` | :material-close: | Show/hide the next departures | [`Next departures`](#next-departures) |
| `traffic_mode` | :material-close: | Enable/disable the traffic feature | `Boolean` |
| `transport_networks` | :material-close: | Enable/disable grouping lines by network | `Boolean` |
| `vehicle_positions`| :material-close: | Show bus vehicle positions on map | [`Vehicle positions`](#vehicle-positions) |

##### Bookmark Mode (Schedule)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `enabled` | :material-close: | Enable/disable to add and remove an item as favorite  | `Boolean` | `true` |
| `display` | :material-close: | Display options of favorite items on screen | [`Bookmark mode display options (Schedule)`](#bookmark-mode-display-options-schedule) | - |

##### Bookmark mode display options (Schedule)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `home` | :material-close: | Display/hide favorite items on home screen | `Boolean` | `true` |

##### Line Name (Schedule)

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `allowed_commerical_modes` | :material-close: | Define the list of commercial mode id allowed to show their name  | `String[]` | `["commercial_mode:Train"]` |

#### Traffic features

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `alert_subscription` | :material-close: | Alert subscription environment configuration | [`Alert subscription`](#alert-subscription) | - |
| `application_periods` | :material-close: | Show/hide the disruption application date | `Boolean` |
| `disruption_contributors` | :material-close: | Define the list of disruption contributors id | `String[]` | `["shortterm.tr_idfm"]` |
| `networks_filter` | :material-close: | Show/hide the networks selector | `Boolean` |
| `transport_networks` | :material-close: | Enable/disable showing network on lines | `Boolean` | - |

##### Alert subscription

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `env` | :material-check: | Kronos environment | `String` | `PROD` |
| `timezone` | :material-check: | Subscriptions timezone | `String` | `Europe/Paris` |

#### Common features

##### Next departures

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `frequency`| :material-check: | frequency of the next departures request in seconds | `Int` | `30` |

##### Park availability

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `frequency`| :material-check: | frequency of the bss and park availability request in seconds | `Int` | `30` |

##### Vehicle positions

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `frequency` | :material-check: | frequency of the vehicle positions request in seconds | `String` | `30` |

### Fonts

| Name | Required  | Type | Target module |
| --- | :-: | :--: | :---: |
| `aroundme` | :material-close: | [`Custom font`](#custom-font) | Around Me |
| `bookmark` | :material-close: | [`Custom font`](#custom-font) | Bookmark |
| `journey` | :material-close: | [`Custom font`](#custom-font) | Journey |
| `schedule` | :material-close: | [`Custom font`](#custom-font) | Schedule |
| `traffic` | :material-close: | [`Custom font`](#custom-font) | Traffic |
<!-- [Not yet]
| `account` | :material-close: | [`Custom font`](#custom-font) | Account | 
-->

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
| `type_id` | :material-check: | Navitia provider type id | `String` | `provider:ridesharing:lime` |
| `provider_id` | :material-check: | Navitia provider id | `String` | `ridesharing_provider` |
| `icon_res` | :material-check: | Provider icon resource id | `String` | `ic_lime` |
| `name_res` | :material-check: | Localized network name resource id | `String` | `lime` |

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

### Configuration JSON file

You can refer to the JSON file <span style="text-decoration:underline">[here](./assets/file/config.json){:download="config_example.json"}</span> to generate your own configuration.<br>
Note that this is the complete version of the configuration. Remove unused objects and adapt the values as needed.

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

=== "Android"

    | Module name  | Implementation |
    | --- | :---: |
    | Around me | [Around Me Android events tracking](../around_me/android/#events-tracking) |
    | Bookmark | [Bookmark Android events tracking](../bookmark/android/#events-tracking) |
    | Journey | [Journey Android events tracking](../journey/android/#events-tracking) |
    | Schedule | [Schedule Android events tracking](../schedule/android/#events-tracking) |
    | Traffic | [Traffic Android events tracking](../traffic/android/#events-tracking) |

=== "iOS"

    | Module name | Implementation |
    | --- | :---: |
    | Around Me | [Around Me iOS events tracking](../around_me/ios/#events-tracking) |
    | Bookmark | [Bookmark iOS events tracking](../bookmark/ios/#events-tracking) |
    | Journey | [Journey iOS events tracking](../journey/ios/#events-tracking) |
    | Schedule | [Schedule iOS events tracking](../schedule/ios/#events-tracking) |
    | Traffic | [Traffic iOS events tracking](../traffic/ios/#events-tracking) |
