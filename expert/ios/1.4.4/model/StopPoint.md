---
layout: main
title: StopPoint
nav_exclude: true
permalink: /expert/ios/model/StopPoint
---

# StopPoint

---

## Properties

Name | Type | Note
---- | ---- | ----
**comment** | **String** | [optional] 
**commercialModes** | [**[CommercialMode]**](CommercialMode.md) | [optional] 
**stopArea** | [**StopArea**](StopArea.md) | [optional] 
**links** | [**[LinkSchema]**](LinkSchema.md) | 
**administrativeRegions** | [**[Admin]**](Admin.md) | [optional] 
**physicalModes** | [**[PhysicalMode]**](PhysicalMode.md) | [optional] 
**lines** | [**[Line]**](Line.md) | [optional] 
**comments** | [**[Comment]**](Comment.md) | [optional] 
**label** | **String** | [optional] 
**equipments** | [**[Equipments]**](#[Equipments])
**codes** | [**[Code]**](Code.md) | [optional] 
**coord** | [**Coord**](Coord.md) | [optional] 
**equipmentDetails** | [**[EquipmentDetails]**](EquipmentDetails.md) | [optional] 
**address** | [**Address**](Address.md) | [optional] 
**fareZone** | [**FareZone**](FareZone.md) | [optional] 
**id** | **String** | Identifier of the object 
**name** | **String** | Name of the object 

## [Equipments]

Name | Value
---- | -----
wheelchairAccessibility | has_wheelchair_accessibility
bikeAccepted | has_bike_accepted
airConditioned | has_air_conditioned
visualAnnouncement | has_visual_announcement
audibleAnnouncement | has_audible_announcement
appropriateEscort | has_appropriate_escort
appropriateSignage | has_appropriate_signage
schoolVehicle | has_school_vehicle
wheelchairBoarding | has_wheelchair_boarding
sheltered | has_sheltered
elevator | has_elevator
escalator | has_escalator
bikeDepot | has_bike_depot

