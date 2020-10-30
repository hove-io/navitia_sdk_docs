# LineGroupsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatLineGroups**](LineGroupsApi.md#getCoverageLonLatLineGroups) | **GET** /coverage/{lon};{lat}/line_groups | 
[**getCoverageLonLatLineGroupsId**](LineGroupsApi.md#getCoverageLonLatLineGroupsId) | **GET** /coverage/{lon};{lat}/line_groups/{id} | 
[**getCoverageLonLatUriLineGroups**](LineGroupsApi.md#getCoverageLonLatUriLineGroups) | **GET** /coverage/{lon};{lat}/{uri}/line_groups | 
[**getCoverageLonLatUriLineGroupsId**](LineGroupsApi.md#getCoverageLonLatUriLineGroupsId) | **GET** /coverage/{lon};{lat}/{uri}/line_groups/{id} | 
[**getCoverageRegionLineGroups**](LineGroupsApi.md#getCoverageRegionLineGroups) | **GET** /coverage/{region}/line_groups | 
[**getCoverageRegionLineGroupsId**](LineGroupsApi.md#getCoverageRegionLineGroupsId) | **GET** /coverage/{region}/line_groups/{id} | 
[**getCoverageRegionUriLineGroups**](LineGroupsApi.md#getCoverageRegionUriLineGroups) | **GET** /coverage/{region}/{uri}/line_groups | 
[**getCoverageRegionUriLineGroupsId**](LineGroupsApi.md#getCoverageRegionUriLineGroupsId) | **GET** /coverage/{region}/{uri}/line_groups/{id} | 
[**getLineGroups**](LineGroupsApi.md#getLineGroups) | **GET** /line_groups | 


<a name="getCoverageLonLatLineGroups"></a>
# **getCoverageLonLatLineGroups**
> LineGroups getCoverageLonLatLineGroups(lat, lon, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
String filter = "filter_example"; // String | The filter parameter
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageLonLatLineGroups(lat, lon, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageLonLatLineGroups");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **filter** | **String**| The filter parameter | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatLineGroupsId"></a>
# **getCoverageLonLatLineGroupsId**
> LineGroups getCoverageLonLatLineGroupsId(lat, lon, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageLonLatLineGroupsId(lat, lon, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageLonLatLineGroupsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **id** | **String**| Id of the object you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriLineGroups"></a>
# **getCoverageLonLatUriLineGroups**
> LineGroups getCoverageLonLatUriLineGroups(lat, lon, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
String filter = "filter_example"; // String | The filter parameter
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageLonLatUriLineGroups(lat, lon, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageLonLatUriLineGroups");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **filter** | **String**| The filter parameter | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriLineGroupsId"></a>
# **getCoverageLonLatUriLineGroupsId**
> LineGroups getCoverageLonLatUriLineGroupsId(lat, lon, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageLonLatUriLineGroupsId(lat, lon, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageLonLatUriLineGroupsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |
 **id** | **String**| Id of the object you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionLineGroups"></a>
# **getCoverageRegionLineGroups**
> LineGroups getCoverageRegionLineGroups(region, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
String region = "region_example"; // String |  The region you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
String filter = "filter_example"; // String | The filter parameter
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageRegionLineGroups(region, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageRegionLineGroups");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **filter** | **String**| The filter parameter | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionLineGroupsId"></a>
# **getCoverageRegionLineGroupsId**
> LineGroups getCoverageRegionLineGroupsId(region, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageRegionLineGroupsId(region, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageRegionLineGroupsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **id** | **String**| Id of the object you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriLineGroups"></a>
# **getCoverageRegionUriLineGroups**
> LineGroups getCoverageRegionUriLineGroups(region, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
String filter = "filter_example"; // String | The filter parameter
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageRegionUriLineGroups(region, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageRegionUriLineGroups");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **filter** | **String**| The filter parameter | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriLineGroupsId"></a>
# **getCoverageRegionUriLineGroupsId**
> LineGroups getCoverageRegionUriLineGroupsId(region, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String externalCode = "externalCode_example"; // String | An external code to query
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getCoverageRegionUriLineGroupsId(region, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getCoverageRegionUriLineGroupsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **id** | **String**| Id of the object you want to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **externalCode** | **String**| An external code to query | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getLineGroups"></a>
# **getLineGroups**
> LineGroups getLineGroups(externalCode, startPage, count, depth, forbiddenId, forbiddenUris, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineGroupsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineGroupsApi apiInstance = new LineGroupsApi();
String externalCode = "externalCode_example"; // String | An external code to query
Integer startPage = 56; // Integer | The page where you want to start
Integer count = 25; // Integer | Number of objects you want on a page
Integer depth = 1; // Integer | The depth of your object
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
String headsign = "headsign_example"; // String | filter vehicle journeys on headsign
Boolean showCodes = true; // Boolean | show more identification codes
String odtLevel = "all"; // String | odt level
String dataFreshness = "base_schedule"; // String | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys).
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
DateTime since = new DateTime(); // DateTime | filters objects not valid before this date
DateTime until = new DateTime(); // DateTime | filters objects not valid after this date
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
String filter = "filter_example"; // String | The filter parameter
List<String> tags = Arrays.asList("tags_example"); // List<String> | If filled, will restrain the search within the given disruption tags
String originalId = "originalId_example"; // String | original uri of the object you want to query
try {
    LineGroups result = apiInstance.getLineGroups(externalCode, startPage, count, depth, forbiddenId, forbiddenUris, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags, originalId);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineGroupsApi#getLineGroups");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **externalCode** | **String**| An external code to query |
 **startPage** | **Integer**| The page where you want to start | [optional]
 **count** | **Integer**| Number of objects you want on a page | [optional] [default to 25]
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **headsign** | **String**| filter vehicle journeys on headsign | [optional]
 **showCodes** | **Boolean**| show more identification codes | [optional]
 **odtLevel** | **String**| odt level | [optional] [default to all] [enum: scheduled, all, zonal, with_stops]
 **dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). | [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **since** | **DateTime**| filters objects not valid before this date | [optional]
 **until** | **DateTime**| filters objects not valid after this date | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]
 **filter** | **String**| The filter parameter | [optional]
 **tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags | [optional]
 **originalId** | **String**| original uri of the object you want to query | [optional]

### Return type

[**LineGroups**](LineGroups.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

