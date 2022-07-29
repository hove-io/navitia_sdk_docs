# Section

## Properties

Name | Type | Note
---- | ---- | ----
**links** | [**List<LinkSchema>**](LinkSchema.md) | 
**departureDateTime** | **String** | Departure date and time of the section [optional] 
**baseDepartureDateTime** | **String** | Base-schedule departure date and time of the section [optional] 
**dataFreshness** | [**DataFreshness**](#DataFreshness) | [optional] 
**duration** | **Int** | Duration of the section (seconds) 
**id** | **String** | 
**from** | [**Place**](Place.md) | [optional] 
**arrivalDateTime** | **String** | Arrival date and time of the section [optional] 
**additionalInformations** | [**List<AdditionalInformations>**](#AdditionalInformations) | [optional] 
**geojson** | [**SectionGeoJsonSchema**](SectionGeoJsonSchema.md) | GeoJSON of the shape of the section [optional] 
**ridesharingInformations** | [**RidesharingInformation**](RidesharingInformation.md) | [optional] 
**to** | [**Place**](Place.md) | [optional] 
**baseArrivalDateTime** | **String** | Base-schedule arrival date and time of the section [optional] 
**transferType** | [**TransferType**](#TransferType) | [optional] 
**type** | [**Type**](#Type) | [optional] 
**streetInformations** | [**List<StreetInformation>**](StreetInformation.md) | [optional] 
**dynamicSpeeds** | [**List<DynamicSpeed>**](DynamicSpeed.md) | [optional] 
**co2Emission** | [**Amount**](Amount.md) | 
**path** | [**List<Path>**](Path.md) | [optional] 
**cycleLaneLength** | **Int** | [optional] 
**elevations** | [**List<Elevation>**](Elevation.md) | [optional] 
**displayInformations** | [**VJDisplayInformation**](VJDisplayInformation.md) | [optional] 
**mode** | [**Mode**](#Mode) | [optional] 
**ridesharingJourneys** | [**List<Journey>**](Journey.md) | [optional] 
**vias** | [**List<PathWay>**](PathWay.md) | [optional] 
**stopDateTimes** | [**List<StopDateTime>**](StopDateTime.md) | [optional] 

## DataFreshness

Name | Value
---- | -----
BASE_SCHEDULE | "base_schedule"
ADAPTED_SCHEDULE | "adapted_schedule"
REALTIME | "realtime"

## AdditionalInformations

Name | Value
---- | -----
ODT_WITH_ZONE | "odt_with_zone"
ODT_WITH_STOP_POINT | "odt_with_stop_point"
ODT_WITH_STOP_TIME | "odt_with_stop_time"
HAS_DATETIME_ESTIMATED | "has_datetime_estimated"
REGULAR | "regular"
STAY_IN | "stay_in"

## TransferType

Name | Value
---- | -----
WALKING | "walking"
STAY_IN | "stay_in"

## Type

Name | Value
---- | -----
PUBLIC_TRANSPORT | "public_transport"
STREET_NETWORK | "street_network"
WAITING | "waiting"
TRANSFER | "transfer"
BOARDING | "boarding"
LANDING | "landing"
BSS_RENT | "bss_rent"
BSS_PUT_BACK | "bss_put_back"
CROW_FLY | "crow_fly"
PARK | "park"
LEAVE_PARKING | "leave_parking"
ALIGHTING | "alighting"
RIDESHARING | "ridesharing"
ON_DEMAND_TRANSPORT | "on_demand_transport"

## Mode

Name | Value
---- | -----
WALKING | "walking"
BIKE | "bike"
CAR | "car"
BSS | "bss"
RIDESHARING | "ridesharing"
CARNOPARK | "carnopark"
TAXI | "taxi"

