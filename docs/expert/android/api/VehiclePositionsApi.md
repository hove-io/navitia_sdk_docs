# VehiclePositionsApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatVehiclePositions**](#getcoordlonlatvehiclepositions) | **GET** coord/{lon};{lat}/vehicle_positions
[**getCoordsLonLatVehiclePositions**](#getcoordslonlatvehiclepositions) | **GET** coords/{lon};{lat}/vehicle_positions
[**getCoverageLonLatUriVehiclePositions**](#getcoveragelonlaturivehiclepositions) | **GET** coverage/{lon};{lat}/{uri}/vehicle_positions
[**getCoverageLonLatVehiclePositions**](#getcoveragelonlatvehiclepositions) | **GET** coverage/{lon};{lat}/vehicle_positions
[**getCoverageRegionUriVehiclePositions**](#getcoverageregionurivehiclepositions) | **GET** coverage/{region}/{uri}/vehicle_positions
[**getCoverageRegionVehiclePositions**](#getcoverageregionvehiclepositions) | **GET** coverage/{region}/vehicle_positions

## **getCoordLonLatVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoordLonLatVehiclePositions(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
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

## **getCoordsLonLatVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoordsLonLatVehiclePositions(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
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

## **getCoverageLonLatUriVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoverageLonLatUriVehiclePositions(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
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

## **getCoverageLonLatVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoverageLonLatVehiclePositions(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
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

## **getCoverageRegionUriVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoverageRegionUriVehiclePositions(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
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

## **getCoverageRegionVehiclePositions**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().vehiclePositionsApi.getCoverageRegionVehiclePositions(
    region = "region_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
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

