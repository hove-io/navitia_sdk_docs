---
layout: main
title: StopDateTime
nav_exclude: true
permalink: /expert/ios/model/StopDateTime
---

# StopDateTime

---

## Properties

Name | Type | Note
---- | ---- | ----
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**links** | [**[LinkSchema]**](LinkSchema.md) | 
**arrivalDateTime** | **String** | [optional] 
**additionalInformations** | [**[AdditionalInformations]**](#[AdditionalInformations])
**departureDateTime** | **String** | [optional] 
**baseArrivalDateTime** | **String** | [optional] 
**baseDepartureDateTime** | **String** | [optional] 
**dataFreshness** | [**DataFreshness**](#DataFreshness) | [optional] 

## [AdditionalInformations]

Name | Value
---- | -----
pickUpOnly | pick_up_only
dropOffOnly | drop_off_only
onDemandTransport | on_demand_transport
dateTimeEstimated | date_time_estimated

## DataFreshness

Name | Value
---- | -----
baseSchedule | base_schedule
adaptedSchedule | adapted_schedule
realtime | realtime

