---
layout: default
title: PtObject
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/pt_object
---

# PtObject

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**embeddedType** | [**EmbeddedTypeEnum**](#EmbeddedTypeEnum) |  | 
**stopPoint** | [**StopPoint**](/navitia_sdk_docs/expert/android/endpoints/stop_point) |  |  [optional]
**name** | **String** | Name of the object | 
**route** | [**Route**](/navitia_sdk_docs/expert/android/endpoints/route) |  |  [optional]
**stopArea** | [**StopArea**](/navitia_sdk_docs/expert/android/endpoints/stop_area) |  |  [optional]
**commercialMode** | [**CommercialMode**](/navitia_sdk_docs/expert/android/endpoints/commercial_mode) |  |  [optional]
**id** | **String** | Identifier of the object | 
**line** | [**Line**](/navitia_sdk_docs/expert/android/endpoints/line) |  |  [optional]
**quality** | **Integer** |  |  [optional]
**trip** | [**Trip**](/navitia_sdk_docs/expert/android/endpoints/trip) |  |  [optional]
**network** | [**Network**](/navitia_sdk_docs/expert/android/endpoints/network) |  |  [optional]


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



