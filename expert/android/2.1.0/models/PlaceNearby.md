---
layout: default
title: PlaceNearby
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/place_nearby
---

# PlaceNearby

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**embeddedType** | [**EmbeddedTypeEnum**](#EmbeddedTypeEnum) |  | 
**stopPoint** | [**StopPoint**](/navitia_sdk_docs/expert/android/endpoints/stop_point) |  |  [optional]
**administrativeRegion** | [**Admin**](/navitia_sdk_docs/expert/android/endpoints/admin) |  |  [optional]
**name** | **String** | Name of the object | 
**distance** | **String** | Distance to the object in meters |  [optional]
**poi** | [**Poi**](/navitia_sdk_docs/expert/android/endpoints/poi) |  |  [optional]
**address** | [**Address**](/navitia_sdk_docs/expert/android/endpoints/address) |  |  [optional]
**quality** | **Integer** |  |  [optional]
**id** | **String** | Identifier of the object | 
**stopArea** | [**StopArea**](/navitia_sdk_docs/expert/android/endpoints/stop_area) |  |  [optional]


<a name="EmbeddedTypeEnum"></a>
## Enum: EmbeddedTypeEnum
| Name | Value
| ---- | -----
LINE | &quot;line&quot;
JOURNEY_PATTERN | &quot;journey_pattern&quot;
VEHICLE_JOURNEY | &quot;vehicle_journey&quot;
STOP_POINT | &quot;stop_point&quot;
STOP_AREA | &quot;stop_area&quot;
NETWORK | &quot;network&quot;
PHYSICAL_MODE | &quot;physical_mode&quot;
COMMERCIAL_MODE | &quot;commercial_mode&quot;
CONNECTION | &quot;connection&quot;
JOURNEY_PATTERN_POINT | &quot;journey_pattern_point&quot;
COMPANY | &quot;company&quot;
ROUTE | &quot;route&quot;
POI | &quot;poi&quot;
CONTRIBUTOR | &quot;contributor&quot;
ADDRESS | &quot;address&quot;
POITYPE | &quot;poitype&quot;
ADMINISTRATIVE_REGION | &quot;administrative_region&quot;
CALENDAR | &quot;calendar&quot;
LINE_GROUP | &quot;line_group&quot;
IMPACT | &quot;impact&quot;
DATASET | &quot;dataset&quot;
TRIP | &quot;trip&quot;



