---
title: Expert Android 3.6.0 - Changelog - Navitia SDK Docs
---

# Expert Android 3.6.0 Changelog

<h2>🗓 13 Feb 2025</h2>

#### API
- Add `language` query parameter to `CommericalModesApi`, `CompaniesApi`, `ContributorsApi`, `DatasetsApi`, `DisruptionsApi`, `JourneyPatternPointsApi`, `JourneyPatternsApi`, `LineGroupsApi`, `LineReportsApi`, `LinesApi`, `NetworksApi`, `PhysicalModesApi`, `PoisApi`, `PoiTypesApi`, `RoutesApi`, `StopAreasApi`, `StopPointsApi`, `TrafficReportApi`, `TripsApi` and `VehicleJourneysApi`
- Update `from_datetime` query parameter type from`RouteSchedulesApi`

#### Models
- Add `BookingRule`
- Remove `CarParkPrice`
- Update `Channel.Type`
- Update `Poi`
- Update `PtObject`
- Update `RouteDisplayInformation`
- Update `VehicleJourneyPositions`

#### Dependencies
- `gradle` > `8.10.2`
- `kotlinVersion` > `2.1.0`
- `com.android.tools.build:gradle` > `8.8.0`
- `compileSdk` > `35`
- `buildToolsVersion` > `35.0.0`
- `org.jetbrains.kotlinx:kotlinx-serialization-json` > `1.6.3`

#### Based on Navitia
https://github.com/hove-io/navitia/releases/tag/v15.75.4
