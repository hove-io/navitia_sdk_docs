---
title: Journey Android 5.14.0 - Changelog - Navitia SDK Docs
---

# Journey Android 5.14.0 Changelog

<h2>🗓 09 Sept 2024</h2>

#### Features
- Update the `earlier / later` feature
- Add a `+1` label if a next departure is the next day
- Add an individual empty state if a destination has no next departures
- Displays a shimmer effect while loading next departures

#### Fixes
- Remove the systematic use of the default `dataFreshness` value in `JourneysRequest`.
- Show a dialog feedback after removing a journey from favorites
- Put a journey with a car and an on demand transport in the correct section
- Put a journey with a bike sharing service and a public transport in the correct section
- _from_ is no longer bold for the next departures in a journey
- _in direction of_ is no longer bold for public transport section in the step by step guidance
- Fix the shortest duration of all journeys in a tab results
- Fix the journey path display in the roadmap
- The shortest duration of all journeys under one minute now displays as `1 min`
- Displays the cause as the title if a disruption does not have one
- Fix the overlapping of the real-time icon for the next departures
- Fix public transport UI in the step by step guidance
- Show back button when navigating back to the results
- Fix the colors of quick settings when changing their state

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
