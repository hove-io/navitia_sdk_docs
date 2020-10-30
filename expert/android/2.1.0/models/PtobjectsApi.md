# PtobjectsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatPtObjects**](PtobjectsApi.md#getCoverageLonLatPtObjects) | **GET** /coverage/{lon};{lat}/pt_objects | 
[**getCoverageRegionPtObjects**](PtobjectsApi.md#getCoverageRegionPtObjects) | **GET** /coverage/{region}/pt_objects | 


<a name="getCoverageLonLatPtObjects"></a>
# **getCoverageLonLatPtObjects**
> PtObjects getCoverageLonLatPtObjects(q, lat, lon, type, count, adminUri, depth, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PtobjectsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PtobjectsApi apiInstance = new PtobjectsApi();
String q = "q_example"; // String | The data to search
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
List<String> type = Arrays.asList("[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"); // List<String> | The type of data to search
Integer count = 10; // Integer | The maximum number of ptobjects returned
List<String> adminUri = Arrays.asList("adminUri_example"); // List<String> | If filled, will restrain the search within the given admin uris
Integer depth = 1; // Integer | The depth of objects
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PtObjects result = apiInstance.getCoverageLonLatPtObjects(q, lat, lon, type, count, adminUri, depth, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PtobjectsApi#getCoverageLonLatPtObjects");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **q** | **String**| The data to search |
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| The type of data to search | [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point]
 **count** | **Integer**| The maximum number of ptobjects returned | [optional] [default to 10]
 **adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris | [optional]
 **depth** | **Integer**| The depth of objects | [optional] [default to 1]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PtObjects**](PtObjects.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPtObjects"></a>
# **getCoverageRegionPtObjects**
> PtObjects getCoverageRegionPtObjects(q, region, type, count, adminUri, depth, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PtobjectsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PtobjectsApi apiInstance = new PtobjectsApi();
String q = "q_example"; // String | The data to search
String region = "region_example"; // String |  The region you want to query
List<String> type = Arrays.asList("[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"); // List<String> | The type of data to search
Integer count = 10; // Integer | The maximum number of ptobjects returned
List<String> adminUri = Arrays.asList("adminUri_example"); // List<String> | If filled, will restrain the search within the given admin uris
Integer depth = 1; // Integer | The depth of objects
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PtObjects result = apiInstance.getCoverageRegionPtObjects(q, region, type, count, adminUri, depth, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PtobjectsApi#getCoverageRegionPtObjects");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **q** | **String**| The data to search |
 **region** | **String**|  The region you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| The type of data to search | [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point]
 **count** | **Integer**| The maximum number of ptobjects returned | [optional] [default to 10]
 **adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris | [optional]
 **depth** | **Integer**| The depth of objects | [optional] [default to 1]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PtObjects**](PtObjects.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

