---
layout: main
title: Place
nav_exclude: true
permalink: /expert/ios/model/Place
---

# Place

---

## Properties

Name | Type | Note
---- | ---- | ----
**embeddedType** | [**EmbeddedType**](#EmbeddedType)
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**administrativeRegion** | [**Admin**](Admin.md) | [optional] 
**name** | **String** | Name of the object 
**distance** | **String** | Distance to the object in meters [optional] 
**address** | [**Address**](Address.md) | [optional] 
**poi** | [**Poi**](Poi.md) | [optional] 
**quality** | **Int** | [optional] 
**id** | **String** | Identifier of the object 
**stopArea** | [**StopArea**](StopArea.md) | [optional] 

## EmbeddedType

Name | Value
---- | -----
line | line
journeyPattern | journey_pattern
vehicleJourney | vehicle_journey
stopPoint | stop_point
stopArea | stop_area
network | network
physicalMode | physical_mode
commercialMode | commercial_mode
connection | connection
journeyPatternPoint | journey_pattern_point
company | company
route | route
poi | poi
contributor | contributor
address | address
poitype | poitype
administrativeRegion | administrative_region
calendar | calendar
lineGroup | line_group
impact | impact
dataset | dataset
trip | trip

