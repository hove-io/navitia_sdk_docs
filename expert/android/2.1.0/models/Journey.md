---
layout: default
title: Journey
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/journey
---

# Journey

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**status** | **String** | Status from the whole journey taking into account the most disturbing information retrieved on every object used (can be \&quot;NO_SERVICE\&quot;, \&quot;SIGNIFICANT_DELAYS\&quot;, ... | 
**distances** | [**Distances**](/navitia_sdk_docs/expert/android/endpoints/distances) |  |  [optional]
**from** | [**Place**](/navitia_sdk_docs/expert/android/endpoints/place) |  |  [optional]
**links** | [**List&lt;LinkSchema&gt;**](/navitia_sdk_docs/expert/android/endpoints/link_schema) |  |  [optional]
**tags** | **List&lt;String&gt;** |  | 
**nbTransfers** | **Integer** | Number of transfers along the journey | 
**durations** | [**Durations**](/navitia_sdk_docs/expert/android/endpoints/durations) |  |  [optional]
**arrivalDateTime** | **String** | Arrival date and time of the journey |  [optional]
**calendars** | [**List&lt;Calendar&gt;**](/navitia_sdk_docs/expert/android/endpoints/calendar) |  |  [optional]
**departureDateTime** | **String** | Departure date and time of the journey |  [optional]
**to** | [**Place**](/navitia_sdk_docs/expert/android/endpoints/place) |  |  [optional]
**requestedDateTime** | **String** |  |  [optional]
**fare** | [**Fare**](/navitia_sdk_docs/expert/android/endpoints/fare) |  | 
**co2Emission** | [**Amount**](/navitia_sdk_docs/expert/android/endpoints/amount) |  | 
**type** | **String** | Used to qualify the journey (can be \&quot;best\&quot;, \&quot;comfort\&quot;, \&quot;non_pt_walk\&quot;, ... | 
**duration** | **Integer** | Duration of the journey (seconds) | 
**sections** | [**List&lt;Section&gt;**](/navitia_sdk_docs/expert/android/endpoints/section) |  |  [optional]
**debug** | [**JourneyDebug**](/navitia_sdk_docs/expert/android/endpoints/journey_debug) |  |  [optional]



