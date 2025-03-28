---
title: Journey Android 5.18.0 - Changelog - Navitia SDK Docs
---

# Journey Android 5.18.0 Changelog

<h2>🗓 25 Feb 2025</h2>

#### Features
- Bike journeys are now sorted into four possible categories: _Bike Rental_, _Bike Rental + Public Transport_, _Personal Bike + Public Transport_ and _Personal Bike_
- Display of reduce mobility parking places for a parking POI is now configurable
- Selection of a next departure for the first public transport section in the roadmap

#### Fixes
- Fix the order of lines for a station in autocomplete
- Fix the missing minute in the journey time calculation
- Fix the crash when the departure and arrival are the same during a search
- Fix the price display in the journey list
- Fix the order of sections in a favorite journey
- Fix the display of the next departures in a public transport section during step-by-step guidance
- Fix the display of contextual map buttons during step-by-step guidance
- Avoid the request for next departures for an end-to-end bike journey
- Fix the display of parking spaces in a car section when there is no data during step-by-step guidance

#### Dependencies
- `gradle` > `8.10.2`
- `kotlinVersion` > `2.1.0`
- `com.android.tools.build:gradle` > `8.8.0`
- `compileSdk` > `35`
- `buildToolsVersion` > `35.0.0`
- `daggerVersion` > `2.55`
- `fragmentVersion` > `1.8.5`
- `androidx.constraintlayout:constraintlayout` > `2.2.0`
- `androidx.core:core-ktx` > `1.15.0`
- `androidx.recyclerview:recyclerview` > `1.4.0`
- `com.kisio.navitia.sdk.engine:design` > `2.20.0`
- `com.kisio.navitia.sdk.engine:router` > `2.6.4`
- `com.kisio.navitia.sdk.engine:toolbox` > `1.20.0`
- `org.jetbrains.kotlinx:kotlinx-serialization-json` > `1.6.3`