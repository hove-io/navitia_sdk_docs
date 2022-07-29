# StopDateTime

## Properties

Name | Type | Note
---- | ---- | ----
**stopPoint** | [**StopPoint**](StopPoint.md) | [optional] 
**links** | [**List<LinkSchema>**](LinkSchema.md) | 
**arrivalDateTime** | **String** | [optional] 
**additionalInformations** | [**List<AdditionalInformations>**](#AdditionalInformations) | 
**departureDateTime** | **String** | [optional] 
**baseArrivalDateTime** | **String** | [optional] 
**baseDepartureDateTime** | **String** | [optional] 
**dataFreshness** | [**DataFreshness**](#DataFreshness) | [optional] 

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

