---
title: Schedule Android 2.6.0 - Changelog - Navitia SDK Docs
---

# Schedule Android 2.6.0 Changelog

<h2>🗓 21 Mai 2024</h2>

#### Features
- Enhance accessibility
- Add `showDirectlyAutoCompletion()`

#### Task
- Enlarge horizontally main content
- Update next departure design

#### Fixes
- Fix initialization of `ScheduleDisruptionColors`
- Remove fallback on failed database migration
- Stop calling next departures when the screen is not visible
- Fix autocompletion when leaving and going back to the module
- Fix crash when clicking back button
- Fix crash when the user starts typing in autocompletion
- Reload favorites when switching tab
- Fix subcategories lines

#### Dependencies
- `com.kisio.navitia.sdk.engine:design` > `2.14.0`
- `com.kisio.navitia.sdk.engine:router` > `2.4.0`
- `com.kisio.navitia.sdk.engine:toolbox` > `1.14.0`
