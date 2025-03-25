# JourneysApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatJourneys**](#getcoveragelonlatjourneys) | **GET** coverage/{lon};{lat}/journeys
[**getCoverageRegionJourneys**](#getcoverageregionjourneys) | **GET** coverage/{region}/journeys
[**getJourneys**](#getjourneys) | **GET** journeys

## **getCoverageLonLatJourneys**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**from** | **String** | The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String** | The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **LocalDateTime** | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String** | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Int** | Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Int** | Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**List<String>**](String.md) | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike` [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**lastSectionMode** | [**List<String>**](String.md) | Same as first_section_mode but for the last section. [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**maxDurationToPt** | **Int** | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds [optional] 
**maxWalkingDurationToPt** | **Int** | Maximal duration of walking on public transport in second [optional] 
**maxBikeDurationToPt** | **Int** | Maximal duration of bike on public transport in second [optional] 
**maxBssDurationToPt** | **Int** | Maximal duration of bss on public transport in second [optional] 
**maxCarDurationToPt** | **Int** | Maximal duration of car on public transport in second [optional] 
**maxRidesharingDurationToPt** | **Int** | Maximal duration of ridesharing on public transport in second [optional] 
**maxCarNoParkDurationToPt** | **Int** | Maximal duration of car no park on public transport in second [optional] 
**maxTaxiDurationToPt** | **Int** | Maximal duration of taxi on public transport in second, only available in distributed scenario [optional] 
**walkingSpeed** | **Float** | Walking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bikeSpeed** | **Float** | Biking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bssSpeed** | **Float** | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second [optional] 
**carSpeed** | **Float** | Driving speed for the fallback sections. Speed unit must be in meter/second [optional] 
**ridesharingSpeed** | **Float** | ridesharing speed for the fallback sections. Speed unit must be in meter/second [optional] 
**carNoParkSpeed** | **Float** | Driving speed without car park for the fallback sections. Speed unit must be in meter/second [optional] 
**taxiSpeed** | **Float** | taxi speed speed for the fallback sections. Speed unit must be in meter/second [optional] 
**forbiddenUris** | [**List<String>**](String.md) | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**List<String>**](String.md) | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Boolean** | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime` [optional] 
**dataFreshness** | **String** | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'realtime' - Use all realtime information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule. [optional] [enum: base_schedule, realtime, adapted_schedule] 
**maxDuration** | **Int** | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Boolean** | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String** | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself. [optional] [enum: standard, slow_walker, fast_walker, luggage, wheelchair, cyclist, motorist] 
**directPath** | **String** | Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none, only_with_alternatives] 
**freeRadiusFrom** | **Int** | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0) [optional] 
**freeRadiusTo** | **Int** | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0) [optional] 
**directPathMode** | [**List<String>**](String.md) | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**partnerServices** | [**List<String>**](String.md) | Expose only the partner type into the response. [optional] [enum: ridesharing] 
**additionalTimeAfterFirstSectionTaxi** | **Int** | the additional time added to the taxi section, right after riding the taxi but before hopping on the public transit [optional] 
**additionalTimeBeforeLastSectionTaxi** | **Int** | the additional time added to the taxi section, right before riding the taxi but after hopping off the public transit [optional] 
**criteria** | **String** | choose the criteria used to compute pt journeys, feature in beta  [optional] [enum: classic, robustness, occupancy, arrival_stop_attractivity, departure_stop_attractivity, pseudo_duration] 
**count** | **Int** | Fixed number of different journeys [optional] 
**isJourneySchedules** | **Boolean** | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters [optional] 
**minNbJourneys** | **Int** | Minimum number of different suggested journeys, must be >= 0 [optional] 
**maxNbJourneys** | **Int** | Maximum number of different suggested journeys, must be > 0 [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response [optional] [enum: bss_stands, car_park, , none] 
**timeframeDuration** | **Int** | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter. [optional] 
**language** | **String** | Here, select a specific language for guidance instruction. list available: - nl-NL = dutch - en-US | en-GB = english - fr-FR = french - de-DE = german - hi-IN = hindi - it-IT = italian - ja-JP = japanese - pt-PT = portuguese - ru-RU = russian - es-ES = spanish  [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**equipmentDetails** | **Boolean** | enhance response with accessibility equipement details [optional] [default to True] 
**maxBssDirectPathDuration** | **Int** | limit duration of direct path in bss, used ONLY in distributed scenario [optional] 
**maxCarNoParkDirectPathDuration** | **Int** | limit duration of direct path in car_no_park, used ONLY in distributed scenario [optional] 
**maxCarDirectPathDuration** | **Int** | limit duration of direct path in car, used ONLY in distributed scenario [optional] 
**maxBikeDirectPathDuration** | **Int** | limit duration of direct path in bike, used ONLY in distributed scenario [optional] 
**maxRidesharingDirectPathDuration** | **Int** | limit duration of direct path in ridesharing, used ONLY in distributed scenario [optional] 
**maxWalkingDirectPathDuration** | **Int** | limit duration of direct path in walking, used ONLY in distributed scenario [optional] 
**maxTaxiDirectPathDuration** | **Int** | limit duration of direct path in taxi, used ONLY in distributed scenario [optional] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**maxWaitingDuration** | **Int** | A journey containing a waiting section with a duration greater or equal to  max_waiting_duration will be discarded. Units : seconds. Must be > 0. Default value : 4h [optional] 

### Return
[**Journeys**](../model/Journeys.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().journeysApi.getCoverageLonLatJourneys(
    lon = 0.0,
    lat = 0.0,
    from = "from_example",
    to = "to_example",
    datetime = LocalDateTime.now(),
    datetimeRepresents = "datetimeRepresents_example",
    maxNbTransfers = 123,
    minNbTransfers = 123,
    firstSectionMode = listOf(),
    lastSectionMode = listOf(),
    maxDurationToPt = 123,
    maxWalkingDurationToPt = 123,
    maxBikeDurationToPt = 123,
    maxBssDurationToPt = 123,
    maxCarDurationToPt = 123,
    maxRidesharingDurationToPt = 123,
    maxCarNoParkDurationToPt = 123,
    maxTaxiDurationToPt = 123,
    walkingSpeed = 0f,
    bikeSpeed = 0f,
    bssSpeed = 0f,
    carSpeed = 0f,
    ridesharingSpeed = 0f,
    carNoParkSpeed = 0f,
    taxiSpeed = 0f,
    forbiddenUris = listOf(),
    allowedId = listOf(),
    disruptionActive = true,
    dataFreshness = "dataFreshness_example",
    maxDuration = 123,
    wheelchair = true,
    travelerType = "travelerType_example",
    directPath = "directPath_example",
    freeRadiusFrom = 123,
    freeRadiusTo = 123,
    directPathMode = listOf(),
    partnerServices = listOf(),
    additionalTimeAfterFirstSectionTaxi = 123,
    additionalTimeBeforeLastSectionTaxi = 123,
    criteria = "criteria_example",
    count = 123,
    isJourneySchedules = true,
    minNbJourneys = 123,
    maxNbJourneys = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    timeframeDuration = 123,
    language = "language_example",
    equipmentDetails = true,
    maxBssDirectPathDuration = 123,
    maxCarNoParkDirectPathDuration = 123,
    maxCarDirectPathDuration = 123,
    maxBikeDirectPathDuration = 123,
    maxRidesharingDirectPathDuration = 123,
    maxWalkingDirectPathDuration = 123,
    maxTaxiDirectPathDuration = 123,
    depth = 123,
    maxWaitingDuration = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionJourneys**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**from** | **String** | The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String** | The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **LocalDateTime** | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String** | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Int** | Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Int** | Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**List<String>**](String.md) | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike` [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**lastSectionMode** | [**List<String>**](String.md) | Same as first_section_mode but for the last section. [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**maxDurationToPt** | **Int** | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds [optional] 
**maxWalkingDurationToPt** | **Int** | Maximal duration of walking on public transport in second [optional] 
**maxBikeDurationToPt** | **Int** | Maximal duration of bike on public transport in second [optional] 
**maxBssDurationToPt** | **Int** | Maximal duration of bss on public transport in second [optional] 
**maxCarDurationToPt** | **Int** | Maximal duration of car on public transport in second [optional] 
**maxRidesharingDurationToPt** | **Int** | Maximal duration of ridesharing on public transport in second [optional] 
**maxCarNoParkDurationToPt** | **Int** | Maximal duration of car no park on public transport in second [optional] 
**maxTaxiDurationToPt** | **Int** | Maximal duration of taxi on public transport in second, only available in distributed scenario [optional] 
**walkingSpeed** | **Float** | Walking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bikeSpeed** | **Float** | Biking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bssSpeed** | **Float** | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second [optional] 
**carSpeed** | **Float** | Driving speed for the fallback sections. Speed unit must be in meter/second [optional] 
**ridesharingSpeed** | **Float** | ridesharing speed for the fallback sections. Speed unit must be in meter/second [optional] 
**carNoParkSpeed** | **Float** | Driving speed without car park for the fallback sections. Speed unit must be in meter/second [optional] 
**taxiSpeed** | **Float** | taxi speed speed for the fallback sections. Speed unit must be in meter/second [optional] 
**forbiddenUris** | [**List<String>**](String.md) | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**List<String>**](String.md) | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Boolean** | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime` [optional] 
**dataFreshness** | **String** | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'realtime' - Use all realtime information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule. [optional] [enum: base_schedule, realtime, adapted_schedule] 
**maxDuration** | **Int** | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Boolean** | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String** | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself. [optional] [enum: standard, slow_walker, fast_walker, luggage, wheelchair, cyclist, motorist] 
**directPath** | **String** | Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none, only_with_alternatives] 
**freeRadiusFrom** | **Int** | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0) [optional] 
**freeRadiusTo** | **Int** | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0) [optional] 
**directPathMode** | [**List<String>**](String.md) | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**partnerServices** | [**List<String>**](String.md) | Expose only the partner type into the response. [optional] [enum: ridesharing] 
**additionalTimeAfterFirstSectionTaxi** | **Int** | the additional time added to the taxi section, right after riding the taxi but before hopping on the public transit [optional] 
**additionalTimeBeforeLastSectionTaxi** | **Int** | the additional time added to the taxi section, right before riding the taxi but after hopping off the public transit [optional] 
**criteria** | **String** | choose the criteria used to compute pt journeys, feature in beta  [optional] [enum: classic, robustness, occupancy, arrival_stop_attractivity, departure_stop_attractivity, pseudo_duration] 
**count** | **Int** | Fixed number of different journeys [optional] 
**isJourneySchedules** | **Boolean** | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters [optional] 
**minNbJourneys** | **Int** | Minimum number of different suggested journeys, must be >= 0 [optional] 
**maxNbJourneys** | **Int** | Maximum number of different suggested journeys, must be > 0 [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response [optional] [enum: bss_stands, car_park, , none] 
**timeframeDuration** | **Int** | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter. [optional] 
**language** | **String** | Here, select a specific language for guidance instruction. list available: - nl-NL = dutch - en-US | en-GB = english - fr-FR = french - de-DE = german - hi-IN = hindi - it-IT = italian - ja-JP = japanese - pt-PT = portuguese - ru-RU = russian - es-ES = spanish  [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**equipmentDetails** | **Boolean** | enhance response with accessibility equipement details [optional] [default to True] 
**maxBssDirectPathDuration** | **Int** | limit duration of direct path in bss, used ONLY in distributed scenario [optional] 
**maxCarNoParkDirectPathDuration** | **Int** | limit duration of direct path in car_no_park, used ONLY in distributed scenario [optional] 
**maxCarDirectPathDuration** | **Int** | limit duration of direct path in car, used ONLY in distributed scenario [optional] 
**maxBikeDirectPathDuration** | **Int** | limit duration of direct path in bike, used ONLY in distributed scenario [optional] 
**maxRidesharingDirectPathDuration** | **Int** | limit duration of direct path in ridesharing, used ONLY in distributed scenario [optional] 
**maxWalkingDirectPathDuration** | **Int** | limit duration of direct path in walking, used ONLY in distributed scenario [optional] 
**maxTaxiDirectPathDuration** | **Int** | limit duration of direct path in taxi, used ONLY in distributed scenario [optional] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**maxWaitingDuration** | **Int** | A journey containing a waiting section with a duration greater or equal to  max_waiting_duration will be discarded. Units : seconds. Must be > 0. Default value : 4h [optional] 

### Return
[**Journeys**](../model/Journeys.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().journeysApi.getCoverageRegionJourneys(
    region = "region_example",
    from = "from_example",
    to = "to_example",
    datetime = LocalDateTime.now(),
    datetimeRepresents = "datetimeRepresents_example",
    maxNbTransfers = 123,
    minNbTransfers = 123,
    firstSectionMode = listOf(),
    lastSectionMode = listOf(),
    maxDurationToPt = 123,
    maxWalkingDurationToPt = 123,
    maxBikeDurationToPt = 123,
    maxBssDurationToPt = 123,
    maxCarDurationToPt = 123,
    maxRidesharingDurationToPt = 123,
    maxCarNoParkDurationToPt = 123,
    maxTaxiDurationToPt = 123,
    walkingSpeed = 0f,
    bikeSpeed = 0f,
    bssSpeed = 0f,
    carSpeed = 0f,
    ridesharingSpeed = 0f,
    carNoParkSpeed = 0f,
    taxiSpeed = 0f,
    forbiddenUris = listOf(),
    allowedId = listOf(),
    disruptionActive = true,
    dataFreshness = "dataFreshness_example",
    maxDuration = 123,
    wheelchair = true,
    travelerType = "travelerType_example",
    directPath = "directPath_example",
    freeRadiusFrom = 123,
    freeRadiusTo = 123,
    directPathMode = listOf(),
    partnerServices = listOf(),
    additionalTimeAfterFirstSectionTaxi = 123,
    additionalTimeBeforeLastSectionTaxi = 123,
    criteria = "criteria_example",
    count = 123,
    isJourneySchedules = true,
    minNbJourneys = 123,
    maxNbJourneys = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    timeframeDuration = 123,
    language = "language_example",
    equipmentDetails = true,
    maxBssDirectPathDuration = 123,
    maxCarNoParkDirectPathDuration = 123,
    maxCarDirectPathDuration = 123,
    maxBikeDirectPathDuration = 123,
    maxRidesharingDirectPathDuration = 123,
    maxWalkingDirectPathDuration = 123,
    maxTaxiDirectPathDuration = 123,
    depth = 123,
    maxWaitingDuration = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getJourneys**

### Parameters

Name | Type | Note
---- | ---- | ----
**from** | **String** | The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String** | The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **LocalDateTime** | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String** | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Int** | Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Int** | Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**List<String>**](String.md) | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike` [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**lastSectionMode** | [**List<String>**](String.md) | Same as first_section_mode but for the last section. [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**maxDurationToPt** | **Int** | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds [optional] 
**maxWalkingDurationToPt** | **Int** | Maximal duration of walking on public transport in second [optional] 
**maxBikeDurationToPt** | **Int** | Maximal duration of bike on public transport in second [optional] 
**maxBssDurationToPt** | **Int** | Maximal duration of bss on public transport in second [optional] 
**maxCarDurationToPt** | **Int** | Maximal duration of car on public transport in second [optional] 
**maxRidesharingDurationToPt** | **Int** | Maximal duration of ridesharing on public transport in second [optional] 
**maxCarNoParkDurationToPt** | **Int** | Maximal duration of car no park on public transport in second [optional] 
**maxTaxiDurationToPt** | **Int** | Maximal duration of taxi on public transport in second, only available in distributed scenario [optional] 
**walkingSpeed** | **Float** | Walking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bikeSpeed** | **Float** | Biking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bssSpeed** | **Float** | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second [optional] 
**carSpeed** | **Float** | Driving speed for the fallback sections. Speed unit must be in meter/second [optional] 
**ridesharingSpeed** | **Float** | ridesharing speed for the fallback sections. Speed unit must be in meter/second [optional] 
**carNoParkSpeed** | **Float** | Driving speed without car park for the fallback sections. Speed unit must be in meter/second [optional] 
**taxiSpeed** | **Float** | taxi speed speed for the fallback sections. Speed unit must be in meter/second [optional] 
**forbiddenUris** | [**List<String>**](String.md) | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**List<String>**](String.md) | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Boolean** | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime` [optional] 
**dataFreshness** | **String** | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'realtime' - Use all realtime information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule. [optional] [enum: base_schedule, realtime, adapted_schedule] 
**maxDuration** | **Int** | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Boolean** | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String** | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself. [optional] [enum: standard, slow_walker, fast_walker, luggage, wheelchair, cyclist, motorist] 
**directPath** | **String** | Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none, only_with_alternatives] 
**freeRadiusFrom** | **Int** | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0) [optional] 
**freeRadiusTo** | **Int** | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0) [optional] 
**directPathMode** | [**List<String>**](String.md) | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: bss, car_no_park, car, bike, ridesharing, walking, taxi] 
**partnerServices** | [**List<String>**](String.md) | Expose only the partner type into the response. [optional] [enum: ridesharing] 
**additionalTimeAfterFirstSectionTaxi** | **Int** | the additional time added to the taxi section, right after riding the taxi but before hopping on the public transit [optional] 
**additionalTimeBeforeLastSectionTaxi** | **Int** | the additional time added to the taxi section, right before riding the taxi but after hopping off the public transit [optional] 
**criteria** | **String** | choose the criteria used to compute pt journeys, feature in beta  [optional] [enum: classic, robustness, occupancy, arrival_stop_attractivity, departure_stop_attractivity, pseudo_duration] 
**count** | **Int** | Fixed number of different journeys [optional] 
**isJourneySchedules** | **Boolean** | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters [optional] 
**minNbJourneys** | **Int** | Minimum number of different suggested journeys, must be >= 0 [optional] 
**maxNbJourneys** | **Int** | Maximum number of different suggested journeys, must be > 0 [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response [optional] [enum: bss_stands, car_park, , none] 
**timeframeDuration** | **Int** | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter. [optional] 
**language** | **String** | Here, select a specific language for guidance instruction. list available: - nl-NL = dutch - en-US | en-GB = english - fr-FR = french - de-DE = german - hi-IN = hindi - it-IT = italian - ja-JP = japanese - pt-PT = portuguese - ru-RU = russian - es-ES = spanish  [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**equipmentDetails** | **Boolean** | enhance response with accessibility equipement details [optional] [default to True] 
**maxBssDirectPathDuration** | **Int** | limit duration of direct path in bss, used ONLY in distributed scenario [optional] 
**maxCarNoParkDirectPathDuration** | **Int** | limit duration of direct path in car_no_park, used ONLY in distributed scenario [optional] 
**maxCarDirectPathDuration** | **Int** | limit duration of direct path in car, used ONLY in distributed scenario [optional] 
**maxBikeDirectPathDuration** | **Int** | limit duration of direct path in bike, used ONLY in distributed scenario [optional] 
**maxRidesharingDirectPathDuration** | **Int** | limit duration of direct path in ridesharing, used ONLY in distributed scenario [optional] 
**maxWalkingDirectPathDuration** | **Int** | limit duration of direct path in walking, used ONLY in distributed scenario [optional] 
**maxTaxiDirectPathDuration** | **Int** | limit duration of direct path in taxi, used ONLY in distributed scenario [optional] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**maxWaitingDuration** | **Int** | A journey containing a waiting section with a duration greater or equal to  max_waiting_duration will be discarded. Units : seconds. Must be > 0. Default value : 4h [optional] 

### Return
[**Journeys**](../model/Journeys.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().journeysApi.getJourneys(
    from = "from_example",
    to = "to_example",
    datetime = LocalDateTime.now(),
    datetimeRepresents = "datetimeRepresents_example",
    maxNbTransfers = 123,
    minNbTransfers = 123,
    firstSectionMode = listOf(),
    lastSectionMode = listOf(),
    maxDurationToPt = 123,
    maxWalkingDurationToPt = 123,
    maxBikeDurationToPt = 123,
    maxBssDurationToPt = 123,
    maxCarDurationToPt = 123,
    maxRidesharingDurationToPt = 123,
    maxCarNoParkDurationToPt = 123,
    maxTaxiDurationToPt = 123,
    walkingSpeed = 0f,
    bikeSpeed = 0f,
    bssSpeed = 0f,
    carSpeed = 0f,
    ridesharingSpeed = 0f,
    carNoParkSpeed = 0f,
    taxiSpeed = 0f,
    forbiddenUris = listOf(),
    allowedId = listOf(),
    disruptionActive = true,
    dataFreshness = "dataFreshness_example",
    maxDuration = 123,
    wheelchair = true,
    travelerType = "travelerType_example",
    directPath = "directPath_example",
    freeRadiusFrom = 123,
    freeRadiusTo = 123,
    directPathMode = listOf(),
    partnerServices = listOf(),
    additionalTimeAfterFirstSectionTaxi = 123,
    additionalTimeBeforeLastSectionTaxi = 123,
    criteria = "criteria_example",
    count = 123,
    isJourneySchedules = true,
    minNbJourneys = 123,
    maxNbJourneys = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    timeframeDuration = 123,
    language = "language_example",
    equipmentDetails = true,
    maxBssDirectPathDuration = 123,
    maxCarNoParkDirectPathDuration = 123,
    maxCarDirectPathDuration = 123,
    maxBikeDirectPathDuration = 123,
    maxRidesharingDirectPathDuration = 123,
    maxWalkingDirectPathDuration = 123,
    maxTaxiDirectPathDuration = 123,
    depth = 123,
    maxWaitingDuration = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

