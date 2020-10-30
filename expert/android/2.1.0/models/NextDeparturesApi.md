# NextDeparturesApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatDepartures**](NextDeparturesApi.md#getCoverageLonLatDepartures) | **GET** /coverage/{lon};{lat}/departures | 
[**getCoverageLonLatUriDepartures**](NextDeparturesApi.md#getCoverageLonLatUriDepartures) | **GET** /coverage/{lon};{lat}/{uri}/departures | 
[**getCoverageRegionDepartures**](NextDeparturesApi.md#getCoverageRegionDepartures) | **GET** /coverage/{region}/departures | 
[**getCoverageRegionUriDepartures**](NextDeparturesApi.md#getCoverageRegionUriDepartures) | **GET** /coverage/{region}/{uri}/departures | 


<a name="getCoverageLonLatDepartures"></a>
# **getCoverageLonLatDepartures**
> Departures getCoverageLonLatDepartures(lat, lon, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.NextDeparturesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

NextDeparturesApi apiInstance = new NextDeparturesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String filter = "filter_example"; // String | use to filter PT objects
DateTime fromDatetime = new DateTime(); // DateTime | The datetime from which you want the schedules
DateTime untilDatetime = new DateTime(); // DateTime | The datetime until which you want the schedules
Integer duration = 86400; // Integer | Maximum duration between datetime and the retrieved stop time
Integer depth = 2; // Integer | The depth of your object
Integer count = 10; // Integer | Number of schedules per page
Integer startPage = 56; // Integer | The current page
Integer maxDateTimes = 56; // Integer | DEPRECATED, replaced by `items_per_schedule`
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String calendar = "calendar_example"; // String | Id of the calendar
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean showCodes = true; // Boolean | show more identification codes
String dataFreshness = "dataFreshness_example"; // String | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data
Integer itemsPerSchedule = 10000; // Integer | maximum number of date_times per schedule
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String directionType = "directionType_example"; // String | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound].
try {
    Departures result = apiInstance.getCoverageLonLatDepartures(lat, lon, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling NextDeparturesApi#getCoverageLonLatDepartures");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **filter** | **String**| use to filter PT objects | [optional]
 **fromDatetime** | **DateTime**| The datetime from which you want the schedules | [optional]
 **untilDatetime** | **DateTime**| The datetime until which you want the schedules | [optional]
 **duration** | **Integer**| Maximum duration between datetime and the retrieved stop time | [optional] [default to 86400]
 **depth** | **Integer**| The depth of your object | [optional] [default to 2]
 **count** | **Integer**| Number of schedules per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **calendar** | **String**| Id of the calendar | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **itemsPerSchedule** | **Integer**| maximum number of date_times per schedule | [optional] [default to 10000]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. | [optional] [enum: all, forward, backward]

### Return type

[**Departures**](Departures.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriDepartures"></a>
# **getCoverageLonLatUriDepartures**
> Departures getCoverageLonLatUriDepartures(lat, lon, uri, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.NextDeparturesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

NextDeparturesApi apiInstance = new NextDeparturesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
String filter = "filter_example"; // String | use to filter PT objects
DateTime fromDatetime = new DateTime(); // DateTime | The datetime from which you want the schedules
DateTime untilDatetime = new DateTime(); // DateTime | The datetime until which you want the schedules
Integer duration = 86400; // Integer | Maximum duration between datetime and the retrieved stop time
Integer depth = 2; // Integer | The depth of your object
Integer count = 10; // Integer | Number of schedules per page
Integer startPage = 56; // Integer | The current page
Integer maxDateTimes = 56; // Integer | DEPRECATED, replaced by `items_per_schedule`
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String calendar = "calendar_example"; // String | Id of the calendar
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean showCodes = true; // Boolean | show more identification codes
String dataFreshness = "dataFreshness_example"; // String | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data
Integer itemsPerSchedule = 10000; // Integer | maximum number of date_times per schedule
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String directionType = "directionType_example"; // String | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound].
try {
    Departures result = apiInstance.getCoverageLonLatUriDepartures(lat, lon, uri, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling NextDeparturesApi#getCoverageLonLatUriDepartures");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |
 **filter** | **String**| use to filter PT objects | [optional]
 **fromDatetime** | **DateTime**| The datetime from which you want the schedules | [optional]
 **untilDatetime** | **DateTime**| The datetime until which you want the schedules | [optional]
 **duration** | **Integer**| Maximum duration between datetime and the retrieved stop time | [optional] [default to 86400]
 **depth** | **Integer**| The depth of your object | [optional] [default to 2]
 **count** | **Integer**| Number of schedules per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **calendar** | **String**| Id of the calendar | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **itemsPerSchedule** | **Integer**| maximum number of date_times per schedule | [optional] [default to 10000]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. | [optional] [enum: all, forward, backward]

### Return type

[**Departures**](Departures.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionDepartures"></a>
# **getCoverageRegionDepartures**
> Departures getCoverageRegionDepartures(region, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.NextDeparturesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

NextDeparturesApi apiInstance = new NextDeparturesApi();
String region = "region_example"; // String |  The region you want to query
String filter = "filter_example"; // String | use to filter PT objects
DateTime fromDatetime = new DateTime(); // DateTime | The datetime from which you want the schedules
DateTime untilDatetime = new DateTime(); // DateTime | The datetime until which you want the schedules
Integer duration = 86400; // Integer | Maximum duration between datetime and the retrieved stop time
Integer depth = 2; // Integer | The depth of your object
Integer count = 10; // Integer | Number of schedules per page
Integer startPage = 56; // Integer | The current page
Integer maxDateTimes = 56; // Integer | DEPRECATED, replaced by `items_per_schedule`
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String calendar = "calendar_example"; // String | Id of the calendar
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean showCodes = true; // Boolean | show more identification codes
String dataFreshness = "dataFreshness_example"; // String | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data
Integer itemsPerSchedule = 10000; // Integer | maximum number of date_times per schedule
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String directionType = "directionType_example"; // String | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound].
try {
    Departures result = apiInstance.getCoverageRegionDepartures(region, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling NextDeparturesApi#getCoverageRegionDepartures");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **filter** | **String**| use to filter PT objects | [optional]
 **fromDatetime** | **DateTime**| The datetime from which you want the schedules | [optional]
 **untilDatetime** | **DateTime**| The datetime until which you want the schedules | [optional]
 **duration** | **Integer**| Maximum duration between datetime and the retrieved stop time | [optional] [default to 86400]
 **depth** | **Integer**| The depth of your object | [optional] [default to 2]
 **count** | **Integer**| Number of schedules per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **calendar** | **String**| Id of the calendar | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **itemsPerSchedule** | **Integer**| maximum number of date_times per schedule | [optional] [default to 10000]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. | [optional] [enum: all, forward, backward]

### Return type

[**Departures**](Departures.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriDepartures"></a>
# **getCoverageRegionUriDepartures**
> Departures getCoverageRegionUriDepartures(region, uri, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.NextDeparturesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

NextDeparturesApi apiInstance = new NextDeparturesApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
String filter = "filter_example"; // String | use to filter PT objects
DateTime fromDatetime = new DateTime(); // DateTime | The datetime from which you want the schedules
DateTime untilDatetime = new DateTime(); // DateTime | The datetime until which you want the schedules
Integer duration = 86400; // Integer | Maximum duration between datetime and the retrieved stop time
Integer depth = 2; // Integer | The depth of your object
Integer count = 10; // Integer | Number of schedules per page
Integer startPage = 56; // Integer | The current page
Integer maxDateTimes = 56; // Integer | DEPRECATED, replaced by `items_per_schedule`
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String calendar = "calendar_example"; // String | Id of the calendar
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean showCodes = true; // Boolean | show more identification codes
String dataFreshness = "dataFreshness_example"; // String | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data
Integer itemsPerSchedule = 10000; // Integer | maximum number of date_times per schedule
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String directionType = "directionType_example"; // String | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound].
try {
    Departures result = apiInstance.getCoverageRegionUriDepartures(region, uri, filter, fromDatetime, untilDatetime, duration, depth, count, startPage, maxDateTimes, forbiddenId, forbiddenUris, calendar, distance, showCodes, dataFreshness, itemsPerSchedule, disableGeojson, directionType);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling NextDeparturesApi#getCoverageRegionUriDepartures");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **filter** | **String**| use to filter PT objects | [optional]
 **fromDatetime** | **DateTime**| The datetime from which you want the schedules | [optional]
 **untilDatetime** | **DateTime**| The datetime until which you want the schedules | [optional]
 **duration** | **Integer**| Maximum duration between datetime and the retrieved stop time | [optional] [default to 86400]
 **depth** | **Integer**| The depth of your object | [optional] [default to 2]
 **count** | **Integer**| Number of schedules per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **calendar** | **String**| Id of the calendar | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data | [optional] [enum: base_schedule, adapted_schedule, realtime]
 **itemsPerSchedule** | **Integer**| maximum number of date_times per schedule | [optional] [default to 10000]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. | [optional] [enum: all, forward, backward]

### Return type

[**Departures**](Departures.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

