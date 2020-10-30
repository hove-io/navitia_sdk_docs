---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# TrafficReportApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatTrafficReports**](TrafficReportApi.md#getCoverageLonLatTrafficReports) | **GET** /coverage/{lon};{lat}/traffic_reports | 
[**getCoverageLonLatUriTrafficReports**](TrafficReportApi.md#getCoverageLonLatUriTrafficReports) | **GET** /coverage/{lon};{lat}/{uri}/traffic_reports | 
[**getCoverageRegionTrafficReports**](TrafficReportApi.md#getCoverageRegionTrafficReports) | **GET** /coverage/{region}/traffic_reports | 
[**getCoverageRegionUriTrafficReports**](TrafficReportApi.md#getCoverageRegionUriTrafficReports) | **GET** /coverage/{region}/{uri}/traffic_reports | 


<a name="getCoverageLonLatTrafficReports"></a>
# **getCoverageLonLatTrafficReports**
> TrafficReports getCoverageLonLatTrafficReports(lat, lon, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.TrafficReportApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

TrafficReportApi apiInstance = new TrafficReportApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean disableGeojson = true; // Boolean | remove geojson from the response
try {
    TrafficReports result = apiInstance.getCoverageLonLatTrafficReports(lat, lon, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling TrafficReportApi#getCoverageLonLatTrafficReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]

### Return type

[**TrafficReports**](TrafficReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriTrafficReports"></a>
# **getCoverageLonLatUriTrafficReports**
> TrafficReports getCoverageLonLatUriTrafficReports(lat, lon, uri, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.TrafficReportApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

TrafficReportApi apiInstance = new TrafficReportApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean disableGeojson = true; // Boolean | remove geojson from the response
try {
    TrafficReports result = apiInstance.getCoverageLonLatUriTrafficReports(lat, lon, uri, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling TrafficReportApi#getCoverageLonLatUriTrafficReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]

### Return type

[**TrafficReports**](TrafficReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionTrafficReports"></a>
# **getCoverageRegionTrafficReports**
> TrafficReports getCoverageRegionTrafficReports(region, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.TrafficReportApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

TrafficReportApi apiInstance = new TrafficReportApi();
String region = "region_example"; // String |  The region you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean disableGeojson = true; // Boolean | remove geojson from the response
try {
    TrafficReports result = apiInstance.getCoverageRegionTrafficReports(region, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling TrafficReportApi#getCoverageRegionTrafficReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]

### Return type

[**TrafficReports**](TrafficReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriTrafficReports"></a>
# **getCoverageRegionUriTrafficReports**
> TrafficReports getCoverageRegionUriTrafficReports(region, uri, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.TrafficReportApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

TrafficReportApi apiInstance = new TrafficReportApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
Boolean disableGeojson = true; // Boolean | remove geojson from the response
try {
    TrafficReports result = apiInstance.getCoverageRegionUriTrafficReports(region, uri, depth, count, startPage, forbiddenId, forbiddenUris, distance, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling TrafficReportApi#getCoverageRegionUriTrafficReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]

### Return type

[**TrafficReports**](TrafficReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

