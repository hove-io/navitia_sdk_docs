# Journey

## Properties

Name | Type | Note
---- | ---- | ----
**status** | **String** | Status from the whole journey taking into account the most disturbing information retrieved on every object used (can be \"NO_SERVICE\", \"SIGNIFICANT_DELAYS\", ... 
**distances** | [**Distances**](Distances.md) | [optional] 
**from** | [**Place**](Place.md) | [optional] 
**links** | [**List<LinkSchema>**](LinkSchema.md) | [optional] 
**tags** | **List<String>** | 
**nbTransfers** | **Int** | Number of transfers along the journey 
**durations** | [**Durations**](Durations.md) | [optional] 
**arrivalDateTime** | **String** | Arrival date and time of the journey [optional] 
**calendars** | [**List<Calendar>**](Calendar.md) | [optional] 
**departureDateTime** | **String** | Departure date and time of the journey [optional] 
**to** | [**Place**](Place.md) | [optional] 
**requestedDateTime** | **String** | [optional] 
**fare** | [**Fare**](Fare.md) | 
**co2Emission** | [**Amount**](Amount.md) | 
**type** | **String** | Used to qualify the journey (can be \"best\", \"comfort\", \"non_pt_walk\", ... 
**duration** | **Int** | Duration of the journey (seconds) 
**sections** | [**List<Section>**](Section.md) | [optional] 
**debug** | [**JourneyDebug**](JourneyDebug.md) | [optional] 

