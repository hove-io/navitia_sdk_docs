---
layout: default
title: StopPoint
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/stop_point
---

# StopPoint

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**comment** | **String** |  |  [optional]
**commercialModes** | [**List&lt;CommercialMode&gt;**](/navitia_sdk_docs/expert/android/endpoints/commercial_mode) |  |  [optional]
**stopArea** | [**StopArea**](/navitia_sdk_docs/expert/android/endpoints/stop_area) |  |  [optional]
**links** | [**List&lt;LinkSchema&gt;**](/navitia_sdk_docs/expert/android/endpoints/link_schema) |  | 
**administrativeRegions** | [**List&lt;Admin&gt;**](/navitia_sdk_docs/expert/android/endpoints/admin) |  |  [optional]
**physicalModes** | [**List&lt;PhysicalMode&gt;**](/navitia_sdk_docs/expert/android/endpoints/physical_mode) |  |  [optional]
**comments** | [**List&lt;Comment&gt;**](/navitia_sdk_docs/expert/android/endpoints/comment) |  |  [optional]
**label** | **String** |  |  [optional]
**equipments** | [**List&lt;EquipmentsEnum&gt;**](#List&lt;EquipmentsEnum&gt;) |  | 
**codes** | [**List&lt;Code&gt;**](/navitia_sdk_docs/expert/android/endpoints/code) |  |  [optional]
**coord** | [**Coord**](/navitia_sdk_docs/expert/android/endpoints/coord) |  |  [optional]
**equipmentDetails** | [**List&lt;EquipmentDetails&gt;**](/navitia_sdk_docs/expert/android/endpoints/equipment_details) |  |  [optional]
**address** | [**Address**](/navitia_sdk_docs/expert/android/endpoints/address) |  |  [optional]
**fareZone** | [**FareZone**](/navitia_sdk_docs/expert/android/endpoints/fare_zone) |  |  [optional]
**id** | **String** | Identifier of the object | 
**name** | **String** | Name of the object | 


<a name="List<EquipmentsEnum>"></a>
## Enum: List&lt;EquipmentsEnum&gt;
| Name | Value
| ---- | -----
WHEELCHAIR_ACCESSIBILITY | &quot;has_wheelchair_accessibility&quot;
BIKE_ACCEPTED | &quot;has_bike_accepted&quot;
AIR_CONDITIONED | &quot;has_air_conditioned&quot;
VISUAL_ANNOUNCEMENT | &quot;has_visual_announcement&quot;
AUDIBLE_ANNOUNCEMENT | &quot;has_audible_announcement&quot;
APPROPRIATE_ESCORT | &quot;has_appropriate_escort&quot;
APPROPRIATE_SIGNAGE | &quot;has_appropriate_signage&quot;
SCHOOL_VEHICLE | &quot;has_school_vehicle&quot;
WHEELCHAIR_BOARDING | &quot;has_wheelchair_boarding&quot;
SHELTERED | &quot;has_sheltered&quot;
ELEVATOR | &quot;has_elevator&quot;
ESCALATOR | &quot;has_escalator&quot;
BIKE_DEPOT | &quot;has_bike_depot&quot;



