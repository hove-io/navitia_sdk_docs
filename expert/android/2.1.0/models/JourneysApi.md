# JourneysApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatJourneys**](JourneysApi.md#getCoverageLonLatJourneys) | **GET** /coverage/{lon};{lat}/journeys | 
[**getCoverageRegionJourneys**](JourneysApi.md#getCoverageRegionJourneys) | **GET** /coverage/{region}/journeys | 
[**getJourneys**](JourneysApi.md#getJourneys) | **GET** /journeys | 


<a name="getCoverageLonLatJourneys"></a>
# **getCoverageLonLatJourneys**
> Journeys getCoverageLonLatJourneys(lat, lon, from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.JourneysApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

JourneysApi apiInstance = new JourneysApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String from = "from_example"; // String | The id of the departure of your journey. If not provided an isochrone is computed.
String to = "to_example"; // String | The id of the arrival of your journey. If not provided an isochrone is computed.
DateTime datetime = new DateTime(); // DateTime | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period.
String datetimeRepresents = "departure"; // String | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime
Integer maxNbTransfers = 56; // Integer | Maximum number of transfers in each journey
Integer minNbTransfers = 56; // Integer | Minimum number of transfers in each journey
List<String> firstSectionMode = Arrays.asList("firstSectionMode_example"); // List<String> | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike`
List<String> lastSectionMode = Arrays.asList("lastSectionMode_example"); // List<String> | Same as first_section_mode but for the last section.
Integer maxDurationToPt = 56; // Integer | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds
Integer maxWalkingDurationToPt = 56; // Integer | Maximal duration of walking on public transport in second
Integer maxBikeDurationToPt = 56; // Integer | Maximal duration of bike on public transport in second
Integer maxBssDurationToPt = 56; // Integer | Maximal duration of bss on public transport in second
Integer maxCarDurationToPt = 56; // Integer | Maximal duration of car on public transport in second
Integer maxRidesharingDurationToPt = 56; // Integer | Maximal duration of ridesharing on public transport in second
Integer maxTaxiDurationToPt = 56; // Integer | Maximal duration of taxi on public transport in second, only available in distributed scenario
Float walkingSpeed = 3.4F; // Float | Walking speed for the fallback sections. Speed unit must be in meter/second
Float bikeSpeed = 3.4F; // Float | Biking speed for the fallback sections. Speed unit must be in meter/second
Float bssSpeed = 3.4F; // Float | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second
Float carSpeed = 3.4F; // Float | Driving speed for the fallback sections. Speed unit must be in meter/second
Float ridesharingSpeed = 3.4F; // Float | ridesharing speed for the fallback sections. Speed unit must be in meter/second
Float taxiSpeed = 3.4F; // Float | taxi speed speed for the fallback sections. Speed unit must be in meter/second
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[])
List<String> allowedId = Arrays.asList("allowedId_example"); // List<String> | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used.
Boolean disruptionActive = true; // Boolean | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime`
String dataFreshness = "dataFreshness_example"; // String | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule.  * 'realtime' - Use all realtime information
Integer maxDuration = 56; // Integer | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them).
Boolean wheelchair = true; // Boolean | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on.
String travelerType = "travelerType_example"; // String | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself.
String directPath = "indifferent"; // String | Specify if direct path should be suggested
Integer freeRadiusFrom = 56; // Integer | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0)
Integer freeRadiusTo = 56; // Integer | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0)
List<String> directPathMode = Arrays.asList("directPathMode_example"); // List<String> | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[]
Integer count = 56; // Integer | Fixed number of different journeys
Boolean isJourneySchedules = true; // Boolean | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters
Integer minNbJourneys = 56; // Integer | Minimum number of different suggested journeys, must be >= 0
Integer maxNbJourneys = 56; // Integer | Maximum number of different suggested journeys, must be > 0
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("addPoiInfos_example"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response
Integer timeframeDuration = 56; // Integer | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter.
Boolean equipmentDetails = True; // Boolean | enhance response with accessibility equipement details
Integer maxTaxiDirectPathDuration = 56; // Integer | limit duration of direct path in taxi, used ONLY in distributed scenario
Integer maxWalkingDirectPathDuration = 56; // Integer | limit duration of direct path in walking, used ONLY in distributed scenario
Integer maxCarDirectPathDuration = 56; // Integer | limit duration of direct path in car, used ONLY in distributed scenario
Integer maxRidesharingDirectPathDuration = 56; // Integer | limit duration of direct path in ridesharing, used ONLY in distributed scenario
Integer maxBssDirectPathDuration = 56; // Integer | limit duration of direct path in bss, used ONLY in distributed scenario
Integer maxBikeDirectPathDuration = 56; // Integer | limit duration of direct path in bike, used ONLY in distributed scenario
Integer depth = 1; // Integer | The depth of your object
try {
    Journeys result = apiInstance.getCoverageLonLatJourneys(lat, lon, from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling JourneysApi#getCoverageLonLatJourneys");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **from** | **String**| The id of the departure of your journey. If not provided an isochrone is computed. | [optional]
 **to** | **String**| The id of the arrival of your journey. If not provided an isochrone is computed. | [optional]
 **datetime** | **DateTime**| Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. | [optional]
 **datetimeRepresents** | **String**| Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime | [optional] [default to departure] [enum: arrival, departure]
 **maxNbTransfers** | **Integer**| Maximum number of transfers in each journey | [optional]
 **minNbTransfers** | **Integer**| Minimum number of transfers in each journey | [optional]
 **firstSectionMode** | [**List&lt;String&gt;**](String.md)| Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **lastSectionMode** | [**List&lt;String&gt;**](String.md)| Same as first_section_mode but for the last section. | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **maxDurationToPt** | **Integer**| Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds | [optional]
 **maxWalkingDurationToPt** | **Integer**| Maximal duration of walking on public transport in second | [optional]
 **maxBikeDurationToPt** | **Integer**| Maximal duration of bike on public transport in second | [optional]
 **maxBssDurationToPt** | **Integer**| Maximal duration of bss on public transport in second | [optional]
 **maxCarDurationToPt** | **Integer**| Maximal duration of car on public transport in second | [optional]
 **maxRidesharingDurationToPt** | **Integer**| Maximal duration of ridesharing on public transport in second | [optional]
 **maxTaxiDurationToPt** | **Integer**| Maximal duration of taxi on public transport in second, only available in distributed scenario | [optional]
 **walkingSpeed** | **Float**| Walking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bikeSpeed** | **Float**| Biking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bssSpeed** | **Float**| Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second | [optional]
 **carSpeed** | **Float**| Driving speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **ridesharingSpeed** | **Float**| ridesharing speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **taxiSpeed** | **Float**| taxi speed speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) | [optional]
 **allowedId** | [**List&lt;String&gt;**](String.md)| If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. | [optional]
 **disruptionActive** | **Boolean**| DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; | [optional]
 **dataFreshness** | **String**| Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **maxDuration** | **Integer**| Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). | [optional]
 **wheelchair** | **Boolean**| If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. | [optional]
 **travelerType** | **String**| Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. | [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker]
 **directPath** | **String**| Specify if direct path should be suggested | [optional] [default to indifferent] [enum: indifferent, only, none]
 **freeRadiusFrom** | **Integer**| Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **freeRadiusTo** | **Integer**| Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **directPathMode** | [**List&lt;String&gt;**](String.md)| Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **count** | **Integer**| Fixed number of different journeys | [optional]
 **isJourneySchedules** | **Boolean**| True when &#39;/journeys&#39; is called to computethe same journey schedules and it&#39;ll override some specific parameters | [optional]
 **minNbJourneys** | **Integer**| Minimum number of different suggested journeys, must be &gt;&#x3D; 0 | [optional]
 **maxNbJourneys** | **Integer**| Maximum number of different suggested journeys, must be &gt; 0 | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of response | [optional] [enum: bss_stands, car_park, , none]
 **timeframeDuration** | **Integer**| Minimum timeframe to search journeys. For example &#39;timeframe_duration&#x3D;3600&#39; will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it&#39;s actually a minimum. Nota 2: &#39;max_nb_journeys&#39; parameter has priority over &#39;timeframe_duration&#39; parameter. | [optional]
 **equipmentDetails** | **Boolean**| enhance response with accessibility equipement details | [optional] [default to True]
 **maxTaxiDirectPathDuration** | **Integer**| limit duration of direct path in taxi, used ONLY in distributed scenario | [optional]
 **maxWalkingDirectPathDuration** | **Integer**| limit duration of direct path in walking, used ONLY in distributed scenario | [optional]
 **maxCarDirectPathDuration** | **Integer**| limit duration of direct path in car, used ONLY in distributed scenario | [optional]
 **maxRidesharingDirectPathDuration** | **Integer**| limit duration of direct path in ridesharing, used ONLY in distributed scenario | [optional]
 **maxBssDirectPathDuration** | **Integer**| limit duration of direct path in bss, used ONLY in distributed scenario | [optional]
 **maxBikeDirectPathDuration** | **Integer**| limit duration of direct path in bike, used ONLY in distributed scenario | [optional]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]

### Return type

[**Journeys**](Journeys.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionJourneys"></a>
# **getCoverageRegionJourneys**
> Journeys getCoverageRegionJourneys(region, from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.JourneysApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

JourneysApi apiInstance = new JourneysApi();
String region = "region_example"; // String |  The region you want to query
String from = "from_example"; // String | The id of the departure of your journey. If not provided an isochrone is computed.
String to = "to_example"; // String | The id of the arrival of your journey. If not provided an isochrone is computed.
DateTime datetime = new DateTime(); // DateTime | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period.
String datetimeRepresents = "departure"; // String | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime
Integer maxNbTransfers = 56; // Integer | Maximum number of transfers in each journey
Integer minNbTransfers = 56; // Integer | Minimum number of transfers in each journey
List<String> firstSectionMode = Arrays.asList("firstSectionMode_example"); // List<String> | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike`
List<String> lastSectionMode = Arrays.asList("lastSectionMode_example"); // List<String> | Same as first_section_mode but for the last section.
Integer maxDurationToPt = 56; // Integer | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds
Integer maxWalkingDurationToPt = 56; // Integer | Maximal duration of walking on public transport in second
Integer maxBikeDurationToPt = 56; // Integer | Maximal duration of bike on public transport in second
Integer maxBssDurationToPt = 56; // Integer | Maximal duration of bss on public transport in second
Integer maxCarDurationToPt = 56; // Integer | Maximal duration of car on public transport in second
Integer maxRidesharingDurationToPt = 56; // Integer | Maximal duration of ridesharing on public transport in second
Integer maxTaxiDurationToPt = 56; // Integer | Maximal duration of taxi on public transport in second, only available in distributed scenario
Float walkingSpeed = 3.4F; // Float | Walking speed for the fallback sections. Speed unit must be in meter/second
Float bikeSpeed = 3.4F; // Float | Biking speed for the fallback sections. Speed unit must be in meter/second
Float bssSpeed = 3.4F; // Float | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second
Float carSpeed = 3.4F; // Float | Driving speed for the fallback sections. Speed unit must be in meter/second
Float ridesharingSpeed = 3.4F; // Float | ridesharing speed for the fallback sections. Speed unit must be in meter/second
Float taxiSpeed = 3.4F; // Float | taxi speed speed for the fallback sections. Speed unit must be in meter/second
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[])
List<String> allowedId = Arrays.asList("allowedId_example"); // List<String> | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used.
Boolean disruptionActive = true; // Boolean | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime`
String dataFreshness = "dataFreshness_example"; // String | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule.  * 'realtime' - Use all realtime information
Integer maxDuration = 56; // Integer | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them).
Boolean wheelchair = true; // Boolean | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on.
String travelerType = "travelerType_example"; // String | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself.
String directPath = "indifferent"; // String | Specify if direct path should be suggested
Integer freeRadiusFrom = 56; // Integer | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0)
Integer freeRadiusTo = 56; // Integer | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0)
List<String> directPathMode = Arrays.asList("directPathMode_example"); // List<String> | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[]
Integer count = 56; // Integer | Fixed number of different journeys
Boolean isJourneySchedules = true; // Boolean | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters
Integer minNbJourneys = 56; // Integer | Minimum number of different suggested journeys, must be >= 0
Integer maxNbJourneys = 56; // Integer | Maximum number of different suggested journeys, must be > 0
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("addPoiInfos_example"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response
Integer timeframeDuration = 56; // Integer | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter.
Boolean equipmentDetails = True; // Boolean | enhance response with accessibility equipement details
Integer maxTaxiDirectPathDuration = 56; // Integer | limit duration of direct path in taxi, used ONLY in distributed scenario
Integer maxWalkingDirectPathDuration = 56; // Integer | limit duration of direct path in walking, used ONLY in distributed scenario
Integer maxCarDirectPathDuration = 56; // Integer | limit duration of direct path in car, used ONLY in distributed scenario
Integer maxRidesharingDirectPathDuration = 56; // Integer | limit duration of direct path in ridesharing, used ONLY in distributed scenario
Integer maxBssDirectPathDuration = 56; // Integer | limit duration of direct path in bss, used ONLY in distributed scenario
Integer maxBikeDirectPathDuration = 56; // Integer | limit duration of direct path in bike, used ONLY in distributed scenario
Integer depth = 1; // Integer | The depth of your object
try {
    Journeys result = apiInstance.getCoverageRegionJourneys(region, from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling JourneysApi#getCoverageRegionJourneys");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **from** | **String**| The id of the departure of your journey. If not provided an isochrone is computed. | [optional]
 **to** | **String**| The id of the arrival of your journey. If not provided an isochrone is computed. | [optional]
 **datetime** | **DateTime**| Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. | [optional]
 **datetimeRepresents** | **String**| Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime | [optional] [default to departure] [enum: arrival, departure]
 **maxNbTransfers** | **Integer**| Maximum number of transfers in each journey | [optional]
 **minNbTransfers** | **Integer**| Minimum number of transfers in each journey | [optional]
 **firstSectionMode** | [**List&lt;String&gt;**](String.md)| Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **lastSectionMode** | [**List&lt;String&gt;**](String.md)| Same as first_section_mode but for the last section. | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **maxDurationToPt** | **Integer**| Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds | [optional]
 **maxWalkingDurationToPt** | **Integer**| Maximal duration of walking on public transport in second | [optional]
 **maxBikeDurationToPt** | **Integer**| Maximal duration of bike on public transport in second | [optional]
 **maxBssDurationToPt** | **Integer**| Maximal duration of bss on public transport in second | [optional]
 **maxCarDurationToPt** | **Integer**| Maximal duration of car on public transport in second | [optional]
 **maxRidesharingDurationToPt** | **Integer**| Maximal duration of ridesharing on public transport in second | [optional]
 **maxTaxiDurationToPt** | **Integer**| Maximal duration of taxi on public transport in second, only available in distributed scenario | [optional]
 **walkingSpeed** | **Float**| Walking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bikeSpeed** | **Float**| Biking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bssSpeed** | **Float**| Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second | [optional]
 **carSpeed** | **Float**| Driving speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **ridesharingSpeed** | **Float**| ridesharing speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **taxiSpeed** | **Float**| taxi speed speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) | [optional]
 **allowedId** | [**List&lt;String&gt;**](String.md)| If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. | [optional]
 **disruptionActive** | **Boolean**| DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; | [optional]
 **dataFreshness** | **String**| Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **maxDuration** | **Integer**| Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). | [optional]
 **wheelchair** | **Boolean**| If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. | [optional]
 **travelerType** | **String**| Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. | [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker]
 **directPath** | **String**| Specify if direct path should be suggested | [optional] [default to indifferent] [enum: indifferent, only, none]
 **freeRadiusFrom** | **Integer**| Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **freeRadiusTo** | **Integer**| Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **directPathMode** | [**List&lt;String&gt;**](String.md)| Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **count** | **Integer**| Fixed number of different journeys | [optional]
 **isJourneySchedules** | **Boolean**| True when &#39;/journeys&#39; is called to computethe same journey schedules and it&#39;ll override some specific parameters | [optional]
 **minNbJourneys** | **Integer**| Minimum number of different suggested journeys, must be &gt;&#x3D; 0 | [optional]
 **maxNbJourneys** | **Integer**| Maximum number of different suggested journeys, must be &gt; 0 | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of response | [optional] [enum: bss_stands, car_park, , none]
 **timeframeDuration** | **Integer**| Minimum timeframe to search journeys. For example &#39;timeframe_duration&#x3D;3600&#39; will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it&#39;s actually a minimum. Nota 2: &#39;max_nb_journeys&#39; parameter has priority over &#39;timeframe_duration&#39; parameter. | [optional]
 **equipmentDetails** | **Boolean**| enhance response with accessibility equipement details | [optional] [default to True]
 **maxTaxiDirectPathDuration** | **Integer**| limit duration of direct path in taxi, used ONLY in distributed scenario | [optional]
 **maxWalkingDirectPathDuration** | **Integer**| limit duration of direct path in walking, used ONLY in distributed scenario | [optional]
 **maxCarDirectPathDuration** | **Integer**| limit duration of direct path in car, used ONLY in distributed scenario | [optional]
 **maxRidesharingDirectPathDuration** | **Integer**| limit duration of direct path in ridesharing, used ONLY in distributed scenario | [optional]
 **maxBssDirectPathDuration** | **Integer**| limit duration of direct path in bss, used ONLY in distributed scenario | [optional]
 **maxBikeDirectPathDuration** | **Integer**| limit duration of direct path in bike, used ONLY in distributed scenario | [optional]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]

### Return type

[**Journeys**](Journeys.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getJourneys"></a>
# **getJourneys**
> Journeys getJourneys(from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.JourneysApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

JourneysApi apiInstance = new JourneysApi();
String from = "from_example"; // String | The id of the departure of your journey. If not provided an isochrone is computed.
String to = "to_example"; // String | The id of the arrival of your journey. If not provided an isochrone is computed.
DateTime datetime = new DateTime(); // DateTime | Date and time to go/arrive (see `datetime_represents`). Note: the datetime must be in the coverage’s publication period.
String datetimeRepresents = "departure"; // String | Determine how datetime is handled.  Possible values:  * 'departure' - Compute journeys starting after datetime  * 'arrival' - Compute journeys arriving before datetime
Integer maxNbTransfers = 56; // Integer | Maximum number of transfers in each journey
Integer minNbTransfers = 56; // Integer | Minimum number of transfers in each journey
List<String> firstSectionMode = Arrays.asList("firstSectionMode_example"); // List<String> | Force the first section mode if the first section is not a public transport one. `bss` stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing `bss` implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: `first_section_mode[]=walking&first_section_mode[]=bss&first_section_mode[]=bike&last_section_mode[]=walking&last_section_mode[]=bss&last_section_mode[]=bike`
List<String> lastSectionMode = Arrays.asList("lastSectionMode_example"); // List<String> | Same as first_section_mode but for the last section.
Integer maxDurationToPt = 56; // Integer | Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds
Integer maxWalkingDurationToPt = 56; // Integer | Maximal duration of walking on public transport in second
Integer maxBikeDurationToPt = 56; // Integer | Maximal duration of bike on public transport in second
Integer maxBssDurationToPt = 56; // Integer | Maximal duration of bss on public transport in second
Integer maxCarDurationToPt = 56; // Integer | Maximal duration of car on public transport in second
Integer maxRidesharingDurationToPt = 56; // Integer | Maximal duration of ridesharing on public transport in second
Integer maxTaxiDurationToPt = 56; // Integer | Maximal duration of taxi on public transport in second, only available in distributed scenario
Float walkingSpeed = 3.4F; // Float | Walking speed for the fallback sections. Speed unit must be in meter/second
Float bikeSpeed = 3.4F; // Float | Biking speed for the fallback sections. Speed unit must be in meter/second
Float bssSpeed = 3.4F; // Float | Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second
Float carSpeed = 3.4F; // Float | Driving speed for the fallback sections. Speed unit must be in meter/second
Float ridesharingSpeed = 3.4F; // Float | ridesharing speed for the fallback sections. Speed unit must be in meter/second
Float taxiSpeed = 3.4F; // Float | taxi speed speed for the fallback sections. Speed unit must be in meter/second
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[])
List<String> allowedId = Arrays.asList("allowedId_example"); // List<String> | If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for `allowed_id[]=line:A&forbidden_uris[]=physical_mode:Bus`, only vehicles of the line A that are not buses will be used.
Boolean disruptionActive = true; // Boolean | DEPRECATED, replaced by `data_freshness`. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: `disruption_active=true` <=> `data_freshness=realtime`
String dataFreshness = "dataFreshness_example"; // String | Define the freshness of data to use to compute journeys. When using the following parameter `&data_freshness=base_schedule` you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a `realtime` request to get a new undisrupted solution.  Possible values:  * 'base_schedule' - Use theoric schedule information  * 'adapted_schedule' - Use of adapted schedule information (like strike adjusting, etc.). Prefer `realtime` for traveler information as it will also contain adapted information schedule.  * 'realtime' - Use all realtime information
Integer maxDuration = 56; // Integer | Maximum duration of journeys in seconds (from `datetime` parameter). More usefull when computing an isochrone (only `from` or `to` is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them).
Boolean wheelchair = true; // Boolean | If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on.
String travelerType = "travelerType_example"; // String | Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set `forbidden_uris[]`! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (`first_section_mode[]` and `last_section_mode[]`) and set them yourself.
String directPath = "indifferent"; // String | Specify if direct path should be suggested
Integer freeRadiusFrom = 56; // Integer | Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly=0)
Integer freeRadiusTo = 56; // Integer | Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly=0)
List<String> directPathMode = Arrays.asList("directPathMode_example"); // List<String> | Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[]
Integer count = 56; // Integer | Fixed number of different journeys
Boolean isJourneySchedules = true; // Boolean | True when '/journeys' is called to computethe same journey schedules and it'll override some specific parameters
Integer minNbJourneys = 56; // Integer | Minimum number of different suggested journeys, must be >= 0
Integer maxNbJourneys = 56; // Integer | Maximum number of different suggested journeys, must be > 0
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("addPoiInfos_example"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of response
Integer timeframeDuration = 56; // Integer | Minimum timeframe to search journeys. For example 'timeframe_duration=3600' will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it's actually a minimum. Nota 2: 'max_nb_journeys' parameter has priority over 'timeframe_duration' parameter.
Boolean equipmentDetails = True; // Boolean | enhance response with accessibility equipement details
Integer maxTaxiDirectPathDuration = 56; // Integer | limit duration of direct path in taxi, used ONLY in distributed scenario
Integer maxWalkingDirectPathDuration = 56; // Integer | limit duration of direct path in walking, used ONLY in distributed scenario
Integer maxCarDirectPathDuration = 56; // Integer | limit duration of direct path in car, used ONLY in distributed scenario
Integer maxRidesharingDirectPathDuration = 56; // Integer | limit duration of direct path in ridesharing, used ONLY in distributed scenario
Integer maxBssDirectPathDuration = 56; // Integer | limit duration of direct path in bss, used ONLY in distributed scenario
Integer maxBikeDirectPathDuration = 56; // Integer | limit duration of direct path in bike, used ONLY in distributed scenario
Integer depth = 1; // Integer | The depth of your object
try {
    Journeys result = apiInstance.getJourneys(from, to, datetime, datetimeRepresents, maxNbTransfers, minNbTransfers, firstSectionMode, lastSectionMode, maxDurationToPt, maxWalkingDurationToPt, maxBikeDurationToPt, maxBssDurationToPt, maxCarDurationToPt, maxRidesharingDurationToPt, maxTaxiDurationToPt, walkingSpeed, bikeSpeed, bssSpeed, carSpeed, ridesharingSpeed, taxiSpeed, forbiddenUris, allowedId, disruptionActive, dataFreshness, maxDuration, wheelchair, travelerType, directPath, freeRadiusFrom, freeRadiusTo, directPathMode, count, isJourneySchedules, minNbJourneys, maxNbJourneys, bssStands, addPoiInfos, timeframeDuration, equipmentDetails, maxTaxiDirectPathDuration, maxWalkingDirectPathDuration, maxCarDirectPathDuration, maxRidesharingDirectPathDuration, maxBssDirectPathDuration, maxBikeDirectPathDuration, depth);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling JourneysApi#getJourneys");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **from** | **String**| The id of the departure of your journey. If not provided an isochrone is computed. | [optional]
 **to** | **String**| The id of the arrival of your journey. If not provided an isochrone is computed. | [optional]
 **datetime** | **DateTime**| Date and time to go/arrive (see &#x60;datetime_represents&#x60;). Note: the datetime must be in the coverage’s publication period. | [optional]
 **datetimeRepresents** | **String**| Determine how datetime is handled.  Possible values:  * &#39;departure&#39; - Compute journeys starting after datetime  * &#39;arrival&#39; - Compute journeys arriving before datetime | [optional] [default to departure] [enum: arrival, departure]
 **maxNbTransfers** | **Integer**| Maximum number of transfers in each journey | [optional]
 **minNbTransfers** | **Integer**| Minimum number of transfers in each journey | [optional]
 **firstSectionMode** | [**List&lt;String&gt;**](String.md)| Force the first section mode if the first section is not a public transport one. &#x60;bss&#x60; stands for bike sharing system. Note 1: It’s an array, you can give multiple modes. Note 2: Choosing &#x60;bss&#x60; implicitly allows the walking mode since you might have to walk to the bss station. Note 3: The parameter is inclusive, not exclusive, so if you want to forbid a mode, you need to add all the other modes. Eg: If you never want to use a car, you need: &#x60;first_section_mode[]&#x3D;walking&amp;first_section_mode[]&#x3D;bss&amp;first_section_mode[]&#x3D;bike&amp;last_section_mode[]&#x3D;walking&amp;last_section_mode[]&#x3D;bss&amp;last_section_mode[]&#x3D;bike&#x60; | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **lastSectionMode** | [**List&lt;String&gt;**](String.md)| Same as first_section_mode but for the last section. | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **maxDurationToPt** | **Integer**| Maximum allowed duration to reach the public transport (same limit used before and after public transport). Use this to limit the walking/biking part. Unit is seconds | [optional]
 **maxWalkingDurationToPt** | **Integer**| Maximal duration of walking on public transport in second | [optional]
 **maxBikeDurationToPt** | **Integer**| Maximal duration of bike on public transport in second | [optional]
 **maxBssDurationToPt** | **Integer**| Maximal duration of bss on public transport in second | [optional]
 **maxCarDurationToPt** | **Integer**| Maximal duration of car on public transport in second | [optional]
 **maxRidesharingDurationToPt** | **Integer**| Maximal duration of ridesharing on public transport in second | [optional]
 **maxTaxiDurationToPt** | **Integer**| Maximal duration of taxi on public transport in second, only available in distributed scenario | [optional]
 **walkingSpeed** | **Float**| Walking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bikeSpeed** | **Float**| Biking speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **bssSpeed** | **Float**| Speed while using a bike from a bike sharing system for the fallback sections. Speed unit must be in meter/second | [optional]
 **carSpeed** | **Float**| Driving speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **ridesharingSpeed** | **Float**| ridesharing speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **taxiSpeed** | **Float**| taxi speed speed for the fallback sections. Speed unit must be in meter/second | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| If you want to avoid lines, modes, networks, etc. Note: the forbidden_uris[] concern only the public transport objects. You can’t for example forbid the use of the bike with them, you have to set the fallback modes for this (first_section_mode[] and last_section_mode[]) | [optional]
 **allowedId** | [**List&lt;String&gt;**](String.md)| If you want to use only a small subset of the public transport objects in your solution. Note: The constraint intersects with forbidden_uris[]. For example, if you ask for &#x60;allowed_id[]&#x3D;line:A&amp;forbidden_uris[]&#x3D;physical_mode:Bus&#x60;, only vehicles of the line A that are not buses will be used. | [optional]
 **disruptionActive** | **Boolean**| DEPRECATED, replaced by &#x60;data_freshness&#x60;. If true the algorithm takes the disruptions into account, and thus avoid disrupted public transport. Nota: &#x60;disruption_active&#x3D;true&#x60; &lt;&#x3D;&gt; &#x60;data_freshness&#x3D;realtime&#x60; | [optional]
 **dataFreshness** | **String**| Define the freshness of data to use to compute journeys. When using the following parameter &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; you can get disrupted journeys in the response. You can then display the disruption message to the traveler and make a &#x60;realtime&#x60; request to get a new undisrupted solution.  Possible values:  * &#39;base_schedule&#39; - Use theoric schedule information  * &#39;adapted_schedule&#39; - Use of adapted schedule information (like strike adjusting, etc.). Prefer &#x60;realtime&#x60; for traveler information as it will also contain adapted information schedule.  * &#39;realtime&#39; - Use all realtime information | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **maxDuration** | **Integer**| Maximum duration of journeys in seconds (from &#x60;datetime&#x60; parameter). More usefull when computing an isochrone (only &#x60;from&#x60; or &#x60;to&#x60; is provided). On a classic journey (from-to), it will mostly speedup Navitia: You may have journeys a bit longer than that value (you would have to filter them). | [optional]
 **wheelchair** | **Boolean**| If true the traveler is considered to be using a wheelchair, thus only accessible public transport are used. Be warned: many data are currently too faint to provide acceptable answers with this parameter on. | [optional]
 **travelerType** | **String**| Define speeds and accessibility values for different kind of people. Each profile also automatically determines appropriate first and last section modes to the covered area. Note: this means that you might get car, bike, etc. fallback routes even if you set &#x60;forbidden_uris[]&#x60;! You can overload all parameters (especially speeds, distances, first and last modes) by setting all of them specifically. We advise that you don’t rely on the traveler_type’s fallback modes (&#x60;first_section_mode[]&#x60; and &#x60;last_section_mode[]&#x60;) and set them yourself. | [optional] [enum: cyclist, luggage, wheelchair, standard, motorist, fast_walker, slow_walker]
 **directPath** | **String**| Specify if direct path should be suggested | [optional] [default to indifferent] [enum: indifferent, only, none]
 **freeRadiusFrom** | **Integer**| Radius length (in meters) around the coordinates of departure in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **freeRadiusTo** | **Integer**| Radius length (in meters) around the coordinates of arrival in which the stop points are considered free to go (crowfly&#x3D;0) | [optional]
 **directPathMode** | [**List&lt;String&gt;**](String.md)| Force the direct-path modes.If this list is not empty, we only compute direct_path for modes in this listAnd filter all the direct_paths of modes in first_section_mode[] | [optional] [enum: taxi, walking, car, ridesharing, bss, bike]
 **count** | **Integer**| Fixed number of different journeys | [optional]
 **isJourneySchedules** | **Boolean**| True when &#39;/journeys&#39; is called to computethe same journey schedules and it&#39;ll override some specific parameters | [optional]
 **minNbJourneys** | **Integer**| Minimum number of different suggested journeys, must be &gt;&#x3D; 0 | [optional]
 **maxNbJourneys** | **Integer**| Maximum number of different suggested journeys, must be &gt; 0 | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of response | [optional] [enum: bss_stands, car_park, , none]
 **timeframeDuration** | **Integer**| Minimum timeframe to search journeys. For example &#39;timeframe_duration&#x3D;3600&#39; will search for all interesting journeys departing within the next hour. Nota 1: Navitia can return journeys after that timeframe as it&#39;s actually a minimum. Nota 2: &#39;max_nb_journeys&#39; parameter has priority over &#39;timeframe_duration&#39; parameter. | [optional]
 **equipmentDetails** | **Boolean**| enhance response with accessibility equipement details | [optional] [default to True]
 **maxTaxiDirectPathDuration** | **Integer**| limit duration of direct path in taxi, used ONLY in distributed scenario | [optional]
 **maxWalkingDirectPathDuration** | **Integer**| limit duration of direct path in walking, used ONLY in distributed scenario | [optional]
 **maxCarDirectPathDuration** | **Integer**| limit duration of direct path in car, used ONLY in distributed scenario | [optional]
 **maxRidesharingDirectPathDuration** | **Integer**| limit duration of direct path in ridesharing, used ONLY in distributed scenario | [optional]
 **maxBssDirectPathDuration** | **Integer**| limit duration of direct path in bss, used ONLY in distributed scenario | [optional]
 **maxBikeDirectPathDuration** | **Integer**| limit duration of direct path in bike, used ONLY in distributed scenario | [optional]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]

### Return type

[**Journeys**](Journeys.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

