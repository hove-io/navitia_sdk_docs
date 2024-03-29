---
title: Schedule Android 2.1.0 - Changelog - Navitia SDK Docs
---

# Schedule Android 2.1.0 Changelog

<h2>🗓 10 Jan 2023</h2>

#### Features
- Show bookmarks on home view
- Show bus vehicle positions on map

#### Tasks
- Replace `Gson` by `kotlinx.serialization`
- Prefix all layouts by `navitia_schedule_`
- Token is passed via `init()` instead of configuration file or object

#### Fixes
- Fix back button action

#### Dependencies
- `gradle-wrapper` > `7.4`
- `com.android.tools.build:gradle` > `7.3.1`
- `androidx.navigation:navigation-fragment-ktx` > `2.5.3`
- `com.kisio.navitia.sdk.data:expert` > `3.2.2`
- `org.jetbrains.kotlinx:kotlinx-serialization-json` > `1.4.1`
