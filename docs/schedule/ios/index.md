# Schedule iOS

## 💻 Setup

In your project, add the following lines to your `Podfile` :

```ruby
platform :ios, '13.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CocoaPods/Specs.git' # Default Cocoapods URL
source 'https://github.com/hove-io/Podspecs.git' # Schedule podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'ScheduleSDK', '~> 3.0.0' # Schedule Pod definition
end
```

Using your CLI, run `pod install` in your project directory.

## 👨‍💻  Implementation

⚠️ Please make sure to read the [modules configuration](../../getting_started/#modules-configuration) section before proceeding!<br>

This module is set up by calling `Schedule.shared.initialize()` method which takes the following parameters:

| Name | Required | Description | Type | Example
| --- |:---:| --- | :---: | :---: |
| `coverage`| :material-check: | Navitia coverage | `String` | `fr-idf` |
| `token`| :material-check: | Navitia token | `String` | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `env`| :material-check: | Navitia environment | `String` | `PROD` |
| `colors`| :material-check: | Define the custom colors | [`ScheduleColorsConfiguration`](../../getting_started/#schedule-color) | - |
| `fonts`| :material-close: | Use custom fonts | [`ScheduleFontsConfiguration`](../../getting_started/#custom-font) | - |
| `lineResources`| :material-close: | List of transport lines resource IDs | [`[LineResource]`](../../getting_started/#line-resource) | - | 
| `modeResources`| :material-close: | List of transport modes resource IDs | [`[ModeResource]`](../../getting_started/#mode-resource) | - | 
| `transportCategories`| :material-check: | List of supported transport modes | [`[TransportCategory]`](../../getting_started/#transport-category) | - |
| `networkResources`| :material-close: | List of network resource IDs | [`[NetworkResource]`](../../getting_started/#network-resource) | - |
| `features`| :material-close: | Enable/disable some features  | [`ScheduleFeaturesConfiguration`](../../getting_started/#schedule-features) | - |

You can also call the `initialize()` method with the global JSON configuration file added to your application bundle:

| Name | Required | Description | Type | Example |
| --- |:---:| --- | :---: | :---: |
| `configurationJsonFile`| :material-check: | Global configuration JSON file name | `String` | `configuration.json` |

<h4>Example</h4>

```swift
do {
    let transportCategories = [TransportCategory(modules: ["schedule"],
                                                 iconRes: "ic_section_mode_metro",
                                                 nameRes: "metro",
                                                 selected: true,
                                                 modes: [TransportCategoryMode(physical: TransportPhysicalMode(id: "physical_mode:Metro", nameRes: "metro"),
                                                 commercial: TransportCommercialMode(id: "commercial_mode:Metro", name: "Metro"))],
                                                 firstSectionModes: ["walking"],
                                                 lastSectionModes: ["walking"])
                              ]
                              
    let scheduleColorsConfiguration = ScheduleColorsConfiguration(primaryColor: "#88819f", secondaryColor: "#8faa96")
                                                                      
    try Schedule.shared.initialize(coverage: "fr-idf",
                                    token: "0de19ce5-e0eb-4524-a074-bda3c6894c19",
                                    env: "PROD",
                                    colors: scheduleColorsConfiguration,
                                    transportCategories: transportCategories)                                                                  
} catch {
    Logger.error("%@", String(format: "Schedule SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

<h4>Example with JSON file</h4>

```swift
do {
    try Schedule.shared.initialize(configurationJsonFile: "schedule_configuration.json")                                                               
} catch {
    Logger.error("%@", String(format: "Schedule SDK cannot be initialized! %@", error.localizedDescription))
}                                   
```

## 🚀  Launching

This module has a single entry point. 

```swift
guard let scheduleViewController = Schedule.shared.rootViewController else {
  return nil
}

navigationController?.pushViewController(scheduleViewController, animated: false)
```

## 📱 Screens

### Home

The home screen allows the user to see all the lines of the defined coverage. The lines are sorted by the different configurable transport categories.<br>
Another filter is added for each transport mode in the selected transport category.

The lines can also be grouped by networks. To enable this feature, you need to switch the `transport_networks` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_home_screen.png" alt="Home screen">

### Search

The search screen allows the user to seek for a station or a line using a built-in autocompletion. The result is based on the user search input text.<br>
The station result combines both the name of the station and all the lines passing through that station. This will allow the user to select directly the searched line and get the list of all destinations starting from the target station point.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_search_screen.png" alt="Search screen">

### Stations

The station screen lists all the stations of the selected line alphabetically sorted. A search feature is added to filter the lines and makes it easier for the user to search for the desired station.<br>
In case the `directions_first` parameter is set to `true` in the [features configuration](../../getting_started/#schedule-features), this screen will show all stations of a defined route (destination).

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_line_stations_screen.png" alt="Stations screen">

### Destinations

The destinations screen lists all possible destinations starting from the target station point.<br>
In case the `directions_first` parameter is set to `true` in the [features configuration](../../getting_started/#schedule-features), this screen will show all the destinations of the selected line.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_station_destinations_screen.png" alt="Destinations screen">

### Next departures

This screen allows the user to see the next departures of the target transport mode through the selected station which is heading to the choisen destination. The map gives more details about the vehicle journey by drawing the line path and both selected station and destination markers.<br>

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_station_next_departures_screen.png" alt="Next departures screen">

### All schedules

When the user taps on the All schedules button in the [next departures](#next-departures) screen, the all schedules screen shows up and gives all theoretical departures of the selected line from the selected station to the target destination.<br>

This screen includes a datepicker button allowing the user to choose a date and see all the scheduled departures on that date.

<img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_all_schedules_screen.png" alt="All schedules screen">

## 🗺 Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img class="img-navigating" src="/navitia_sdk_docs/assets/img/schedule_ios_navigating.png" alt="Navigating">