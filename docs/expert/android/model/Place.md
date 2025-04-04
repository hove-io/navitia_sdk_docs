# Place

## Properties

Name | Type | Note
---- | ---- | ----
**id** | **String** | Identifier of the object 
**name** | **String** | Name of the object 
**quality** | **Int** | [optional] 
**stopArea** | [**StopArea**](StopArea.md) | [optional] 
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**administrativeRegion** | [**Admin**](Admin.md) | [optional] 
**embeddedType** | [**EmbeddedType**](#EmbeddedType) | 
**address** | [**Address**](Address.md) | [optional] 
**poi** | [**Poi**](Poi.md) | [optional] 
**accessPoint** | [**PathWay**](PathWay.md) | [optional] 
**distance** | **String** | Distance to the object in meters [optional] 

## EmbeddedType

Name | Value
---- | -----
LINE | "line"
JOURNEY_PATTERN | "journey_pattern"
VEHICLE_JOURNEY | "vehicle_journey"
STOP_POINT | "stop_point"
STOP_AREA | "stop_area"
NETWORK | "network"
PHYSICAL_MODE | "physical_mode"
COMMERCIAL_MODE | "commercial_mode"
CONNECTION | "connection"
JOURNEY_PATTERN_POINT | "journey_pattern_point"
COMPANY | "company"
ROUTE | "route"
POI | "poi"
CONTRIBUTOR | "contributor"
ADDRESS | "address"
POITYPE | "poitype"
ADMINISTRATIVE_REGION | "administrative_region"
CALENDAR | "calendar"
LINE_GROUP | "line_group"
IMPACT | "impact"
DATASET | "dataset"
TRIP | "trip"
ACCESS_POINT | "access_point"

