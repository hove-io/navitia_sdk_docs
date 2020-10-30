---
layout: default
title: CurrentAvailability
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/current_availability
---

# CurrentAvailability

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**status** | [**StatusEnum**](#StatusEnum) |  |  [optional]
**effect** | [**Effect**](/navitia_sdk_docs/expert/android/endpoints/effect) |  |  [optional]
**cause** | [**Cause**](/navitia_sdk_docs/expert/android/endpoints/cause) |  |  [optional]
**periods** | [**List&lt;Period&gt;**](/navitia_sdk_docs/expert/android/endpoints/period) |  |  [optional]
**updatedAt** | **String** |  |  [optional]


<a name="StatusEnum"></a>
## Enum: StatusEnum
| Name | Value
| ---- | -----
UNKNOWN | &quot;unknown&quot;
AVAILABLE | &quot;available&quot;
UNAVAILABLE | &quot;unavailable&quot;



