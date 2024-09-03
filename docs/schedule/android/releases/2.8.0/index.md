---
title: Schedule Android 2.8.0 - Changelog - Navitia SDK Docs
---

# Schedule Android 2.8.0 Changelog

<h2>🗓 09 Sept 2024</h2>

#### Features
- New contextual menu with the _Go from / Go to_ feature when clicking on a favorite station
- Add a `+1` label if a next departure is the next day
- Add an individual empty state if a destination has no next departures

#### Fixes
- Fix history database in the autocompletion search
- Fix network filter mechanic and it can bet written in 2 lines
- Fix empty state and error handling on the lines pager
- Fix the timetable update after selecting an hour

#### Dependencies
- `androidx.appcompat:appcompat` > `1.7.0`
- `androidx.fragment:fragment-ktx` > `1.8.2`
- `androidx.lifecycle:lifecycle-viewmodel-ktx` > `2.8.4`
- `com.kisio.navitia.sdk.engine:design` > `2.17.0`
- `com.kisio.navitia.sdk.engine:router` > `2.6.0`
- `com.kisio.navitia.sdk.engine:toolbox` > `2.17.0`
- `org.jetbrains.kotlinx:kotlinx-coroutines-android` > `1.7.3`
- `org.jetbrains.kotlinx:kotlinx-coroutines-core` > `1.7.3`
- `androidx.test:core` > `1.6.1`
- `androidx.test.ext:junit` > `1.2.1`
- `androidx.test:rules` > `1.6.1`
- `androidx.test:runner` > `1.6.1`
- `androidx.test.espresso:espresso-core` > `3.6.1`
