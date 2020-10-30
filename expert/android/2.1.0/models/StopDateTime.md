---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# StopDateTime

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**stopPoint** | [**StopPoint**](StopPoint.md) |  |  [optional]
**links** | [**List&lt;LinkSchema&gt;**](LinkSchema.md) |  | 
**arrivalDateTime** | **String** |  |  [optional]
**additionalInformations** | [**List&lt;AdditionalInformationsEnum&gt;**](#List&lt;AdditionalInformationsEnum&gt;) |  | 
**departureDateTime** | **String** |  |  [optional]
**baseArrivalDateTime** | **String** |  |  [optional]
**baseDepartureDateTime** | **String** |  |  [optional]
**dataFreshness** | [**DataFreshnessEnum**](#DataFreshnessEnum) |  |  [optional]


<a name="List<AdditionalInformationsEnum>"></a>
## Enum: List&lt;AdditionalInformationsEnum&gt;
Name | Value
---- | -----
PICK_UP_ONLY | &quot;pick_up_only&quot;
DROP_OFF_ONLY | &quot;drop_off_only&quot;
ON_DEMAND_TRANSPORT | &quot;on_demand_transport&quot;
DATE_TIME_ESTIMATED | &quot;date_time_estimated&quot;


<a name="DataFreshnessEnum"></a>
## Enum: DataFreshnessEnum
Name | Value
---- | -----
BASE_SCHEDULE | &quot;base_schedule&quot;
ADAPTED_SCHEDULE | &quot;adapted_schedule&quot;
REALTIME | &quot;realtime&quot;



