---
layout: default
title: Getting started
parent: Journey Android
grand_parent: Journey
nav_order: 2
permalink: /journey/android/getting-started
---

# Getting Started

FROM JOURNEY REPO
---

## Installation
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
    implementation("com.kisio.navitia.sdk.ui:journey:3.1.2")
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

## Configuration & initialization
This module is set up by `JourneysUI.getInstance()`. The singleton behave like a builder with each methods allowing you to configure the module. You need to call at the end `init()`.

#### Example
```kotlin
JourneysUI.getInstance()
    .token("0de19ce5-e0eb-4524-a074-bda3c6894c19")
    .colors(JourneysColors("#0277BD").apply {
        setPrimaryColor("#FF4081")
        setOriginBackgroundColor("#00BB75")
        setDestinationBackgroundColor("#B00353")
    })
    .maxHistory(10)
    .withMultiNetwork()
    .init(WeakReference(this), null)
```

### Colors
<div markdown="1">

| Configuration | Required | Description | Example |
| --- |:---:| --- | --- |
| `JourneyColors(String)` | ✓ | To set the background color | by default `??` |
| `.setPrimaryColor(String)`<br>`.setPrimaryColorRes(ColorRes)` | ✗ | To set the color of ?? | by default `??` |
| `.setOriginColor(String)`<br>`.setOriginColorRes(ColorRes)`  | ✗ | To set the color of the origin icon and the roadmap departure block | by default `??` |
| `.setOriginBackgroundColor(String)`<br>`.setOriginBackgroundColorRes(ColorRes)`  | ✗ | To set the color of ?? | by default `??` |
| `.setOriginIconColor(String)`<br>`.setOriginIconColorRes(ColorRes)`  | ✗ | To set the color of ?? | by default `??` |
| `.setDestinationColor(String)`<br>`.setDestinationColorRes(ColorRes)` | ✗ | To set the color of the destination icon and the roadmap arrival bloc  | by default `??` |
| `.setDestinationBackgroundColor(String)`<br>`.setDestinationBackgroundColorRes(ColorRes)`  | ✗ | To set the color of ?? | by default `??` |
| `.setDestinationIconColor(String)`<br>`.setDestinationIconColorRes(ColorRes)`  | ✗ | To set the color of ?? | by default `??` |

</div>

### Configuration methods
<div markdown="1">

| Configuration | Required | Description | Example |
| --- |:---:| --- | --- |
| `.token(String)` | ✓ | Your Navitia token | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `.colors(JourneyColors)` | ✓ | To set colors of Journey  | `JourneyColors(#0277BD)` |
| `.autoCompleteTitle(String)`<br>`.autoCompleteTitle(StringRes)` | ✗ | To set the title of the auto completion view | by default the localized ressource `R.string.journeys` |
| `.formTitle(String)`<br>`.formTitle(StringRes)` | ✗ | To set the title of the form view | by default the localized ressource `R.string.journeys` |
| `.journeysTitle(String)`<br>`.journeysTitle(StringRes)` | ✗ | To set the title of the list of journeys view | by default the localized ressource `R.string.journeys` |
| `.ridesharingTitle(String)`<br>`.ridesharingTitle(StringRes)` | ✗ | To set the title of the list of ridesharings view | by default the localized ressource `R.string.ridesharing_noun` |
| `.roadmapTitle(String)`<br>`.roadmapTitle(StringRes)` | ✗ | To set the title of the roadmap view | by default the localized ressource `R.string.roadmap` |
| `.maxHistory(Int)` | ✗ | To set up the maximum number of items you can find in autocompletion search history | by default `10` |
| `.withBooking()` | ✗ | Some UI can have a different behaviour for this using in a Maas project | by default `false`. Calling the method put it to `true` |
| `.withEarlierLaterFeature()` | ✗ | ??? | by default `false`. Calling the method put it to `true` |
| `.withMaas()` | ✗ | Some UI can have a different behaviour for this using in a Maas project | by default `false`. Calling the method put it to `true` |
| `.withMultiNetwork()` | ✗ | To set the display of the network name in the roadmap  | by default `false`. Calling the method put it to `true` |
| `.withNextDepartures()` | ✗ | ??? | by default `false`. Calling the method put it to `true` |

</div>

See [Resources](/navitia_sdk_docs/journey/android/resources) for values of string resources

### Init method
<div markdown="1">

| Parameter | Type | Description | Example |
| --- | --- | --- | --- |
| `activity` | `WeakReference<AppCompatActivity>` | Weak reference of the activity launching the module | Assuming `this` is an AppCompatActivity<br>`WeakReference(this)` |
| `navigationListener` | `NavigationListener?` | Listener the module can rely on for navigation events within the app | `null` |

</div>
