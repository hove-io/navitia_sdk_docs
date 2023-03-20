# Journey Android 5.2.2 Changelog

<h2>🗓 17 Mar 2023</h2>

#### Features
- Add events analytics
- Show journeys history
- Show favorite journeys
- Show favorite addresses and POIs in auto completion
- Add `carNoPark` section mode support

#### Fixes
- Fix request of ridesharing journeys without any common transportation
- Fix autocompletion search

#### Tasks
- Change configuration color variable names
- Add bike configuration colors
- Add direct path modes configuration support
- Ridesharing journeys request is made independent from the public transport request
- Remove `addPoiInfos`, `directPathModes`, `firstSectionModes`, `forbiddenUris` and `lastSectionModes` from `JourneysRequest`

#### Dependencies
- `androidx.recyclerview:recyclerview` >`1.3.0`
- `com.kisio.navitia.sdk.ui:bookmark` > `1.2.1`
