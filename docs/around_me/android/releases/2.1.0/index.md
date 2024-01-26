---
title: AroundMe iOS 2.1.0 - Changelog - Navitia SDK Docs
---

# Around Me Android 2.1.0 Changelog

<h2>🗓 10 Jan 2023</h2>

#### Features
- Can add a station or a POI as favorite
- Show _my position_ button only in full map mode
- Can open directly bookmarks and _Traffic_
- Add progress indicators in bottom sheet at first data loading

#### Tasks
- Replace `Gson` by `kotlinx.serialization`
- Enhance map performance
- Prefix all layouts by `navitia_nearby_`
- Token is passed via `init()` instead of configuration file or object

#### Fixes
- Fix back button action

#### Dependencies
- `gradle-wrapper` > `7.4`
- `com.android.tools.build:gradle` > `7.3.1`
- `androidx.navigation:navigation-fragment-ktx` > `2.5.3`
- `com.kisio.navitia.sdk.data:expert` > `3.2.2`
- `org.jetbrains.kotlinx:kotlinx-serialization-json` > `1.4.1`
