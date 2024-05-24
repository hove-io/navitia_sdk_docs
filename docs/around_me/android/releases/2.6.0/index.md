---
title: AroundMe Android 2.6.0 - Changelog - Navitia SDK Docs
---

# Around Me Android 2.6.0 Changelog

<h2>🗓 11 Jan 2024</h2>

#### Features
- Customizable disruption colors
- Add clusters on the map for bus station and POI markers
- Remove postal code from POI details
- Show an auto-completion POI result only if it's filtered
- Auto-completion results are ordered by distance if the user location is enabled

#### Fix
- Fix negative battery on scooter
- Fix auto-completion history order
- Fix auto-completion result height

#### Tasks
- Add proguard rules for Crashlytics
- Add proguard rules for `java.io.Serializable`
- Add frequency for next departures request in configuration

#### Dependencies
- `com.android.tools.build:gradle` > `8.1.1`
- `compileSdk` > `34`
- `buildToolsVersion` > `34.0.0`
- `com.google.maps.android:android-maps-utils` > `3.5.3`
- `com.kisio.navitia.sdk.data:expert` > `3.4.1`
