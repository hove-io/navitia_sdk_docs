# EquipmentReportsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoordLonLatEquipmentReports**](EquipmentReportsApi.md#getCoordLonLatEquipmentReports) | **GET** /coord/{lon};{lat}/equipment_reports | 
[**getCoordsLonLatEquipmentReports**](EquipmentReportsApi.md#getCoordsLonLatEquipmentReports) | **GET** /coords/{lon};{lat}/equipment_reports | 
[**getCoverageLonLatEquipmentReports**](EquipmentReportsApi.md#getCoverageLonLatEquipmentReports) | **GET** /coverage/{lon};{lat}/equipment_reports | 
[**getCoverageLonLatUriEquipmentReports**](EquipmentReportsApi.md#getCoverageLonLatUriEquipmentReports) | **GET** /coverage/{lon};{lat}/{uri}/equipment_reports | 
[**getCoverageRegionEquipmentReports**](EquipmentReportsApi.md#getCoverageRegionEquipmentReports) | **GET** /coverage/{region}/equipment_reports | 
[**getCoverageRegionUriEquipmentReports**](EquipmentReportsApi.md#getCoverageRegionUriEquipmentReports) | **GET** /coverage/{region}/{uri}/equipment_reports | 


<a name="getCoordLonLatEquipmentReports"></a>
# **getCoordLonLatEquipmentReports**
> EquipmentReports getCoordLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoordLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoordLonLatEquipmentReports");
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
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoordsLonLatEquipmentReports"></a>
# **getCoordsLonLatEquipmentReports**
> EquipmentReports getCoordsLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoordsLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoordsLonLatEquipmentReports");
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
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatEquipmentReports"></a>
# **getCoverageLonLatEquipmentReports**
> EquipmentReports getCoverageLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoverageLonLatEquipmentReports(lat, lon, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoverageLonLatEquipmentReports");
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
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageLonLatUriEquipmentReports"></a>
# **getCoverageLonLatUriEquipmentReports**
> EquipmentReports getCoverageLonLatUriEquipmentReports(lat, lon, uri, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoverageLonLatUriEquipmentReports(lat, lon, uri, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoverageLonLatUriEquipmentReports");
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
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionEquipmentReports"></a>
# **getCoverageRegionEquipmentReports**
> EquipmentReports getCoverageRegionEquipmentReports(region, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
String region = "region_example"; // String |  The region you want to query
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoverageRegionEquipmentReports(region, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoverageRegionEquipmentReports");
    e.printStackTrace();
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **region** | **String**|  The region you want to query |
 **depth** | **Integer**| The depth of your object | [optional] [default to 1]
 **count** | **Integer**| Number of objects per page | [optional] [default to 25]
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getCoverageRegionUriEquipmentReports"></a>
# **getCoverageRegionUriEquipmentReports**
> EquipmentReports getCoverageRegionUriEquipmentReports(region, uri, depth, count, filter, startPage, forbiddenUris)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.EquipmentReportsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

EquipmentReportsApi apiInstance = new EquipmentReportsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
Integer depth = 1; // Integer | The depth of your object
Integer count = 25; // Integer | Number of objects per page
String filter = "filter_example"; // String | Filter your objects
Integer startPage = 56; // Integer | The current page
List<String> forbiddenUris = Arrays.asList("forbiddenUris_example"); // List<String> | forbidden uris
try {
    EquipmentReports result = apiInstance.getCoverageRegionUriEquipmentReports(region, uri, depth, count, filter, startPage, forbiddenUris);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling EquipmentReportsApi#getCoverageRegionUriEquipmentReports");
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
 **filter** | **String**| Filter your objects | [optional]
 **startPage** | **Integer**| The current page | [optional]
 **forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris | [optional]

### Return type

[**EquipmentReports**](EquipmentReports.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

