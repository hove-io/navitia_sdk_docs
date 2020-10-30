# CoordsApi

All URIs are relative to *https://api.navitia.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCoverageLonLatCoord**](CoordsApi.md#getCoverageLonLatCoord) | **GET** /coverage/{lon};{lat}/coord | 
[**getCoverageLonLatCoordId**](CoordsApi.md#getCoverageLonLatCoordId) | **GET** /coverage/{lon};{lat}/coord/{id} | 
[**getCoverageLonLatCoords**](CoordsApi.md#getCoverageLonLatCoords) | **GET** /coverage/{lon};{lat}/coords | 
[**getCoverageLonLatCoordsId**](CoordsApi.md#getCoverageLonLatCoordsId) | **GET** /coverage/{lon};{lat}/coords/{id} | 
[**getCoverageLonLatUriCoord**](CoordsApi.md#getCoverageLonLatUriCoord) | **GET** /coverage/{lon};{lat}/{uri}/coord | 
[**getCoverageLonLatUriCoordId**](CoordsApi.md#getCoverageLonLatUriCoordId) | **GET** /coverage/{lon};{lat}/{uri}/coord/{id} | 
[**getCoverageLonLatUriCoords**](CoordsApi.md#getCoverageLonLatUriCoords) | **GET** /coverage/{lon};{lat}/{uri}/coords | 
[**getCoverageLonLatUriCoordsId**](CoordsApi.md#getCoverageLonLatUriCoordsId) | **GET** /coverage/{lon};{lat}/{uri}/coords/{id} | 
[**getCoverageRegionCoord**](CoordsApi.md#getCoverageRegionCoord) | **GET** /coverage/{region}/coord | 
[**getCoverageRegionCoordId**](CoordsApi.md#getCoverageRegionCoordId) | **GET** /coverage/{region}/coord/{id} | 
[**getCoverageRegionCoords**](CoordsApi.md#getCoverageRegionCoords) | **GET** /coverage/{region}/coords | 
[**getCoverageRegionCoordsId**](CoordsApi.md#getCoverageRegionCoordsId) | **GET** /coverage/{region}/coords/{id} | 
[**getCoverageRegionUriCoord**](CoordsApi.md#getCoverageRegionUriCoord) | **GET** /coverage/{region}/{uri}/coord | 
[**getCoverageRegionUriCoordId**](CoordsApi.md#getCoverageRegionUriCoordId) | **GET** /coverage/{region}/{uri}/coord/{id} | 
[**getCoverageRegionUriCoords**](CoordsApi.md#getCoverageRegionUriCoords) | **GET** /coverage/{region}/{uri}/coords | 
[**getCoverageRegionUriCoordsId**](CoordsApi.md#getCoverageRegionUriCoordsId) | **GET** /coverage/{region}/{uri}/coords/{id} | 


<a name="getCoverageLonLatCoord"></a>
# **getCoverageLonLatCoord**
> DictAddresses getCoverageLonLatCoord(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatCoord(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatCoord");
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

<a name="getCoverageLonLatCoordId"></a>
# **getCoverageLonLatCoordId**
> DictAddresses getCoverageLonLatCoordId(lat, lon, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatCoordId(lat, lon, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatCoordId");
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

<a name="getCoverageLonLatCoords"></a>
# **getCoverageLonLatCoords**
> DictAddresses getCoverageLonLatCoords(lat, lon)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatCoords(lat, lon);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatCoords");
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

<a name="getCoverageLonLatCoordsId"></a>
# **getCoverageLonLatCoordsId**
> DictAddresses getCoverageLonLatCoordsId(lat, lon, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatCoordsId(lat, lon, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatCoordsId");
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

<a name="getCoverageLonLatUriCoord"></a>
# **getCoverageLonLatUriCoord**
> DictAddresses getCoverageLonLatUriCoord(lat, lon, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriCoord(lat, lon, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatUriCoord");
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

<a name="getCoverageLonLatUriCoordId"></a>
# **getCoverageLonLatUriCoordId**
> DictAddresses getCoverageLonLatUriCoordId(lat, lon, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriCoordId(lat, lon, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatUriCoordId");
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

<a name="getCoverageLonLatUriCoords"></a>
# **getCoverageLonLatUriCoords**
> DictAddresses getCoverageLonLatUriCoords(lat, lon, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriCoords(lat, lon, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatUriCoords");
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

<a name="getCoverageLonLatUriCoordsId"></a>
# **getCoverageLonLatUriCoordsId**
> DictAddresses getCoverageLonLatUriCoordsId(lat, lon, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
BigDecimal lat = new BigDecimal(); // BigDecimal |  The latitude of where the coord you want to query
BigDecimal lon = new BigDecimal(); // BigDecimal |  The longitude of where the coord you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageLonLatUriCoordsId(lat, lon, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageLonLatUriCoordsId");
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

<a name="getCoverageRegionCoord"></a>
# **getCoverageRegionCoord**
> DictAddresses getCoverageRegionCoord(region)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoord(region);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionCoord");
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

<a name="getCoverageRegionCoordId"></a>
# **getCoverageRegionCoordId**
> DictAddresses getCoverageRegionCoordId(region, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoordId(region, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionCoordId");
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

<a name="getCoverageRegionCoords"></a>
# **getCoverageRegionCoords**
> DictAddresses getCoverageRegionCoords(region)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoords(region);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionCoords");
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

<a name="getCoverageRegionCoordsId"></a>
# **getCoverageRegionCoordsId**
> DictAddresses getCoverageRegionCoordsId(region, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionCoordsId(region, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionCoordsId");
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

<a name="getCoverageRegionUriCoord"></a>
# **getCoverageRegionUriCoord**
> DictAddresses getCoverageRegionUriCoord(region, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageRegionUriCoord(region, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionUriCoord");
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

<a name="getCoverageRegionUriCoordId"></a>
# **getCoverageRegionUriCoordId**
> DictAddresses getCoverageRegionUriCoordId(region, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionUriCoordId(region, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionUriCoordId");
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

<a name="getCoverageRegionUriCoords"></a>
# **getCoverageRegionUriCoords**
> DictAddresses getCoverageRegionUriCoords(region, uri)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
try {
    DictAddresses result = apiInstance.getCoverageRegionUriCoords(region, uri);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionUriCoords");
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

<a name="getCoverageRegionUriCoordsId"></a>
# **getCoverageRegionUriCoordsId**
> DictAddresses getCoverageRegionUriCoordsId(region, uri, id)



### Example
```java
// Import classes:
//import com.kisio.navitia.sdk.data.expert.invokers.ApiClient;
//import com.kisio.navitia.sdk.data.expert.invokers.ApiException;
//import com.kisio.navitia.sdk.data.expert.invokers.Configuration;
//import com.kisio.navitia.sdk.data.expert.invokers.auth.*;
//import com.kisio.navitia.sdk.data.expert.apis.CoordsApi;

ApiClient defaultClient = Configuration.getDefaultApiClient();

// Configure HTTP basic authorization: basicAuth
HttpBasicAuth basicAuth = (HttpBasicAuth) defaultClient.getAuthentication("basicAuth");
basicAuth.setUsername("YOUR USERNAME");
basicAuth.setPassword("YOUR PASSWORD");

CoordsApi apiInstance = new CoordsApi();
String region = "region_example"; // String |  The region you want to query
String uri = "uri_example"; // String | First part of the uri
String id = "id_example"; // String | Id of the object you want to query
try {
    DictAddresses result = apiInstance.getCoverageRegionUriCoordsId(region, uri, id);
    System.out.println(result);
} catch (ApiException e) {
    System.err.println("Exception when calling CoordsApi#getCoverageRegionUriCoordsId");
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

