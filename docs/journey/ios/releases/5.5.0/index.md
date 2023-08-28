# Journey iOS 5.5.0 Changelog

<h2>🗓 28 Aug 2023</h2>

#### Features 
- Add specific error messages when a search request failed
- Update automatically walking instruction in the step by step guidance based on user location
- Update automatically the cards in guidance based on user location
- Can configure and show in a autocompletion result if this is included in the main region of the coverage or not
- Show if a journey contains a low emission zone for a car section
- Add a deep link to an map application for a walking, car or bike section in roadmap
- Show nearby bus station on the map in roadmap
- Show station entrance and station exit on the map in roadmap
- Show vehicle positions on the map in roadmap
- Show next departures beyond 1 hour
- Show icon for air-conditioned lines
- Add button to toggle between satellite and standard map types
- Add `ShowBack` param
- Can subscribe to a traffic alert when a journey is bookmarked
- Show the number of available ridesharing for a journey
- Hide tabs if corresponding filter is disabled

#### Tasks
- Add custom analytic events
- Show guidance cards in full screen
- Add missing params in `JourneyRequest` object

#### Fixes
- Fix header size in roadmap
- Fix ridesharing loading state when no ridesharing journeys found
- Fix car tabs not appearing when it's the only mode configured
- Fix bottom sheet scroll in roadmap and guidance
- Fix next departure annotations on guidance map
- Fix percentage of cyclable lanes
- Fix ridesharing offers count showing only with carbon and calories
 
#### Dependencies
- `FlexLayout` -> `1.3.31`
- `RealmSwift` -> `10.42.0`
- `DesignEngine` -> `2.7.0`
- `RouterEngine` -> `1.0.0`
- `BookmarkSDK` -> `Removed`

#### Deployment target
-  `iOS 14` minimun
