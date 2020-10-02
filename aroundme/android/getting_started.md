---
layout: default
title: Getting started
parent: Around Me Android
grand_parent: Around Me
nav_order: 2
permalink: /around-me/android/getting-started
---

# Getting started

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

The activity launching Around Me must handle the following configuration changes: `orientation|screenSize` declared into your `AndroidManifest.xml`
```xml
<activity
    ...
    android:configChanges="orientation|screenSize"
    .../>
```

## Configuration & initialization
This module is set up by `AroundMeUI.getInstance()`. The singleton behave like a builder with each methods allowing you to configure the module. You need to call at the end `init()`.

#### Example
```kotlin
AroundMeUI.getInstance()
    .withGoFromGoTo()
    .maxHistory(10)
    .init(
        activity = WeakReference(this),
        colors = AroundMeColors(
            backgroundColor = "#0277BD",
            primaryColor = "#FF4081"
        ),
        coverage = "fr-idf",
        token = "0de19ce5-e0eb-4524-a074-bda3c6894c19",
        preferencesConfigFile = ""
    )
```

### Colors
<div markdown="1">

| Configuration | Required | Description | Example |
| --- |:---:| --- | --- |
| `backgroundColor: String` | ✓ | To set the background color | `"#0277BD"` |
| `primaryColor: String` | ✓ | To set the primary color | `"#FF4081"` |

</div>

### Configuration methods
<div markdown="1">

| Configuration | Required | Description | Example |
| --- |:---:| --- | --- |
| `.maxHistory(Int)` | ✗ | To set up the maximum number of items you can find in autocompletion search history | by default `10` |
| `.withGoFromGoTo()` | ✗ | To display _Go From_ and _Go to_ buttons to open Journey | by default `false`. Calling the method put it to `true` |

</div>

### Init method
<div markdown="1">

| Parameter | Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `activity` | `WeakReference<AppCompatActivity>` | Weak reference of the activity launching the module | Assuming `this` is an AppCompatActivity<br>`WeakReference(this)` |
| `colors` | `AroundMeColors` | To set colors of Around Me  | `AroundMeColors(#0277BD, #FF4081)` |
| `coverage` | `String` | Your Navitia coverage | `fr-idf` |
| `token` | `String` | Your Navitia token | `0de19ce5-e0eb-4524-a074-bda3c6894c19` |
| `defaultLocation` | `Pair<Double, Double>` | Default location on Map at the very first launch of Around Me | by default `48.8467812 to 2.3771505` |
| `navigationListener` | `NavigationListener?` | Listener the module can rely on for navigation events within the app | by default `null` |

</div>





