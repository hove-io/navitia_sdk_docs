---
layout: main
title: GraphicalIsochroneApi
nav_exclude: true
permalink: /expert/android/api/GraphicalIsochroneApi
---

# GraphicalIsochroneApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatIsochrones**](#getCoverageLonLatIsochrones) | **GET** /coverage/{lon};{lat}/isochrones
[**getCoverageRegionIsochrones**](#getCoverageRegionIsochrones) | **GET** /coverage/{region}/isochrones

## **getCoverageLonLatIsochrones**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**from** | **String**| The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String**| The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **DateTime**| Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String**| Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Integer**| Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Integer**| Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**List&lt;String&gt;**](String.md)| Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**lastSectionMode** | [**List&lt;String&gt;**](String.md)| Same as first_section_mode but for the last section. [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**maxDurationToPt** | **Integer**| Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds [optional] 
**maxWalkingDurationToPt** | **Integer**| Maximal duration of walking on public transport in second [optional] 
**maxBikeDurationToPt** | **Integer**| Maximal duration of bike on public transport in second [optional] 
**maxBssDurationToPt** | **Integer**| Maximal duration of bss on public transport in second [optional] 
**maxCarDurationToPt** | **Integer**| Maximal duration of car on public transport in second [optional] 
**maxRidesharingDurationToPt** | **Integer**| Maximal duration of ridesharing on public transport in second [optional] 
**maxCarNoParkDurationToPt** | **Integer**| Maximal duration of car no park on public transport in second [optional] 
**maxTaxiDurationToPt** | **Integer**| Maximal duration of taxi on public transport in second, only available in distributed scenario [optional] 
**walkingSpeed** | **Float**| Walking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bikeSpeed** | **Float**| Biking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bssSpeed** | **Float**| Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second [optional] 
**carSpeed** | **Float**| Driving speed for the fallback sections. Speed unit must be in meter/second [optional] 
**ridesharingSpeed** | **Float**| ridesharing speed for the fallback sections. Speed unit must be in meter/second [optional] 
**carNoParkSpeed** | **Float**| Driving speed without car park for the fallback sections. Speed unit must be in meter/second [optional] 
**taxiSpeed** | **Float**| taxi speed speed for the fallback sections. Speed unit must be in meter/second [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**List&lt;String&gt;**](String.md)| If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Boolean**| DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; [optional] 
**dataFreshness** | **String**| Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information [optional] [enum: base_schedule, adapted_schedule, realtime] 
**maxDuration** | **Integer**| Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Boolean**| If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String**| Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker] 
**directPath** | **String**| Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none] 
**freeRadiusFrom** | **Integer**| Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**freeRadiusTo** | **Integer**| Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**directPathMode** | [**List&lt;String&gt;**](String.md)| Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**partnerServices** | [**List&lt;String&gt;**](String.md)| Expose only the partner type into the response. [optional] [enum: ridesharing] 
**minDuration** | **Integer**| Minimum travel duration [optional] 
**boundaryDuration** | [**List&lt;Integer&gt;**](Integer.md)| To provide multiple duration parameters [optional] 

### Return
[**GraphicalIsrochone1**](../model/GraphicalIsrochone1)

### Example
```kotlin
navitiaSdk.graphicalIsochroneApi.newCoverageLonLatIsochronesRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withFrom("from_example")
    .withTo("to_example")
    .withDatetime(DateTime())
    .withDatetimeRepresents("departure")
    .withMaxNbTransfers(56)
    .withMinNbTransfers(56)
    .withFirstSectionMode(listOf("firstSectionMode_example"))
    .withLastSectionMode(listOf("lastSectionMode_example"))
    .withMaxDurationToPt(56)
    .withMaxWalkingDurationToPt(56)
    .withMaxBikeDurationToPt(56)
    .withMaxBssDurationToPt(56)
    .withMaxCarDurationToPt(56)
    .withMaxRidesharingDurationToPt(56)
    .withMaxCarNoParkDurationToPt(56)
    .withMaxTaxiDurationToPt(56)
    .withWalkingSpeed(3.4f)
    .withBikeSpeed(3.4f)
    .withBssSpeed(3.4f)
    .withCarSpeed(3.4f)
    .withRidesharingSpeed(3.4f)
    .withCarNoParkSpeed(3.4f)
    .withTaxiSpeed(3.4f)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withAllowedId(listOf("allowedId_example"))
    .withDisruptionActive(true)
    .withDataFreshness("dataFreshness_example")
    .withMaxDuration(56)
    .withWheelchair(true)
    .withTravelerType("travelerType_example")
    .withDirectPath("indifferent")
    .withFreeRadiusFrom(56)
    .withFreeRadiusTo(56)
    .withDirectPathMode(listOf("directPathMode_example"))
    .withPartnerServices(listOf("partnerServices_example"))
    .withMinDuration(56)
    .withBoundaryDuration(listOf(56))
    .get(object : ApiCallback<T> {
        override fun onSuccess(
            result: T,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Success result
        }

        override fun onFailure(
            e: ApiException?,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Failure result
        }

        override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            // Progress upload
        }

        override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            // Progress download
        }
    })
```

## **getCoverageRegionIsochrones**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**from** | **String**| The id of the departure of your journey. If not provided an isochrone is computed. [optional] 
**to** | **String**| The id of the arrival of your journey. If not provided an isochrone is computed. [optional] 
**datetime** | **DateTime**| Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. [optional] 
**datetimeRepresents** | **String**| Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime [optional] [default to departure] [enum: arrival, departure] 
**maxNbTransfers** | **Integer**| Maximum number of transfers in each journey [optional] 
**minNbTransfers** | **Integer**| Minimum number of transfers in each journey [optional] 
**firstSectionMode** | [**List&lt;String&gt;**](String.md)| Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**lastSectionMode** | [**List&lt;String&gt;**](String.md)| Same as first_section_mode but for the last section. [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**maxDurationToPt** | **Integer**| Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds [optional] 
**maxWalkingDurationToPt** | **Integer**| Maximal duration of walking on public transport in second [optional] 
**maxBikeDurationToPt** | **Integer**| Maximal duration of bike on public transport in second [optional] 
**maxBssDurationToPt** | **Integer**| Maximal duration of bss on public transport in second [optional] 
**maxCarDurationToPt** | **Integer**| Maximal duration of car on public transport in second [optional] 
**maxRidesharingDurationToPt** | **Integer**| Maximal duration of ridesharing on public transport in second [optional] 
**maxCarNoParkDurationToPt** | **Integer**| Maximal duration of car no park on public transport in second [optional] 
**maxTaxiDurationToPt** | **Integer**| Maximal duration of taxi on public transport in second, only available in distributed scenario [optional] 
**walkingSpeed** | **Float**| Walking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bikeSpeed** | **Float**| Biking speed for the fallback sections. Speed unit must be in meter/second [optional] 
**bssSpeed** | **Float**| Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second [optional] 
**carSpeed** | **Float**| Driving speed for the fallback sections. Speed unit must be in meter/second [optional] 
**ridesharingSpeed** | **Float**| ridesharing speed for the fallback sections. Speed unit must be in meter/second [optional] 
**carNoParkSpeed** | **Float**| Driving speed without car park for the fallback sections. Speed unit must be in meter/second [optional] 
**taxiSpeed** | **Float**| taxi speed speed for the fallback sections. Speed unit must be in meter/second [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) [optional] 
**allowedId** | [**List&lt;String&gt;**](String.md)| If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. [optional] 
**disruptionActive** | **Boolean**| DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; [optional] 
**dataFreshness** | **String**| Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information [optional] [enum: base_schedule, adapted_schedule, realtime] 
**maxDuration** | **Integer**| Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). [optional] 
**wheelchair** | **Boolean**| If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. [optional] 
**travelerType** | **String**| Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker] 
**directPath** | **String**| Specify if direct path should be suggested [optional] [default to indifferent] [enum: indifferent, only, none] 
**freeRadiusFrom** | **Integer**| Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**freeRadiusTo** | **Integer**| Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) [optional] 
**directPathMode** | [**List&lt;String&gt;**](String.md)| Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] [optional] [enum: taxi, walking, car_no_park, car, ridesharing, bss, bike] 
**partnerServices** | [**List&lt;String&gt;**](String.md)| Expose only the partner type into the response. [optional] [enum: ridesharing] 
**minDuration** | **Integer**| Minimum travel duration [optional] 
**boundaryDuration** | [**List&lt;Integer&gt;**](Integer.md)| To provide multiple duration parameters [optional] 

### Return
[**GraphicalIsrochone1**](../model/GraphicalIsrochone1)

### Example
```kotlin
navitiaSdk.graphicalIsochroneApi.newCoverageRegionIsochronesRequestBuilder()
    .withRegion("region_example")
    .withFrom("from_example")
    .withTo("to_example")
    .withDatetime(DateTime())
    .withDatetimeRepresents("departure")
    .withMaxNbTransfers(56)
    .withMinNbTransfers(56)
    .withFirstSectionMode(listOf("firstSectionMode_example"))
    .withLastSectionMode(listOf("lastSectionMode_example"))
    .withMaxDurationToPt(56)
    .withMaxWalkingDurationToPt(56)
    .withMaxBikeDurationToPt(56)
    .withMaxBssDurationToPt(56)
    .withMaxCarDurationToPt(56)
    .withMaxRidesharingDurationToPt(56)
    .withMaxCarNoParkDurationToPt(56)
    .withMaxTaxiDurationToPt(56)
    .withWalkingSpeed(3.4f)
    .withBikeSpeed(3.4f)
    .withBssSpeed(3.4f)
    .withCarSpeed(3.4f)
    .withRidesharingSpeed(3.4f)
    .withCarNoParkSpeed(3.4f)
    .withTaxiSpeed(3.4f)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withAllowedId(listOf("allowedId_example"))
    .withDisruptionActive(true)
    .withDataFreshness("dataFreshness_example")
    .withMaxDuration(56)
    .withWheelchair(true)
    .withTravelerType("travelerType_example")
    .withDirectPath("indifferent")
    .withFreeRadiusFrom(56)
    .withFreeRadiusTo(56)
    .withDirectPathMode(listOf("directPathMode_example"))
    .withPartnerServices(listOf("partnerServices_example"))
    .withMinDuration(56)
    .withBoundaryDuration(listOf(56))
    .get(object : ApiCallback<T> {
        override fun onSuccess(
            result: T,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Success result
        }

        override fun onFailure(
            e: ApiException?,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Failure result
        }

        override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            // Progress upload
        }

        override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            // Progress download
        }
    })
```

