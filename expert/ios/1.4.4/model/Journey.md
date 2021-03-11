---
layout: main
title: Journey
nav_exclude: true
permalink: /expert/ios/model/Journey
---

# Journey

---

## Properties

Name | Type | Note
---- | ---- | ----
**status** | **String** | Status from the whole journey taking into account the most disturbing information retrieved on every object used (can be \&quot;NO_SERVICE\&quot;, \&quot;SIGNIFICANT_DELAYS\&quot;, ... 
**distances** | [**Distances**](Distances.md) | [optional] 
**from** | [**Place**](Place.md) | [optional] 
**links** | [**[LinkSchema]**](LinkSchema.md) | [optional] 
**tags** | **[String]** | 
**nbTransfers** | **Int** | Number of transfers along the journey 
**durations** | [**Durations**](Durations.md) | [optional] 
**arrivalDateTime** | **String** | Arrival date and time of the journey [optional] 
**calendars** | [**[Calendar]**](Calendar.md) | [optional] 
**departureDateTime** | **String** | Departure date and time of the journey [optional] 
**to** | [**Place**](Place.md) | [optional] 
**requestedDateTime** | **String** | [optional] 
**fare** | [**Fare**](Fare.md) | 
**co2Emission** | [**Amount**](Amount.md) | 
**type** | **String** | Used to qualify the journey (can be \&quot;best\&quot;, \&quot;comfort\&quot;, \&quot;non_pt_walk\&quot;, ... 
**duration** | **Int** | Duration of the journey (seconds) 
**sections** | [**[Section]**](Section.md) | [optional] 
**debug** | [**JourneyDebug**](JourneyDebug.md) | [optional] 

