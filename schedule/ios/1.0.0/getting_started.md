---
layout: main
title: Getting started
parent: Schedule iOS
grand_parent: Schedule
nav_order: 1
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

## 💻 Setup

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
  pod 'ScheduleSDK', '~> 0.2.0' # Schedule Pod definition
end
```

## 🚀 Launching

This module needs to be initialized before launching the main `ViewController`. Therefore, You need to call the `Schedule.shared.initialize()` method.\
Please refer to the following code:

```swift
do {
    guard let scheduleViewController = Schedule.shared.rootViewController else {
      return
    }

    let scheduleColorsConfiguration = ScheduleColorsConfiguration(primary: .blue, secondary: .systemOrange)
    let transportsResConfigurationJson = "transportResConfig.json"
    let scheduleConfiguration = try ScheduleConfiguration(colorsConfiguration: scheduleColorsConfiguration,
                                                          transportsResConfigurationJson: transportsResConfigurationJson)
    
    try Schedule.shared.initialize(token: navitia_token,
                                   coverage: navitia_coverage,
                                   configuration: scheduleConfiguration)
    navigationController?.pushViewController(scheduleViewController, animated: false)
} catch {
    Logger.error("%@", String(format: "ScheduleSDK cannot be initialized! %@", error.localizedDescription))
}
```

## 🛠 Configuration

The `ScheduleConfiguration` is a mandatory element to pass to the `ìnitialize()` method. The below is the list of parameters required to build this configuration object:

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `colorsConfiguration` | ✓ | To set the module colors configuration | ✗ |
| `transportsResConfigurationJson` | ✗ | To customize the icons of transport modes and lines | ✗ |
| `transportsResConfigurationJson` | ✗ | To customize the icons of transport modes and lines from JSON file | ✗ |

</div>

### Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `primary` | ✓ | To set the background color | ✗ |
| `secondary` | ✗ | To set the color of some UI components | `primary` |

</div>

### Icons
​
The module offers the possibility to customize the icons of modes of transport and lines. You may need to request Navitia first to get your available list of lines and commercial modes for your coverage:<br> `https://api.navitia.io/v1/coverage/<COVERAGE>/lines`
​
- Transport lines

The `lines` is a JSON array of transport lines.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `code` | String | ✓ | [Code of the line](http://doc.navitia.io.#public-transportation-objects-exploration) from Navitia |
| `icon_res` | Array | ✓ | Icon resource ID of the line |
| `mode_id` | Array | ✓ | Commercial mode name of the corresponding mode described below |
​
</div>

- Transport modes

The `modes` is a JSON array of transport modes.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `id` | String | ✓ | [Commercial mode name](http://doc.navitia.io/#commercial-mode) from Navitia |
| `icon_res` | String | ✓ | Icon resource ID of the mode |
|`name_res`| String |✓| Name resource ID of the mode |
| `physical` | Array  | ✓ | Array of concerned physical mode |

</div>

### How to configure Icons?
​
Follow one of the steps below:
​
- Using JSON file

The JSON file should be added to the `Resources` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file
​
```json
{
  "lines": [
    {
      "code": "1",
      "icon_res": "ic_metro_1",
      "mode_id": "Metro",
    },
    {
      "code": "2",
      "icon_res": "ic_metro_2",
      "mode_id": "Metro",
    },
    {
      "code": "3",
      "icon_res": "ic_metro_3",
      "mode_id": "Metro",
    }
  ],
  "categories": [
    {
      "commercial": "Métro",
      "icon_res": "ic_metro",
      "name_res": "metro",
      "subcategories": [
          {
              "name_res": "metro",
              "physical_mode": "physical_mode:Metro"
              
          }
      ]
    }
  ]
}  
```
```swift

// Usage of Configure lines and modes icons from json file
let scheduleConfiguration = try ScheduleConfiguration(
  colorsConfiguration: scheduleColorsConfiguration,
  transportsResConfigurationJson: transportsResConfigurationJson
)​
```

- Using Configuration object
​
```swift
// Configure lines
let linesIcons = [
    ConfigurationLineModel(code: "1", iconNameRes: "ic_metro_1", modeId: "Metro"),
    ConfigurationLineModel(code: "2", iconNameRes: "ic_metro_2", modeId: "Metro"),
    ConfigurationLineModel(code: "3", iconNameRes: "ic_metro_3", modeId: "Metro")
]
​
// Configure modes
let modesIcons = [
    ConfigurationModeModel(id: "Metro", 
                           iconNameRes: "ic_metro", 
                           nameRes: "Métro", 
                           physicalMode: ["physical_mode:Metro"])
]
​
// Setup configuration object
let scheduleConfiguration = try ScheduleConfiguration(
    colorsConfiguration: scheduleColorsConfiguration,
    transportsResConfiguration: transportsResConfiguration
)
```
