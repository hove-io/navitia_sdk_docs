# PlacesNearbyApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoordLonLatPlacesNearby**](PlacesNearbyApi.md#getCoordLonLatPlacesNearby) | **GET** /coord/{lon};{lat}/places_nearby | 
[**getCoordsLonLatPlacesNearby**](PlacesNearbyApi.md#getCoordsLonLatPlacesNearby) | **GET** /coords/{lon};{lat}/places_nearby | 
[**getCoverageLonLatPlacesNearby**](PlacesNearbyApi.md#getCoverageLonLatPlacesNearby) | **GET** /coverage/{lon};{lat}/places_nearby | 
[**getCoverageLonLatUriPlacesNearby**](PlacesNearbyApi.md#getCoverageLonLatUriPlacesNearby) | **GET** /coverage/{lon};{lat}/{uri}/places_nearby | 
[**getCoverageRegionPlacesNearby**](PlacesNearbyApi.md#getCoverageRegionPlacesNearby) | **GET** /coverage/{region}/places_nearby | 
[**getCoverageRegionUriPlacesNearby**](PlacesNearbyApi.md#getCoverageRegionUriPlacesNearby) | **GET** /coverage/{region}/{uri}/places_nearby | 


<a name="getCoordLonLatPlacesNearby"></a>
# **getCoordLonLatPlacesNearby**
> PlacesNearby getCoordLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoordLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoordLonLatPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoordsLonLatPlacesNearby"></a>
# **getCoordsLonLatPlacesNearby**
> PlacesNearby getCoordsLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoordsLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoordsLonLatPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatPlacesNearby"></a>
# **getCoverageLonLatPlacesNearby**
> PlacesNearby getCoverageLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoverageLonLatPlacesNearby(lat, lon, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoverageLonLatPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriPlacesNearby"></a>
# **getCoverageLonLatUriPlacesNearby**
> PlacesNearby getCoverageLonLatUriPlacesNearby(lat, lon, uri, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoverageLonLatUriPlacesNearby(lat, lon, uri, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoverageLonLatUriPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **lat** | **BigDecimal**|  The latitude of where the coord you want to query |
 **lon** | **BigDecimal**|  The longitude of where the coord you want to query |
 **uri** | **String**| First part of the uri |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionPlacesNearby"></a>
# **getCoverageRegionPlacesNearby**
> PlacesNearby getCoverageRegionPlacesNearby(region, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
String region = "region_example"; // String |  The region you want to query
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoverageRegionPlacesNearby(region, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoverageRegionPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriPlacesNearby"></a>
# **getCoverageRegionUriPlacesNearby**
> PlacesNearby getCoverageRegionUriPlacesNearby(region, uri, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.PlacesNearbyApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

PlacesNearbyApi apiInstance = new PlacesNearbyApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
List<String> type = Arrays.asList("[u'stop_area', u'stop_point', u'poi']"); // List<String> | Type of the objects to return
String filter = "filter_example"; // String | Filter your objects
Integer distance = 500; // Integer | Distance range of the query in meters
Integer count = 10; // Integer | Elements per page
Integer depth = 1; // Integer | Maximum depth on objects
Integer startPage = 56; // Integer | The page number of the ptref result
Boolean bssStands = true; // Boolean | DEPRECATED, Use add_poi_infos[]=bss_stands
List<String> addPoiInfos = Arrays.asList("[u'bss_stands', u'car_park']"); // List<String> | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response
Boolean disableGeojson = true; // Boolean | remove geojson from the response
Boolean disableDisruption = true; // Boolean | remove disruptions from the response
try {
    PlacesNearby result = apiInstance.getCoverageRegionUriPlacesNearby(region, uri, type, filter, distance, count, depth, startPage, bssStands, addPoiInfos, disableGeojson, disableDisruption);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling PlacesNearbyApi#getCoverageRegionUriPlacesNearby");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **uri** | **String**| First part of the uri |
 **type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return | [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address]
 **filter** | **String**| Filter your objects | [optional]
 **distance** | **Integer**| Distance range of the query in meters | [optional] [default to 500]
 **count** | **Integer**| Elements per page | [optional] [default to 10]
 **depth** | **Integer**| Maximum depth on objects | [optional] [default to 1]
 **startPage** | **Integer**| The page number of the ptref result | [optional]
 **bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands | [optional]
 **addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response | [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none]
 **disableGeojson** | **Boolean**| remove geojson from the response | [optional]
 **disableDisruption** | **Boolean**| remove disruptions from the response | [optional]

### Return type

[**PlacesNearby**](PlacesNearby.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

