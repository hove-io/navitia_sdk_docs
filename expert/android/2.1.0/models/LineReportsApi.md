---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# LineReportsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatLineReports**](LineReportsApi.md#getCoverageLonLatLineReports) | **GET** /coverage/{lon};{lat}/line_reports | 
[**getCoverageLonLatUriLineReports**](LineReportsApi.md#getCoverageLonLatUriLineReports) | **GET** /coverage/{lon};{lat}/{uri}/line_reports | 
[**getCoverageRegionLineReports**](LineReportsApi.md#getCoverageRegionLineReports) | **GET** /coverage/{region}/line_reports | 
[**getCoverageRegionUriLineReports**](LineReportsApi.md#getCoverageRegionUriLineReports) | **GET** /coverage/{region}/{uri}/line_reports | 


<a name="getCoverageLonLatLineReports"></a>
# **getCoverageLonLatLineReports**
> LineReports getCoverageLonLatLineReports(lat, lon, depth, count, startPage, forbiddenUris, disableGeojson, since, until)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineReportsApi apiInstance = new LineReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Boolean disableGeojson = true; // Boolean | remove geojson from the response
DateTime since = new DateTime(); // DateTime | use disruptions valid after this date
DateTime until = new DateTime(); // DateTime | use disruptions valid before this date
try {
    LineReports result = apiInstance.getCoverageLonLatLineReports(lat, lon, depth, count, startPage, forbiddenUris, disableGeojson, since, until);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineReportsApi#getCoverageLonLatLineReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 25]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **since** | **DateTime**| use disruptions valid after this date | [optional]
 **until** | **DateTime**| use disruptions valid before this date | [optional]

### Return type

[**LineReports**](LineReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriLineReports"></a>
# **getCoverageLonLatUriLineReports**
> LineReports getCoverageLonLatUriLineReports(lat, lon, uri, depth, count, startPage, forbiddenUris, disableGeojson, since, until)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineReportsApi apiInstance = new LineReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Boolean disableGeojson = true; // Boolean | remove geojson from the response
DateTime since = new DateTime(); // DateTime | use disruptions valid after this date
DateTime until = new DateTime(); // DateTime | use disruptions valid before this date
try {
    LineReports result = apiInstance.getCoverageLonLatUriLineReports(lat, lon, uri, depth, count, startPage, forbiddenUris, disableGeojson, since, until);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineReportsApi#getCoverageLonLatUriLineReports");
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
 **count** | **Integer**| Number of objects per page | [optional] [default to 25]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **since** | **DateTime**| use disruptions valid after this date | [optional]
 **until** | **DateTime**| use disruptions valid before this date | [optional]

### Return type

[**LineReports**](LineReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionLineReports"></a>
# **getCoverageRegionLineReports**
> LineReports getCoverageRegionLineReports(region, depth, count, startPage, forbiddenUris, disableGeojson, since, until)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineReportsApi apiInstance = new LineReportsApi();
String region = "region_example"; // String |  The region you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Boolean disableGeojson = true; // Boolean | remove geojson from the response
DateTime since = new DateTime(); // DateTime | use disruptions valid after this date
DateTime until = new DateTime(); // DateTime | use disruptions valid before this date
try {
    LineReports result = apiInstance.getCoverageRegionLineReports(region, depth, count, startPage, forbiddenUris, disableGeojson, since, until);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineReportsApi#getCoverageRegionLineReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 25]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **since** | **DateTime**| use disruptions valid after this date | [optional]
 **until** | **DateTime**| use disruptions valid before this date | [optional]

### Return type

[**LineReports**](LineReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriLineReports"></a>
# **getCoverageRegionUriLineReports**
> LineReports getCoverageRegionUriLineReports(region, uri, depth, count, startPage, forbiddenUris, disableGeojson, since, until)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.LineReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

LineReportsApi apiInstance = new LineReportsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Boolean disableGeojson = true; // Boolean | remove geojson from the response
DateTime since = new DateTime(); // DateTime | use disruptions valid after this date
DateTime until = new DateTime(); // DateTime | use disruptions valid before this date
try {
    LineReports result = apiInstance.getCoverageRegionUriLineReports(region, uri, depth, count, startPage, forbiddenUris, disableGeojson, since, until);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling LineReportsApi#getCoverageRegionUriLineReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 25]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **since** | **DateTime**| use disruptions valid after this date | [optional]
 **until** | **DateTime**| use disruptions valid before this date | [optional]

### Return type

[**LineReports**](LineReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

