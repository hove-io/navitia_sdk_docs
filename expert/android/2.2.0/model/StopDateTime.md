---
layout: main
title: StopDateTime
nav_exclude: true
permalink: /expert/android/model/StopDateTime
---

# StopDateTime

---

## Properties

Name | Type | Note
---- | ---- | ----
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**links** | [**List&lt;LinkSchema&gt;**](LinkSchema.md) | 
**arrivalDateTime** | **String** | [optional] 
**additionalInformations** | [**List&lt;AdditionalInformationsEnum&gt;**](#List&lt;AdditionalInformationsEnum&gt;)
**departureDateTime** | **String** | [optional] 
**baseArrivalDateTime** | **String** | [optional] 
**baseDepartureDateTime** | **String** | [optional] 
**dataFreshness** | [**DataFreshnessEnum**](#DataFreshnessEnum)[optional] 

## List&lt;AdditionalInformationsEnum&gt;

Name | Value
---- | -----
PICK_UP_ONLY | &quot;pick_up_only&quot;
DROP_OFF_ONLY | &quot;drop_off_only&quot;
ON_DEMAND_TRANSPORT | &quot;on_demand_transport&quot;
DATE_TIME_ESTIMATED | &quot;date_time_estimated&quot;

## DataFreshnessEnum

Name | Value
---- | -----
BASE_SCHEDULE | &quot;base_schedule&quot;
ADAPTED_SCHEDULE | &quot;adapted_schedule&quot;
REALTIME | &quot;realtime&quot;

