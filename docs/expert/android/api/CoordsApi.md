# CoordsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCoord**](#getcoveragelonlatcoord) | **GET** coverage/{lon};{lat}/coord
[**getCoverageLonLatCoordId**](#getcoveragelonlatcoordid) | **GET** coverage/{lon};{lat}/coord/{id}
[**getCoverageLonLatCoords**](#getcoveragelonlatcoords) | **GET** coverage/{lon};{lat}/coords
[**getCoverageLonLatCoordsId**](#getcoveragelonlatcoordsid) | **GET** coverage/{lon};{lat}/coords/{id}
[**getCoverageLonLatUriCoord**](#getcoveragelonlaturicoord) | **GET** coverage/{lon};{lat}/{uri}/coord
[**getCoverageLonLatUriCoordId**](#getcoveragelonlaturicoordid) | **GET** coverage/{lon};{lat}/{uri}/coord/{id}
[**getCoverageLonLatUriCoords**](#getcoveragelonlaturicoords) | **GET** coverage/{lon};{lat}/{uri}/coords
[**getCoverageLonLatUriCoordsId**](#getcoveragelonlaturicoordsid) | **GET** coverage/{lon};{lat}/{uri}/coords/{id}
[**getCoverageRegionCoord**](#getcoverageregioncoord) | **GET** coverage/{region}/coord
[**getCoverageRegionCoordId**](#getcoverageregioncoordid) | **GET** coverage/{region}/coord/{id}
[**getCoverageRegionCoords**](#getcoverageregioncoords) | **GET** coverage/{region}/coords
[**getCoverageRegionCoordsId**](#getcoverageregioncoordsid) | **GET** coverage/{region}/coords/{id}
[**getCoverageRegionUriCoord**](#getcoverageregionuricoord) | **GET** coverage/{region}/{uri}/coord
[**getCoverageRegionUriCoordId**](#getcoverageregionuricoordid) | **GET** coverage/{region}/{uri}/coord/{id}
[**getCoverageRegionUriCoords**](#getcoverageregionuricoords) | **GET** coverage/{region}/{uri}/coords
[**getCoverageRegionUriCoordsId**](#getcoverageregionuricoordsid) | **GET** coverage/{region}/{uri}/coords/{id}

## **getCoverageLonLatCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatCoord(
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatCoordId(
    lon = 0.0,
    lat = 0.0,
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatCoords(
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatCoordsId(
    lon = 0.0,
    lat = 0.0,
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatUriCoord(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatUriCoordId(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatUriCoords(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageLonLatUriCoordsId(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionCoord(
    region = "region_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionCoordId(
    region = "region_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionCoords(
    region = "region_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionCoordsId(
    region = "region_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionUriCoord(
    region = "region_example",
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionUriCoordId(
    region = "region_example",
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionUriCoords(
    region = "region_example",
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordsApi.getCoverageRegionUriCoordsId(
    region = "region_example",
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

