# Journey Android 5.7.0 Changelog

<h2>🗓 23 Aug 2023</h2>

#### Features
- Add specific error messages when a search request failed
- Update automatically walking instruction in the step by step guidance based on user location
- Can configure and show in a autocompletion result if this is included in the main region of the coverage or not
- Show if a journey contains a low emission zone for a car section
- Add a deep link to an map application for a walking, car or bike section in roadmap
- Show nearby bus station on the map in roadmap
- Show station entrance and station exit on the map in roadmap
- Show vehicle positions on the map in roadmap
- Show next departures beyond 1 hour
- Show icon for air-conditioned lines

#### Fixes
- Fix display of location button in roadmap
- Fix initial UI state when navigating from guidance back to roadmap
- Fix display of an empty state right before the journey search results
- Fix bottom sheet scroll for walking instructions in guidance
- Fix display of lines when a searched station is added to history
- Fix departure and arrival field states
- Fix display of line icon in a `SpannableString` in guidance

#### Tasks
- Add custom analytics events
- Update `JourneyEnvironment` which can have `SBX`, `CUS` and `PROD`
- Delegate is no more accessible
- Add navigation listener and remove navigation callbacks from `JourneyUI.init()`

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
