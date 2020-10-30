---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# CoordApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoordLonLat**](CoordApi.md#getCoordLonLat) | **GET** /coord/{lon};{lat}/ | 
[**getCoordsLonLat**](CoordApi.md#getCoordsLonLat) | **GET** /coords/{lon};{lat}/ | 
[**getCoverageRegionCoordLonLatAddresses**](CoordApi.md#getCoverageRegionCoordLonLatAddresses) | **GET** /coverage/{region}/coord/{lon};{lat}/addresses | 
[**getCoverageRegionCoordsLonLatAddresses**](CoordApi.md#getCoverageRegionCoordsLonLatAddresses) | **GET** /coverage/{region}/coords/{lon};{lat}/addresses | 


<a name="getCoordLonLat"></a>
# **getCoordLonLat**
> DictAddresses getCoordLonLat(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordApi apiInstance = new CoordApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoordLonLat(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordApi#getCoordLonLat");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoordsLonLat"></a>
# **getCoordsLonLat**
> DictAddresses getCoordsLonLat(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordApi apiInstance = new CoordApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoordsLonLat(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordApi#getCoordsLonLat");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionCoordLonLatAddresses"></a>
# **getCoverageRegionCoordLonLatAddresses**
> DictAddresses getCoverageRegionCoordLonLatAddresses(lat, region, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordApi apiInstance = new CoordApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
String region = "region_example"; // String |  The region you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoordLonLatAddresses(lat, region, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordApi#getCoverageRegionCoordLonLatAddresses");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **region** | **String**|  The region you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionCoordsLonLatAddresses"></a>
# **getCoverageRegionCoordsLonLatAddresses**
> DictAddresses getCoverageRegionCoordsLonLatAddresses(lat, region, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordApi apiInstance = new CoordApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
String region = "region_example"; // String |  The region you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoordsLonLatAddresses(lat, region, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordApi#getCoverageRegionCoordsLonLatAddresses");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **region** | **String**|  The region you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

