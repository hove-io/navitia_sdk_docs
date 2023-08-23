# Around Me Android 2.5.0 Changelog

<h2>🗓 23 Aug 2023</h2>

#### Features
- Add quick filters for public transports and free floatings
- Show line routes and vehicle positions on map when clicking on a bus station
- New POI filters button on map
- New configurable markers colors

#### Fixes
- Fix absence of next departures on some occurrences
- Fix marker for an searched address
- Remove favorite title when there are no favorites

#### Tasks
- Add custom analytics events
- Update AroundMeEnvironment which can have SBX, CUS and PROD
- Delegate is no more accessible
- Add navigation listener and remove navigation callbacks from `AroundMeUI.init()`

#### Dependencies
- `kotlin` > `1.8.21`
- `gradle-wrapper` > `8.0`
- `com.android.tools.build:gradle` > `8.0.2`
- `minSdk` > `23`
- `com.kisio.navitia.sdk.ui:bookmark` > Removed
