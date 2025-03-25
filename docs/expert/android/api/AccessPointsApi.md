# AccessPointsApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatAccessPoints**](#getcoordlonlataccesspoints) | **GET** coord/{lon};{lat}/access_points
[**getCoordsLonLatAccessPoints**](#getcoordslonlataccesspoints) | **GET** coords/{lon};{lat}/access_points
[**getCoverageLonLatAccessPoints**](#getcoveragelonlataccesspoints) | **GET** coverage/{lon};{lat}/access_points
[**getCoverageLonLatUriAccessPoints**](#getcoveragelonlaturiaccesspoints) | **GET** coverage/{lon};{lat}/{uri}/access_points
[**getCoverageRegionAccessPoints**](#getcoverageregionaccesspoints) | **GET** coverage/{region}/access_points
[**getCoverageRegionUriAccessPoints**](#getcoverageregionuriaccesspoints) | **GET** coverage/{region}/{uri}/access_points

## **getCoordLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoordLonLatAccessPoints(
    lon = 0.0,
    lat = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoordsLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoordsLonLatAccessPoints(
    lon = 0.0,
    lat = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoverageLonLatAccessPoints(
    lon = 0.0,
    lat = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoverageLonLatUriAccessPoints(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoverageRegionAccessPoints(
    region = "region_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().accessPointsApi.getCoverageRegionUriAccessPoints(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

