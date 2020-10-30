---
layout: default
title: GeoStatusApi
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/GeoStatusApi
---

# GeoStatusApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatGeoStatus**](#getCoverageLonLatGeoStatus) | **GET** /coverage/{lon};{lat}/_geo_status | 
[**getCoverageRegionGeoStatus**](#getCoverageRegionGeoStatus) | **GET** /coverage/{region}/_geo_status | 


<a name="getCoverageLonLatGeoStatus"></a>
# **getCoverageLonLatGeoStatus**
> GeoStatus1 getCoverageLonLatGeoStatus(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.GeoStatusApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

GeoStatusApi apiInstance = new GeoStatusApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    GeoStatus1 result = apiInstance.getCoverageLonLatGeoStatus(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling GeoStatusApi#getCoverageLonLatGeoStatus");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
-| ------------ | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |

### Return type

[**GeoStatus1**](/navitia_sdk_docs/expert/android/endpoints/geo_status1)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionGeoStatus"></a>
# **getCoverageRegionGeoStatus**
> GeoStatus1 getCoverageRegionGeoStatus(region)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.GeoStatusApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

GeoStatusApi apiInstance = new GeoStatusApi();
String region = "region_example"; // String |  The region you want to query
try {
    GeoStatus1 result = apiInstance.getCoverageRegionGeoStatus(region);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling GeoStatusApi#getCoverageRegionGeoStatus");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
-| ------------ | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |

### Return type

[**GeoStatus1**](/navitia_sdk_docs/expert/android/endpoints/geo_status1)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

