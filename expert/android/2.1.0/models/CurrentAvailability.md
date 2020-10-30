---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# CurrentAvailability

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**status** | [**StatusEnum**](#StatusEnum) |  |  [optional]
**effect** | [**Effect**](Effect.md) |  |  [optional]
**cause** | [**Cause**](Cause.md) |  |  [optional]
**periods** | [**List&lt;Period&gt;**](Period.md) |  |  [optional]
**updatedAt** | **String** |  |  [optional]


<a name="StatusEnum"></a>
## Enum: StatusEnum
Name | Value
---- | -----
UNKNOWN | &quot;unknown&quot;
AVAILABLE | &quot;available&quot;
UNAVAILABLE | &quot;unavailable&quot;



