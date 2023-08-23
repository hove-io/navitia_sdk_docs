# Bookmark Android 1.2.2 Changelog

<h2>🗓 23 Aug 2023</h2>

#### Feature
- Tabs are now configurable

#### Fix
- Fix deletion of a line from a favorite station
- Fetch location if the user use _Go to there_ function

#### Tasks
- Add custom analytics events
- Update BookmarkEnvironment which can have SBX, CUS and PROD
- Delegate is no more accessible
- Add navigation listener and remove navigation callbacks from `BookmarkUI.init()`
- Rename `BookmarkConfiguration.featuresConfiguration` by `BookmarkConfiguration.features`

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
