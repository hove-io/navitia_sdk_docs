# HeatMapAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatHeatMaps**](#getCoverageLonLatHeatMaps) | **GET** /coverage/{lon};{lat}/heat_maps
[**getCoverageRegionHeatMaps**](#getCoverageRegionHeatMaps) | **GET** /coverage/{region}/heat_maps

## **getCoverageLonLatHeatMaps**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**from** | **String** | The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String** | The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **Date** | Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String** | Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Int** | Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Int** | Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**[String]**](String.md) | Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**lastSectionMode** | [**[String]**](String.md) | Same as first_section_mode but for the last section. [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
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
**forbiddenUris** | [**[String]**](String.md) | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**[String]**](String.md) | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Bool** | DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; [optional] 
**dataFreshness** | **String** | Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information [optional] [enum: base_schedule, adapted_schedule, realtime] 
**maxDuration** | **Int** | Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Bool** | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String** | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker] 
**directPath** | **String** | Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none, only_with_alternatives] 
**freeRadiusFrom** | **Int** | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**freeRadiusTo** | **Int** | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**directPathMode** | [**[String]**](String.md) | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**partnerServices** | [**[String]**](String.md) | Expose only the partner type into the response. [optional] [enum: ridesharing] 
**additionalTimeAfterFirstSectionTaxi** | **Int** | the additional time added to the taxi section, right after riding the taxi but before hopping on the public transit [optional] 
**additionalTimeBeforeLastSectionTaxi** | **Int** | the additional time added to the taxi section, right before riding the taxi but after hopping off the public transit [optional] 
**resolution** | **Int** | Sampling resolution [optional] [default to 500] 

### Return
[**HeatMap1**](../model/HeatMap1.md)


<h3>Example</h3>
```swift
Expert.shared.heatMapApi.getCoverageLonLatHeatMaps(
    lat: 3.4, 
    lon: 3.4, 
    from: "from_example", 
    to: "to_example", 
    datetime: Date(), 
    datetimeRepresents: "departure", 
    maxNbTransfers: 56, 
    minNbTransfers: 56, 
    firstSectionMode: ["firstSectionMode_example"], 
    lastSectionMode: ["lastSectionMode_example"], 
    maxDurationToPt: 56, 
    maxWalkingDurationToPt: 56, 
    maxBikeDurationToPt: 56, 
    maxBssDurationToPt: 56, 
    maxCarDurationToPt: 56, 
    maxRidesharingDurationToPt: 56, 
    maxCarNoParkDurationToPt: 56, 
    maxTaxiDurationToPt: 56, 
    walkingSpeed: 3.4, 
    bikeSpeed: 3.4, 
    bssSpeed: 3.4, 
    carSpeed: 3.4, 
    ridesharingSpeed: 3.4, 
    carNoParkSpeed: 3.4, 
    taxiSpeed: 3.4, 
    forbiddenUris: ["forbiddenUris_example"], 
    allowedId: ["allowedId_example"], 
    disruptionActive: true, 
    dataFreshness: "dataFreshness_example", 
    maxDuration: 56, 
    wheelchair: true, 
    travelerType: "travelerType_example", 
    directPath: "indifferent", 
    freeRadiusFrom: 56, 
    freeRadiusTo: 56, 
    directPathMode: ["directPathMode_example"], 
    partnerServices: ["partnerServices_example"], 
    additionalTimeAfterFirstSectionTaxi: 56, 
    additionalTimeBeforeLastSectionTaxi: 56, 
    resolution: 500
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionHeatMaps**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**from** | **String** | The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String** | The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **Date** | Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String** | Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Int** | Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Int** | Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**[String]**](String.md) | Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**lastSectionMode** | [**[String]**](String.md) | Same as first_section_mode but for the last section. [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
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
**forbiddenUris** | [**[String]**](String.md) | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**[String]**](String.md) | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Bool** | DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; [optional] 
**dataFreshness** | **String** | Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information [optional] [enum: base_schedule, adapted_schedule, realtime] 
**maxDuration** | **Int** | Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Bool** | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String** | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker] 
**directPath** | **String** | Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none, only_with_alternatives] 
**freeRadiusFrom** | **Int** | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**freeRadiusTo** | **Int** | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**directPathMode** | [**[String]**](String.md) | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**partnerServices** | [**[String]**](String.md) | Expose only the partner type into the response. [optional] [enum: ridesharing] 
**additionalTimeAfterFirstSectionTaxi** | **Int** | the additional time added to the taxi section, right after riding the taxi but before hopping on the public transit [optional] 
**additionalTimeBeforeLastSectionTaxi** | **Int** | the additional time added to the taxi section, right before riding the taxi but after hopping off the public transit [optional] 
**resolution** | **Int** | Sampling resolution [optional] [default to 500] 

### Return
[**HeatMap1**](../model/HeatMap1.md)


<h3>Example</h3>
```swift
Expert.shared.heatMapApi.getCoverageRegionHeatMaps(
    region: "region_example", 
    from: "from_example", 
    to: "to_example", 
    datetime: Date(), 
    datetimeRepresents: "departure", 
    maxNbTransfers: 56, 
    minNbTransfers: 56, 
    firstSectionMode: ["firstSectionMode_example"], 
    lastSectionMode: ["lastSectionMode_example"], 
    maxDurationToPt: 56, 
    maxWalkingDurationToPt: 56, 
    maxBikeDurationToPt: 56, 
    maxBssDurationToPt: 56, 
    maxCarDurationToPt: 56, 
    maxRidesharingDurationToPt: 56, 
    maxCarNoParkDurationToPt: 56, 
    maxTaxiDurationToPt: 56, 
    walkingSpeed: 3.4, 
    bikeSpeed: 3.4, 
    bssSpeed: 3.4, 
    carSpeed: 3.4, 
    ridesharingSpeed: 3.4, 
    carNoParkSpeed: 3.4, 
    taxiSpeed: 3.4, 
    forbiddenUris: ["forbiddenUris_example"], 
    allowedId: ["allowedId_example"], 
    disruptionActive: true, 
    dataFreshness: "dataFreshness_example", 
    maxDuration: 56, 
    wheelchair: true, 
    travelerType: "travelerType_example", 
    directPath: "indifferent", 
    freeRadiusFrom: 56, 
    freeRadiusTo: 56, 
    directPathMode: ["directPathMode_example"], 
    partnerServices: ["partnerServices_example"], 
    additionalTimeAfterFirstSectionTaxi: 56, 
    additionalTimeBeforeLastSectionTaxi: 56, 
    resolution: 500
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

