---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# CalendarsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatCalendars**](CalendarsApi.md#getCoverageLonLatCalendars) | **GET** /coverage/{lon};{lat}/calendars | 
[**getCoverageLonLatCalendarsId**](CalendarsApi.md#getCoverageLonLatCalendarsId) | **GET** /coverage/{lon};{lat}/calendars/{id} | 
[**getCoverageLonLatUriCalendars**](CalendarsApi.md#getCoverageLonLatUriCalendars) | **GET** /coverage/{lon};{lat}/{uri}/calendars | 
[**getCoverageRegionCalendars**](CalendarsApi.md#getCoverageRegionCalendars) | **GET** /coverage/{region}/calendars | 
[**getCoverageRegionCalendarsId**](CalendarsApi.md#getCoverageRegionCalendarsId) | **GET** /coverage/{region}/calendars/{id} | 
[**getCoverageRegionUriCalendars**](CalendarsApi.md#getCoverageRegionUriCalendars) | **GET** /coverage/{region}/{uri}/calendars | 


<a name="getCoverageLonLatCalendars"></a>
# **getCoverageLonLatCalendars**
> Calendars getCoverageLonLatCalendars(lat, lon, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageLonLatCalendars(lat, lon, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageLonLatCalendars");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatCalendarsId"></a>
# **getCoverageLonLatCalendarsId**
> Calendars getCoverageLonLatCalendarsId(lat, lon, id, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageLonLatCalendarsId(lat, lon, id, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageLonLatCalendarsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **id** | **String**| Id of the object you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriCalendars"></a>
# **getCoverageLonLatUriCalendars**
> Calendars getCoverageLonLatUriCalendars(lat, lon, uri, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageLonLatUriCalendars(lat, lon, uri, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageLonLatUriCalendars");
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
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionCalendars"></a>
# **getCoverageRegionCalendars**
> Calendars getCoverageRegionCalendars(region, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
String region = "region_example"; // String |  The region you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageRegionCalendars(region, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageRegionCalendars");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionCalendarsId"></a>
# **getCoverageRegionCalendarsId**
> Calendars getCoverageRegionCalendarsId(region, id, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageRegionCalendarsId(region, id, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageRegionCalendarsId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **id** | **String**| Id of the object you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriCalendars"></a>
# **getCoverageRegionUriCalendars**
> Calendars getCoverageRegionUriCalendars(region, uri, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CalendarsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CalendarsApi apiInstance = new CalendarsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 10; // Integer | Number of calendars per page
Integer startPage = 56; // Integer | The current page
String startDate = "startDate_example"; // String | Start date
String endDate = "endDate_example"; // String | End date
List<String> forbiddenId = Arrays.asList("forbiddenId_example"); // List<String> | DEPRECATED, replaced by `forbidden_uris[]`
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
Integer distance = 200; // Integer | Distance range of the query. Used only if a coord is in the query
try {
    Calendars result = apiInstance.getCoverageRegionUriCalendars(region, uri, depth, count, startPage, startDate, endDate, forbiddenId, forbiddenUris, distance);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CalendarsApi#getCoverageRegionUriCalendars");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of calendars per page | [optional] [default to 10]
 **startPage** | **Integer**| The current page | [optional]
 **startDate** | **String**| Start date | [optional]
 **endDate** | **String**| End date | [optional]
 **forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]
 **distance** | **Integer**| Distance range of the query. Used only if a coord is in the query | [optional] [default to 200]

### Return type

[**Calendars**](Calendars.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

