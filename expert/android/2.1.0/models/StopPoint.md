---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# StopPoint

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**comment** | **String** |  |  [optional]
**commercialModes** | [**List&lt;CommercialMode&gt;**](CommercialMode.md) |  |  [optional]
**stopArea** | [**StopArea**](StopArea.md) |  |  [optional]
**links** | [**List&lt;LinkSchema&gt;**](LinkSchema.md) |  | 
**administrativeRegions** | [**List&lt;Admin&gt;**](Admin.md) |  |  [optional]
**physicalModes** | [**List&lt;PhysicalMode&gt;**](PhysicalMode.md) |  |  [optional]
**comments** | [**List&lt;Comment&gt;**](Comment.md) |  |  [optional]
**label** | **String** |  |  [optional]
**equipments** | [**List&lt;EquipmentsEnum&gt;**](#List&lt;EquipmentsEnum&gt;) |  | 
**codes** | [**List&lt;Code&gt;**](Code.md) |  |  [optional]
**coord** | [**Coord**](Coord.md) |  |  [optional]
**equipmentDetails** | [**List&lt;EquipmentDetails&gt;**](EquipmentDetails.md) |  |  [optional]
**address** | [**Address**](Address.md) |  |  [optional]
**fareZone** | [**FareZone**](FareZone.md) |  |  [optional]
**id** | **String** | Identifier of the object | 
**name** | **String** | Name of the object | 


<a name="List<EquipmentsEnum>"></a>
## Enum: List&lt;EquipmentsEnum&gt;
Name | Value
---- | -----
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



