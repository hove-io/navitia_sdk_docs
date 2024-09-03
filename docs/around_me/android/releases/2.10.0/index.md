---
title: AroundMe Android 2.10.0 - Changelog - Navitia SDK Docs
---

# Around Me Android 2.10.0 Changelog

<h2>🗓 09 Sept 2024</h2>

#### Features
- New contextual menu with the _Go from / Go to_ feature and the _See all schedule_ feature when clicking on a favorite station
- Add a `+1` label if a next departure is the next day
- Add an individual empty state if a destination has no next departures

#### Fixes
- Fix the display of lines at a station on the map
- Fixed the unexpected updating of the favorite icon in station details
- The map re-centers on the selected POI position during autocomplete search, even if its category filter is not selected on the map

#### Dependencies
- `androidx.appcompat:appcompat` > `1.7.0`
- `androidx.core:core-ktx` > `1.13.1`
- `androidx.fragment:fragment-ktx` > `1.8.2`
- `androidx.lifecycle:lifecycle-viewmodel-ktx` > `2.8.4`
- `com.google.android.material:material` > `1.12.0`
- `com.kisio.navitia.sdk.engine:design` > `2.17.0`
- `com.kisio.navitia.sdk.engine:router` > `2.6.0`
- `com.kisio.navitia.sdk.engine:toolbox` > `2.17.0`
- `org.jetbrains.kotlinx:kotlinx-coroutines-android` > `1.7.3`
- `org.jetbrains.kotlinx:kotlinx-coroutines-core` > `1.7.3`
- `androidx.test:core` > `1.6.1`
- `androidx.test.ext:junit` > `1.2.1`
- `androidx.test.espresso:espresso-core` > `3.6.1`
