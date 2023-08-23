# Schedule Android 2.3.0 Changelog

<h2>🗓 23 Aug 2023</h2>

#### Features
- Add city and region for a searched station
- Add network for a searched line
- Add vehicle position configuration

#### Tasks
- Add custom analytics events
- Update ScheduleEnvironment which can have SBX, CUS and PROD
- Delegate is no more accessible
- Add navigation listener and remove navigation callbacks from `ScheduleUI.init()`
- Rename `ScheduleConfiguration.featuresConfiguration` by `ScheduleConfiguration.features`

#### Dependencies
- `kotlin` > `1.8.21`
- `gradle-wrapper` > `8.0`
- `com.android.tools.build:gradle` > `8.0.2`
- `minSdk` > `23`
- `daggerVersion` > `2.44`
- `fragmentVersion` > `1.6.1`
- `kotlinCoroutinesVersion ` > `1.6.4`
- `navigationVersion` > `2.7.0`
- `roomVersion` > `2.5.2`
- `com.kisio.navitia.sdk.ui:bookmark` > Removed
