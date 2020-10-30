# PhysicalModesApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatPhysicalModes**](PhysicalModesApi.md#getCoverageLonLatPhysicalModes) | **GET** /coverage/{lon};{lat}/physical_modes | 
[**getCoverageLonLatPhysicalModesId**](PhysicalModesApi.md#getCoverageLonLatPhysicalModesId) | **GET** /coverage/{lon};{lat}/physical_modes/{id} | 
[**getCoverageLonLatUriPhysicalModes**](PhysicalModesApi.md#getCoverageLonLatUriPhysicalModes) | **GET** /coverage/{lon};{lat}/{uri}/physical_modes | 
[**getCoverageLonLatUriPhysicalModesId**](PhysicalModesApi.md#getCoverageLonLatUriPhysicalModesId) | **GET** /coverage/{lon};{lat}/{uri}/physical_modes/{id} | 
[**getCoverageRegionPhysicalModes**](PhysicalModesApi.md#getCoverageRegionPhysicalModes) | **GET** /coverage/{region}/physical_modes | 
[**getCoverageRegionPhysicalModesId**](PhysicalModesApi.md#getCoverageRegionPhysicalModesId) | **GET** /coverage/{region}/physical_modes/{id} | 
[**getCoverageRegionUriPhysicalModes**](PhysicalModesApi.md#getCoverageRegionUriPhysicalModes) | **GET** /coverage/{region}/{uri}/physical_modes | 
[**getCoverageRegionUriPhysicalModesId**](PhysicalModesApi.md#getCoverageRegionUriPhysicalModesId) | **GET** /coverage/{region}/{uri}/physical_modes/{id} | 


<a name="getCoverageLonLatPhysicalModes"></a>
# **getCoverageLonLatPhysicalModes**
> PhysicalModes getCoverageLonLatPhysicalModes(lat, lon, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageLonLatPhysicalModes(lat, lon, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageLonLatPhysicalModes");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatPhysicalModesId"></a>
# **getCoverageLonLatPhysicalModesId**
> PhysicalModes getCoverageLonLatPhysicalModesId(lat, lon, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageLonLatPhysicalModesId(lat, lon, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageLonLatPhysicalModesId");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriPhysicalModes"></a>
# **getCoverageLonLatUriPhysicalModes**
> PhysicalModes getCoverageLonLatUriPhysicalModes(lat, lon, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageLonLatUriPhysicalModes(lat, lon, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageLonLatUriPhysicalModes");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriPhysicalModesId"></a>
# **getCoverageLonLatUriPhysicalModesId**
> PhysicalModes getCoverageLonLatUriPhysicalModesId(lat, lon, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageLonLatUriPhysicalModesId(lat, lon, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageLonLatUriPhysicalModesId");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPhysicalModes"></a>
# **getCoverageRegionPhysicalModes**
> PhysicalModes getCoverageRegionPhysicalModes(region, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageRegionPhysicalModes(region, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageRegionPhysicalModes");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPhysicalModesId"></a>
# **getCoverageRegionPhysicalModesId**
> PhysicalModes getCoverageRegionPhysicalModesId(region, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageRegionPhysicalModesId(region, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageRegionPhysicalModesId");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriPhysicalModes"></a>
# **getCoverageRegionUriPhysicalModes**
> PhysicalModes getCoverageRegionUriPhysicalModes(region, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageRegionUriPhysicalModes(region, uri, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, filter, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageRegionUriPhysicalModes");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriPhysicalModesId"></a>
# **getCoverageRegionUriPhysicalModesId**
> PhysicalModes getCoverageRegionUriPhysicalModesId(region, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PhysicalModesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PhysicalModesApi apiInstance = new PhysicalModesApi();
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
try {
    PhysicalModes result = apiInstance.getCoverageRegionUriPhysicalModesId(region, uri, id, startPage, count, depth, forbiddenId, forbiddenUris, externalCode, headsign, showCodes, odtLevel, dataFreshness, distance, since, until, disableGeojson, disableDisruption, tags);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PhysicalModesApi#getCoverageRegionUriPhysicalModesId");
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

### Return type

[**PhysicalModes**](PhysicalModes.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

