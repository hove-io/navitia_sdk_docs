---
layout: default
title: Getting started
parent: Journey Android
grand_parent: Journey
nav_order: 1
permalink: /journey/android/getting-started
---

# Getting Started

---

## Installation
Add the following dependency to your `build.gradle` file:

```ruby
dependencies {
    implementation("com.kisio.sdk:navitia-sdk-ui:2.1.0")
}
```

For the use of cartography, add your Google Maps API Key to your `AndroidManifest.xml` as well
```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY"/>
```

The activity launching journeyUI must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`
```
<activity
    android:name=".MainActivity"
    android:configChanges="orientation|screenSize"
```

## Set up
This module is set up by `JourneysUI.getInstance()`. The singleton behave like a builder with each methods allowing you to configure the module.  You need to call at the end `init()` with the current activity as parameter.

| Configuration | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| `.token("my-token")` | `String` | ✓ | Navitia token (generate a token on [navitia.io](https://www.navitia.io/))| `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `.mainColor("")` | `String` | ✗ | To set the background and the journey's duration colors  | by default `#40958E` |
| `.originColor("")` | `String` | ✗ | To set the color of the origin icon and the roadmap departure block | by default `#00BB75` |
| `.destinationColor("")` | `String` | ✗ | To set the color of the destination icon and the roadmap arrival bloc  | by default `#B00353` |
| `.maxHistory(1)` | `int` | ✗ | To set up the maximum number of items you can find in autocompletion search history | by default 10 |
| `.withMultiNetwork()` | ✗ | ✗ | To set the display of the network name in the roadmap  | by default `false`. Calling the method put it to `true` |
| `.withMaas()` | ✗ | ✗ | Some UI can have a different behaviour for this using in a Maas project | by default `false`. Calling the method put it to `true` |

#### Example
```java
JourneysUI.getInstance()
    .token("my-token")
    .mainColor("#40958E")
    .originColor("#00BB75")
    .destinationColor("#B00353")
    .maxHistory(10)
    .withMultiNetwork()
    .withMaas()
    .init(this);
```
