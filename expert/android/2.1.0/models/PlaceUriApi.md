---
layout: default
title: PlaceUriApi
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/PlaceUriApi
---

# PlaceUriApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatPlacesId**](#getCoverageLonLatPlacesId) | **GET** /coverage/{lon};{lat}/places/{id} | 
[**getCoverageRegionPlacesId**](#getCoverageRegionPlacesId) | **GET** /coverage/{region}/places/{id} | 
[**getPlacesId**](#getPlacesId) | **GET** /places/{id} | 


<a name="getCoverageLonLatPlacesId"></a>
# **getCoverageLonLatPlacesId**
> Places getCoverageLonLatPlacesId(lat, lon, id, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlaceUriApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlaceUriApi apiInstance = new PlaceUriApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    Places result = apiInstance.getCoverageLonLatPlacesId(lat, lon, id, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlaceUriApi#getCoverageLonLatPlacesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
-| ------------ | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **id** | **String**| Id of the object you want to query |
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**Places**](/navitia_sdk_docs/expert/android/endpoints/places)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPlacesId"></a>
# **getCoverageRegionPlacesId**
> Places getCoverageRegionPlacesId(region, id, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlaceUriApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlaceUriApi apiInstance = new PlaceUriApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    Places result = apiInstance.getCoverageRegionPlacesId(region, id, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlaceUriApi#getCoverageRegionPlacesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
-| ------------ | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **id** | **String**| Id of the object you want to query |
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**Places**](/navitia_sdk_docs/expert/android/endpoints/places)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getPlacesId"></a>
# **getPlacesId**
> Places getPlacesId(id, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlaceUriApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlaceUriApi apiInstance = new PlaceUriApi();
String id = "id_example"; // String | Id of the object you want to query
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    Places result = apiInstance.getPlacesId(id, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlaceUriApi#getPlacesId");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
-| ------------ | ------------- | ------------- | -------------
 **id** | **String**| Id of the object you want to query |
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**Places**](/navitia_sdk_docs/expert/android/endpoints/places)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

