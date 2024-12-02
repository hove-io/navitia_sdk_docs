---
title: Journey Android 5.17.0 - Changelog - Navitia SDK Docs
---

# Journey Android 5.17.0 Changelog

<h2>🗓 02 Dec 2024</h2>

#### Features 
- New ridesharing offer UI in the list of offers and in the roadmap
- Enhance disruption UI in the roadmap and handle html titles
- Upcoming departures on the roadmap screen align with the route search date and time

#### Tasks
- Elevation graph for a bike section in the roadmap is collapsible
- Add `application_periods` in the configuration for toggling the display of disruptions
- Empty state is displayed when there is no history or favorite journeys on the home screen

#### Fixes
- Fix the journey request using `car_no_park`

#### Dependencies
- `kotlin` > `1.9.25`
- `com.android.tools.build:gradle` > `8.7.2`
- `compileSdk` > `35`
- `androidx.constraintlayout:constraintlayout` > `2.2.0`
- `androidx.core:core-ktx` > `1.15.0`
- `androidx.fragment:fragment-ktx` > `1.8.5`
- `androidx.lifecycle:lifecycle-viewmodel-ktx` > `2.8.7`
- `com.kisio.navitia.sdk.data:expert` > `3.5.2`
- `com.kisio.navitia.sdk.engine:design` > `2.19.0`
- `com.kisio.navitia.sdk.engine:router` > `2.6.2`
- `com.kisio.navitia.sdk.engine:toolbox` > `1.19.0`
