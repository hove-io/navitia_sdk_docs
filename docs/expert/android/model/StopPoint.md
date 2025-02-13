# StopPoint

## Properties

Name | Type | Note
---- | ---- | ----
**id** | **String** | Identifier of the object 
**name** | **String** | Name of the object 
**comments** | [**List<Comment>**](Comment.md) | [optional] 
**comment** | **String** | [optional] 
**codes** | [**List<Code>**](Code.md) | [optional] 
**label** | **String** | [optional] 
**coord** | [**Coord**](Coord.md) | [optional] 
**links** | [**List<LinkSchema>**](LinkSchema.md) | 
**commercialModes** | [**List<CommercialMode>**](CommercialMode.md) | [optional] 
**physicalModes** | [**List<PhysicalMode>**](PhysicalMode.md) | [optional] 
**administrativeRegions** | [**List<Admin>**](Admin.md) | [optional] 
**stopArea** | [**StopArea**](StopArea.md) | [optional] 
**equipments** | [**List<Equipments>**](#Equipments) | 
**address** | [**Address**](Address.md) | [optional] 
**fareZone** | [**FareZone**](FareZone.md) | [optional] 
**equipmentDetails** | [**List<EquipmentDetails>**](EquipmentDetails.md) | [optional] 
**lines** | [**List<Line>**](Line.md) | [optional] 
**accessPoints** | [**List<PathWay>**](PathWay.md) | [optional] 

## Equipments

Name | Value
---- | -----
WHEELCHAIR_ACCESSIBILITY | "has_wheelchair_accessibility"
BIKE_ACCEPTED | "has_bike_accepted"
AIR_CONDITIONED | "has_air_conditioned"
VISUAL_ANNOUNCEMENT | "has_visual_announcement"
AUDIBLE_ANNOUNCEMENT | "has_audible_announcement"
APPROPRIATE_ESCORT | "has_appropriate_escort"
APPROPRIATE_SIGNAGE | "has_appropriate_signage"
SCHOOL_VEHICLE | "has_school_vehicle"
WHEELCHAIR_BOARDING | "has_wheelchair_boarding"
SHELTERED | "has_sheltered"
ELEVATOR | "has_elevator"
ESCALATOR | "has_escalator"
BIKE_DEPOT | "has_bike_depot"

