# Journey

## Properties

Name | Type | Note
---- | ---- | ----
**duration** | **Int** | Duration of the journey (seconds) 
**nbTransfers** | **Int** | Number of transfers along the journey 
**departureDateTime** | **String** | Departure date and time of the journey [optional] 
**arrivalDateTime** | **String** | Arrival date and time of the journey [optional] 
**requestedDateTime** | **String** | [optional] 
**to** | [**Place**](Place.md) | [optional] 
**from** | [**Place**](Place.md) | [optional] 
**type** | **String** | Used to qualify the journey (can be \"best\", \"comfort\", \"non_pt_walk\", ... 
**status** | **String** | Status from the whole journey taking into account the most disturbing information retrieved on PT object used (can be \"NO_SERVICE\", \"SIGNIFICANT_DELAYS\", ...). A base-schedule journey using a stop-time that is deleted in realtime will have a NO_SERVICE status (no matter the effect of the disruption causing it). 
**tags** | **List<String>** | 
**co2Emission** | [**Amount**](Amount.md) | 
**airPollutants** | [**AirPollutants**](AirPollutants.md) | [optional] 
**lowEmissionZone** | [**LowEmissionZone**](LowEmissionZone.md) | [optional] 
**durations** | [**Durations**](Durations.md) | [optional] 
**distances** | [**Distances**](Distances.md) | [optional] 
**fare** | [**Fare**](Fare.md) | 
**calendars** | [**List<Calendar>**](Calendar.md) | [optional] 
**sections** | [**List<Section>**](Section.md) | [optional] 
**debug** | [**JourneyDebug**](JourneyDebug.md) | [optional] 
**links** | [**List<LinkSchema>**](LinkSchema.md) | [optional] 

