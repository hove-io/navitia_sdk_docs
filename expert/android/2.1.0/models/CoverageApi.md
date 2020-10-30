# CoverageApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverage**](CoverageApi.md#getCoverage) | **GET** /coverage/ | 
[**getCoverageLonLat**](CoverageApi.md#getCoverageLonLat) | **GET** /coverage/{lon};{lat}/ | 
[**getCoverageRegion**](CoverageApi.md#getCoverageRegion) | **GET** /coverage/{region}/ | 


<a name="getCoverage"></a>
# **getCoverage**
> Coverages getCoverage(disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoverageApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoverageApi apiInstance = new CoverageApi();
Boolean disableGeojson = true; // Boolean | hide the coverage geojson to reduce response size
try {
    Coverages result = apiInstance.getCoverage(disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoverageApi#getCoverage");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size | [optional]

### Return type

[**Coverages**](Coverages.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLat"></a>
# **getCoverageLonLat**
> Coverages getCoverageLonLat(lat, lon, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoverageApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoverageApi apiInstance = new CoverageApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Boolean disableGeojson = true; // Boolean | hide the coverage geojson to reduce response size
try {
    Coverages result = apiInstance.getCoverageLonLat(lat, lon, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoverageApi#getCoverageLonLat");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size | [optional]

### Return type

[**Coverages**](Coverages.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegion"></a>
# **getCoverageRegion**
> Coverages getCoverageRegion(region, disableGeojson)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoverageApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoverageApi apiInstance = new CoverageApi();
String region = "region_example"; // String |  The region you want to query
Boolean disableGeojson = true; // Boolean | hide the coverage geojson to reduce response size
try {
    Coverages result = apiInstance.getCoverageRegion(region, disableGeojson);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoverageApi#getCoverageRegion");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size | [optional]

### Return type

[**Coverages**](Coverages.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

