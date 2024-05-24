---
title: Journey Android 5.12.0 - Changelog - Navitia SDK Docs
---

# Journey Android 5.12.0 Changelog

<h2>🗓 21 Mai 2024</h2>

#### Features
- Itineraries organized by tab and public transport based sections
- Alternative api calls for bike, car and ridesharing are launched on request
- Enhance accessibilty

#### Task
- Enlarge horizontally main content
- Update next departures design

#### Fixes
- Fix 'outside of region' string
- Fix realtime request performance
- Fix `externalNavigation` feature configuration
- Use correctly `maxFavoriteAddresses` configuration
- Fix _later_ button when launching the request with a same datetime on some cases
- Show history when clicking on the clear button
- Fix order of transport modes and lines for an history entry

#### Dependencies
- `com.kisio.navitia.sdk.engine:design` > `2.14.0`
- `com.kisio.navitia.sdk.engine:router` > `2.4.0`
- `com.kisio.navitia.sdk.engine:toolbox` > `1.14.0`
