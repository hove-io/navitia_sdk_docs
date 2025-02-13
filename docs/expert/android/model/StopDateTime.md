# StopDateTime

## Properties

Name | Type | Note
---- | ---- | ----
**departureDateTime** | **String** | [optional] 
**baseDepartureDateTime** | **String** | [optional] 
**arrivalDateTime** | **String** | [optional] 
**baseArrivalDateTime** | **String** | [optional] 
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**additionalInformations** | [**List<AdditionalInformations>**](#AdditionalInformations) | 
**links** | [**List<LinkSchema>**](LinkSchema.md) | 
**dataFreshness** | [**DataFreshness**](#DataFreshness) | [optional] 
**departureOccupancy** | [**DepartureOccupancy**](#DepartureOccupancy) | [optional] 

## AdditionalInformations

Name | Value
---- | -----
PICK_UP_ONLY | "pick_up_only"
DROP_OFF_ONLY | "drop_off_only"
ON_DEMAND_TRANSPORT | "on_demand_transport"
DATE_TIME_ESTIMATED | "date_time_estimated"
SKIPPED_STOP | "skipped_stop"

## DataFreshness

Name | Value
---- | -----
BASE_SCHEDULE | "base_schedule"
ADAPTED_SCHEDULE | "adapted_schedule"
REALTIME | "realtime"

## DepartureOccupancy

Name | Value
---- | -----
EMPTY | "empty"
MANY_SEATS_AVAILABLE | "many_seats_available"
FEW_SEATS_AVAILABLE | "few_seats_available"
STANDING_ROOM_ONLY | "standing_room_only"
CRUSHED_STANDING_ROOM_ONLY | "crushed_standing_room_only"
FULL | "full"
NOT_ACCEPTING_PASSENGERS | "not_accepting_passengers"

