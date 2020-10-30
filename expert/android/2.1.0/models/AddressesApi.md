---
layout: default
title: AddressesApi
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/AddressesApi.md
---

# AddressesApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatAddresses**](AddressesApi.md#getCoverageLonLatAddresses) | **GET** /coverage/{lon};{lat}/addresses | 
[**getCoverageLonLatAddressesId**](AddressesApi.md#getCoverageLonLatAddressesId) | **GET** /coverage/{lon};{lat}/addresses/{id} | 
[**getCoverageLonLatUriAddresses**](AddressesApi.md#getCoverageLonLatUriAddresses) | **GET** /coverage/{lon};{lat}/{uri}/addresses | 
[**getCoverageLonLatUriAddressesId**](AddressesApi.md#getCoverageLonLatUriAddressesId) | **GET** /coverage/{lon};{lat}/{uri}/addresses/{id} | 
[**getCoverageRegionAddresses**](AddressesApi.md#getCoverageRegionAddresses) | **GET** /coverage/{region}/addresses | 
[**getCoverageRegionAddressesId**](AddressesApi.md#getCoverageRegionAddressesId) | **GET** /coverage/{region}/addresses/{id} | 
[**getCoverageRegionUriAddresses**](AddressesApi.md#getCoverageRegionUriAddresses) | **GET** /coverage/{region}/{uri}/addresses | 
[**getCoverageRegionUriAddressesId**](AddressesApi.md#getCoverageRegionUriAddressesId) | **GET** /coverage/{region}/{uri}/addresses/{id} | 


<a name="getCoverageLonLatAddresses"></a>
# **getCoverageLonLatAddresses**
> DictAddresses getCoverageLonLatAddresses(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatAddresses(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageLonLatAddresses");
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

<a name="getCoverageLonLatAddressesId"></a>
# **getCoverageLonLatAddressesId**
> DictAddresses getCoverageLonLatAddressesId(lat, lon, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatAddressesId(lat, lon, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageLonLatAddressesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **id** | **String**| Id of the object you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriAddresses"></a>
# **getCoverageLonLatUriAddresses**
> DictAddresses getCoverageLonLatUriAddresses(lat, lon, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriAddresses(lat, lon, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageLonLatUriAddresses");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriAddressesId"></a>
# **getCoverageLonLatUriAddressesId**
> DictAddresses getCoverageLonLatUriAddressesId(lat, lon, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriAddressesId(lat, lon, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageLonLatUriAddressesId");
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

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionAddresses"></a>
# **getCoverageRegionAddresses**
> DictAddresses getCoverageRegionAddresses(region)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
String region = "region_example"; // String |  The region you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionAddresses(region);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageRegionAddresses");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionAddressesId"></a>
# **getCoverageRegionAddressesId**
> DictAddresses getCoverageRegionAddressesId(region, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionAddressesId(region, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageRegionAddressesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **id** | **String**| Id of the object you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriAddresses"></a>
# **getCoverageRegionUriAddresses**
> DictAddresses getCoverageRegionUriAddresses(region, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageRegionUriAddresses(region, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageRegionUriAddresses");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriAddressesId"></a>
# **getCoverageRegionUriAddressesId**
> DictAddresses getCoverageRegionUriAddressesId(region, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.AddressesApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

AddressesApi apiInstance = new AddressesApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionUriAddressesId(region, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling AddressesApi#getCoverageRegionUriAddressesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **id** | **String**| Id of the object you want to query |

### Return type

[**DictAddresses**](DictAddresses.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

