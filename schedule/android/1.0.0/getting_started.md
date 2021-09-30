---
layout: main
title: Getting started
parent: Schedule Android
grand_parent: Schedule
nav_order: 2
permalink: /schedule/android/getting-started
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

## 💻 Setup

The access to `Schedule` module requires valid credentials to our private artifactory. Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials:

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
    implementation("com.kisio.navitia.sdk.ui:schedule:1.0.0")
}
```

The activity launching Schedule must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`:

```xml
<activity
    ...
    android:configChanges="orientation|screenSize"
    .../>
```

## 👨‍💻 Implementation

- Init
This module is set up by calling `ScheduleUI.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. \
This method takes the following parameters:

<div markdown="1">

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| `activity` | `WeakReference<AppCompatActivity>` | ✓ | Weak reference of the activity launching the module | ✗ |
| `colors` | `ScheduleColors` | ✓ | Module colors configuration | ✗ |
| `coverage` | `String` | ✓ | Navitia target coverage | ✗ |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `configuration` | `Configuration` | Only if `configurationJsonFile` is not set | Data configuration of the module | `null` |
| `configurationJsonFile` | `String` | Only if `Configuration` is not set | Json file name in `assets` folder | `null` |
| `navigationListener` | `NavigationListener` | ✗ | Listener the module can rely on for navigation events within the app | `null` |

</div>

##### Example

```kotlin
ScheduleUI.getInstance()
   .init(
       activity = WeakReference(this),
       colors = ScheduleUIColors(
           primaryColor = "#0277BD",
           secondaryColor = "#FF4081"
       ),
       coverage = "YOUR_COVERAGE",
       token = "YOUR_TOKEN",
       configuration = Configuration(), // Not required if configurationJsonFile is set
       configurationJsonFile = "jsonFile", // Not required if configuration object is set
       { fragment, _ ->
           // Navigate from Fragment1 to Fragment2
           // Execute some instructions
       },
       {
           // Navigate from Fragment2 to Fragment1
           // Execute some instructions
           return true
       }
   )
```

- Activity delegation

Since the module launches itself fragments, you may want to execute their `onBackPressed()` from your activity.
For that, you have to attach the activity that will host fragments to `ScheduleUI.getInstance()`. This will provide a delegate which will execute `onBackPressed()` on the displayed fragment.\
You can call this method before or after `init()`.

<div markdown="1">

| Method | Description | Example |
| --- | --- | --- |
| `.attachActivity(AppCompatActivity)` | Attach the activity that will host Schedule fragments |

</div>

Then, you can call `ScheduleUI.getInstance().delegate` to obtain the delegate.
Therefore, if you try to access it without attaching an activity before, an exception will be thrown.

```kotlin
ScheduleUI.getInstance().attachActivity(AppCompatActivity)
...
ScheduleUI.getInstance().delegate.onBackPressed()
```

## 🚀 Launching

Schedule has one entry point `HomeFragment`. Please make sure to `init` the module before launching this fragment.

- Example

Assuming you have an `AppCompatActivity` with a fragment container, please refer to the following example to launch the entry screen fragment.

```kotlin
supportFragmentManager.beginTransaction().run {
    replace(R.id.container_id, HomeFragment.newInstance(), Fragment.TAG)
    addToBackStack(HomeFragment.TAG)
    commit()
}
```

## 🛠 Configuration

### Colors

<div markdown="1">

| Color | Required | Description | Default |
| --- |:---:| --- | --- |
| `primaryColor` | ✓ | To set the primary color | ✗ |
| `secondaryColor` | ✗ | To set the color of some UI components | `primaryColor` |

</div>

### Transport modes & lines

The module offers the possibility to customize icons and names of transport modes and lines.
For your coverage, you may need to request Navitia first to get your available list of lines, commercial modes and physical modes :<br>
`https://api.navitia.io/v1/coverage/<COVERAGE>/lines`<br>
`https://api.navitia.io/v1/coverage/<COVERAGE>/physical_modes`

- Transport lines

`lines` is a JSON array of transport lines.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `code` | String | ✓ | [Code of the line](http://doc.navitia.io/#public-transportation-objects-exploration) from Navitia |
| `icon_res` | String | ✓ | Icon resource ID of the line |
| `commercial` | String | ✓ | Commercial mode name of the corresponding mode described below |

</div>

- Categories

`categories` is a JSON array of categories representing group of modes.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `commercial` | String | ✓ | [Commercial mode name](http://doc.navitia.io/#commercial-mode) from Navitia |
| `icon_res` | String | ✓ | Icon resource ID of the mode |
| `name_res` | String | ✓ | String resource ID of the mode |
| `subcategories` | List<ScheduleConfigurationSubcategory> | ✓ | See below |

</div>

- Subcategories

`subcategories` is a JSON object of a single tranport mode.

<div markdown="1">

| Value | Type | Required | Description |
| --- | --- |:---:| --- |
| `name_res` | String | ✓ | String resource ID of the mode |
| `physical_mode` | String | ✓ | [Physical mode](http://doc.navitia.io/#physical-mode) of the mode |

</div>

#### How to configure Data
{: .no_toc }

- Using JSON file

The JSON file should be added to the `assets` folder of your project.
Please check the example below to know more about the structure of the configuration JSON file

```json
{
  "lines": [
    {
      "code": "B1",
      "icon_res": "ic_bus_1",
      "commercial": "Bus",
    },
    {
      "code": "B2",
      "icon_res": "ic_bus_2",
      "commercial": "Bus",
    },
    {
      "code": "1",
      "icon_res": "ic_metro_1",
      "commercial": "Metro+Tram",
    },
    {
      "code": "2",
      "icon_res": "ic_metro_2",
      "commercial": "Metro+Tram",
    },
    {
      "code": "3",
      "icon_res": "ic_metro_3",
      "commercial": "Metro+Tram",
    },
    {
      "code": "A",
      "icon_res": "ic_tram_a",
      "commercial": "Metro+Tram",
    },
    {
      "code": "B",
      "icon_res": "ic_tram_b",
      "commercial": "Metro+Tram",
    }
  ],
  "categories": [
    {
      "commercial": "Bus",
      "icon_res": "ic_bus",
      "name_res": "label_bus",
      "subcategories": [
        {
          "name_res": "label_bus",
          "physical_mode": "physical_mode:Bus"
        }
      ]
    },
    {
      "commercial": "Metro+Tram",
      "icon_res": "ic_metro_tram",
      "name_res": "label_metro_tram",
      "subcategories": [
        {
          "name_res": "label_metro",
          "physical_mode": "physical_mode:Metro"
        },
        {
          "name_res": "label_tram",
          "physical_mode": "physical_mode:Tramway"
        }
      ]
    }
  ]
}
```

- Using Configuration object

```kotlin
// Configure lines
val linesConfiguration = listOf(
    ScheduleConfigurationLine().apply {
        code = "B1"
        iconRes = "ic_bus_1"
        commercial = "Bus"
    },
    ScheduleConfigurationLine().apply {
        code = "B2"
        iconRes = "ic_bus_2"
        commercial = "Bus"
    },
    ScheduleConfigurationLine().apply {
        code = "1"
        iconRes = "ic_metro_1"
        commercial = "Metro+Tram"
    },
    ScheduleConfigurationLine().apply {
        code = "2"
        iconRes = "ic_metro_2"
        commercial = "Metro+Tram"
    },
    ScheduleConfigurationLine().apply {
        code = "3"
        iconRes = "ic_metro_3"
        commercial = "Metro+Tram"
    },
    ScheduleConfigurationLine().apply {
        code = "A"
        iconRes = "ic_tram_a"
        commercial = "Metro+Tram"
    },
    ScheduleConfigurationLine().apply {
        code = "B"
        iconRes = "ic_tram_b"
        commercial = "Metro+Tram"
    }
)

// Configure categories
val categoriesConfiguration = listOf(
    ScheduleConfigurationCategory().apply {
        commercial = "Bus"
        iconRes = "ic_bus"
        nameRes = "label_bus"
        physical = listOf(
           ScheduleConfigurationCategory(
               nameRes = "label_bus",
               physicalMode = "physical_mode:Bus"
           )
       )
    },
    ScheduleConfigurationCategory().apply {
        commercial = "Metro+Tram"
        iconRes = "ic_metro_tram"
        nameRes = "label_metro_tram"
        physical = listOf(
            ScheduleConfigurationCategory(
                nameRes = "label_metro",
                physicalMode = "physical_mode:Metro"
            )
            ScheduleConfigurationCategory(
                nameRes = "label_tram",
                physicalMode = "physical_mode:Tramway"
            )
        )
    }
)

// Setup configuration object
val configuration = ScheduleConfiguration(linesConfiguration, categoriesConfiguration)
```
