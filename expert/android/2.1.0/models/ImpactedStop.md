---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# ImpactedStop

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amendedArrivalTime** | **String** |  |  [optional]
**stopPoint** | [**StopPoint**](StopPoint.md) |  |  [optional]
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
Name | Value
---- | -----
DELAYED | &quot;delayed&quot;
ADDED | &quot;added&quot;
DELETED | &quot;deleted&quot;
UNCHANGED | &quot;unchanged&quot;



