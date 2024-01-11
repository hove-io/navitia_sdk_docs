# Traffic Android 2.4.0 Changelog

<h2>🗓 11 Jan 2024</h2>

#### Features
- Customizable disruption colors
- Add network filter in line list
- Enhance accessibility

#### Fixes
- Avoid possible crash on day selection for a new line alert
- Fix lines not showing in My Alerts after adding a subscription
- Fix title length for a line disruption

#### Tasks
- Add proguard rules for Crashlytics
- Add proguard rules for `java.io.Serializable`

#### Dependencies
- `com.android.tools.build:gradle` > `8.1.1`
- `compileSdk` > `34`
- `buildToolsVersion` > `34.0.0`
- `com.kisio.navitia.sdk.data:expert` > `3.4.1`
