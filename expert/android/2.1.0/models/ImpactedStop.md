---
layout: default
title: ImpactedStop
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/impacted_stop
---

# ImpactedStop

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**amendedArrivalTime** | **String** |  |  [optional]
**stopPoint** | [**StopPoint**](/navitia_sdk_docs/expert/android/endpoints/stop_point) |  |  [optional]
**stopTimeEffect** | [**StopTimeEffectEnum**](#StopTimeEffectEnum) |  |  [optional]
**departureStatus** | **String** |  |  [optional]
**isDetour** | **Boolean** |  | 
**amendedDepartureTime** | **String** |  |  [optional]
**baseArrivalTime** | **String** |  |  [optional]
**cause** | **String** |  | 
**baseDepartureTime** | **String** |  |  [optional]
**arrivalStatus** | **String** |  |  [optional]


<a name="StopTimeEffectEnum"></a>
## Enum: StopTimeEffectEnum
| Name | Value
| ---- | -----
DELAYED | &quot;delayed&quot;
ADDED | &quot;added&quot;
DELETED | &quot;deleted&quot;
UNCHANGED | &quot;unchanged&quot;



