---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# PlacesApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatPlaces**](PlacesApi.md#getCoverageLonLatPlaces) | **GET** /coverage/{lon};{lat}/places | 
[**getCoverageRegionPlaces**](PlacesApi.md#getCoverageRegionPlaces) | **GET** /coverage/{region}/places | 
[**getPlaces**](PlacesApi.md#getPlaces) | **GET** /places | 


<a name="getCoverageLonLatPlaces"></a>
# **getCoverageLonLatPlaces**
> Places getCoverageLonLatPlaces(q, lat, lon, type, count, adminUri, depth, disableGeojson, from, shape)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesApi apiInstance = new PlacesApi();
String q = "q_example"; // String | The data to search
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
List<String> type = Arrays.asList("[u'stop_area', u'address', u'poi', u'administrative_region']"); // List<String> | The type of data to search
Integer count = 10; // Integer | The maximum number of places returned
List<String> adminUri = Arrays.asList("adminUri_example"); // List<String> | If filled, will restrain the search within the given admin uris
Integer depth = 1; // Integer | The depth of objects
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String from = "from_example"; // String | Coordinates longitude;latitude used to prioritize the objects around this coordinate
String shape = "shape_example"; // String | Geographical shape to limit the search.
try {
    Places result = apiInstance.getCoverageLonLatPlaces(q, lat, lon, type, count, adminUri, depth, disableGeojson, from, shape);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesApi#getCoverageLonLatPlaces");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **q** | **String**| The data to search |
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| The type of data to search | [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **count** | **Integer**| The maximum number of places returned | [optional] [default to 10]
 **adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris | [optional]
 **depth** | **Integer**| The depth of objects | [optional] [default to 1]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate | [optional]
 **shape** | **String**| Geographical shape to limit the search. | [optional]

### Return type

[**Places**](Places.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPlaces"></a>
# **getCoverageRegionPlaces**
> Places getCoverageRegionPlaces(q, region, type, count, adminUri, depth, disableGeojson, from, shape)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesApi apiInstance = new PlacesApi();
String q = "q_example"; // String | The data to search
String region = "region_example"; // String |  The region you want to query
List<String> type = Arrays.asList("[u'stop_area', u'address', u'poi', u'administrative_region']"); // List<String> | The type of data to search
Integer count = 10; // Integer | The maximum number of places returned
List<String> adminUri = Arrays.asList("adminUri_example"); // List<String> | If filled, will restrain the search within the given admin uris
Integer depth = 1; // Integer | The depth of objects
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String from = "from_example"; // String | Coordinates longitude;latitude used to prioritize the objects around this coordinate
String shape = "shape_example"; // String | Geographical shape to limit the search.
try {
    Places result = apiInstance.getCoverageRegionPlaces(q, region, type, count, adminUri, depth, disableGeojson, from, shape);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesApi#getCoverageRegionPlaces");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **q** | **String**| The data to search |
 **region** | **String**|  The region you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| The type of data to search | [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **count** | **Integer**| The maximum number of places returned | [optional] [default to 10]
 **adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris | [optional]
 **depth** | **Integer**| The depth of objects | [optional] [default to 1]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate | [optional]
 **shape** | **String**| Geographical shape to limit the search. | [optional]

### Return type

[**Places**](Places.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getPlaces"></a>
# **getPlaces**
> Places getPlaces(q, type, count, adminUri, depth, disableGeojson, from, shape)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesApi apiInstance = new PlacesApi();
String q = "q_example"; // String | The data to search
List<String> type = Arrays.asList("[u'stop_area', u'address', u'poi', u'administrative_region']"); // List<String> | The type of data to search
Integer count = 10; // Integer | The maximum number of places returned
List<String> adminUri = Arrays.asList("adminUri_example"); // List<String> | If filled, will restrain the search within the given admin uris
Integer depth = 1; // Integer | The depth of objects
Boolean disableGeojson = true; // Boolean | remove geojson from the response
String from = "from_example"; // String | Coordinates longitude;latitude used to prioritize the objects around this coordinate
String shape = "shape_example"; // String | Geographical shape to limit the search.
try {
    Places result = apiInstance.getPlaces(q, type, count, adminUri, depth, disableGeojson, from, shape);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesApi#getPlaces");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **q** | **String**| The data to search |
 **type** | [**List&lt;String&gt;**](String.md)| The type of data to search | [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **count** | **Integer**| The maximum number of places returned | [optional] [default to 10]
 **adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris | [optional]
 **depth** | **Integer**| The depth of objects | [optional] [default to 1]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate | [optional]
 **shape** | **String**| Geographical shape to limit the search. | [optional]

### Return type

[**Places**](Places.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

