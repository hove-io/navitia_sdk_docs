---
layout: main
title: Section
nav_exclude: true
permalink: /expert/ios/model/Section
---

# Section

---

## Properties

Name | Type | Note
---- | ---- | ----
**links** | [**[LinkSchema]**](LinkSchema.md) | 
**departureDateTime** | **String** | Departure date and time of the section [optional] 
**baseDepartureDateTime** | **String** | Base-schedule departure date and time of the section [optional] 
**duration** | **Int** | Duration of the section (seconds) 
**id** | **String** | 
**from** | [**Place**](Place.md) | [optional] 
**arrivalDateTime** | **String** | Arrival date and time of the section [optional] 
**additionalInformations** | [**[AdditionalInformations]**](#[AdditionalInformations]) | [optional] 
**geojson** | [**SectionGeoJsonSchema**](SectionGeoJsonSchema.md) | GeoJSON of the shape of the section [optional] 
**ridesharingInformations** | [**RidesharingInformation**](RidesharingInformation.md) | [optional] 
**to** | [**Place**](Place.md) | [optional] 
**baseArrivalDateTime** | **String** | Base-schedule arrival date and time of the section [optional] 
**transferType** | [**TransferType**](#TransferType) | [optional] 
**type** | [**ModelType**](#ModelType) | [optional] 
**dataFreshness** | [**DataFreshness**](#DataFreshness) | [optional] 
**co2Emission** | [**Amount**](Amount.md) | 
**path** | [**[Path]**](Path.md) | [optional] 
**cycleLaneLength** | **Int** | [optional] 
**displayInformations** | [**VJDisplayInformation**](VJDisplayInformation.md) | [optional] 
**mode** | [**Mode**](#Mode) | [optional] 
**ridesharingJourneys** | [**[Journey]**](Journey.md) | [optional] 
**stopDateTimes** | [**[StopDateTime]**](StopDateTime.md) | [optional] 

## [AdditionalInformations]

Name | Value
---- | -----
odtWithZone | odt_with_zone
odtWithStopPoint | odt_with_stop_point
odtWithStopTime | odt_with_stop_time
hasDatetimeEstimated | has_datetime_estimated
regular | regular
stayIn | stay_in

## TransferType

Name | Value
---- | -----
walking | walking
stayIn | stay_in

## ModelType

Name | Value
---- | -----
publicTransport | public_transport
streetNetwork | street_network
waiting | waiting
transfer | transfer
boarding | boarding
landing | landing
bssRent | bss_rent
bssPutBack | bss_put_back
crowFly | crow_fly
park | park
leaveParking | leave_parking
alighting | alighting
ridesharing | ridesharing
onDemandTransport | on_demand_transport

## DataFreshness

Name | Value
---- | -----
baseSchedule | base_schedule
adaptedSchedule | adapted_schedule
realtime | realtime

## Mode

Name | Value
---- | -----
walking | walking
bike | bike
car | car
bss | bss
ridesharing | ridesharing
carnopark | carnopark
taxi | taxi

