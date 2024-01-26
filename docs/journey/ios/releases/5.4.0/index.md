---
title: Journey iOS 5.4.0 - Changelog - Navitia SDK Docs
---

# Journey iOS 5.4.0 Changelog

<h2>🗓 17 Mar 2023</h2>

#### Features
- Add events analytics
- Show journeys history
- Show favorite journeys
- Show favorite addresses and POIs in auto completion
- Add BSS trip duration and distance
- Add `carNoPark` section mode support

#### Tasks
- Add direct path modes configuration support
- Change `search` param to `searchOnly` param
- Change configuration color variable names
- Add bike configuration colors
- Ridesharing journeys request is made independent from the public transport request
- Remove `addPoiInfos`, `directPathModes`, `firstSectionModes`, `forbiddenUris` and `lastSectionModes` from `JourneysRequest`

#### Fixes
- Fix BSS bike and places availability not showing
- Fix bike path not showing on map
- Fix autocompletion wrong sections order

#### Dependencies
- `BookmarkSDK` -> `1.2.0`
