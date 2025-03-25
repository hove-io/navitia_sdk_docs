# ObstaclesNearbyApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatObstaclesNearby**](#getcoordlonlatobstaclesnearby) | **GET** coord/{lon};{lat}/obstacles_nearby
[**getCoordsLonLatObstaclesNearby**](#getcoordslonlatobstaclesnearby) | **GET** coords/{lon};{lat}/obstacles_nearby
[**getCoverageLonLatObstaclesNearby**](#getcoveragelonlatobstaclesnearby) | **GET** coverage/{lon};{lat}/obstacles_nearby
[**getCoverageLonLatUriObstaclesNearby**](#getcoveragelonlaturiobstaclesnearby) | **GET** coverage/{lon};{lat}/{uri}/obstacles_nearby
[**getCoverageRegionObstaclesNearby**](#getcoverageregionobstaclesnearby) | **GET** coverage/{region}/obstacles_nearby
[**getCoverageRegionUriObstaclesNearby**](#getcoverageregionuriobstaclesnearby) | **GET** coverage/{region}/{uri}/obstacles_nearby

## **getCoordLonLatObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoordLonLatObstaclesNearby(
    lon = 0.0,
    lat = 0.0,
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoordsLonLatObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoordsLonLatObstaclesNearby(
    lon = 0.0,
    lat = 0.0,
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoverageLonLatObstaclesNearby(
    lon = 0.0,
    lat = 0.0,
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoverageLonLatUriObstaclesNearby(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoverageRegionObstaclesNearby(
    region = "region_example",
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriObstaclesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**path** | **String** | A geojson in polyline path as base64 [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**Obstacles**](../model/Obstacles.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().obstaclesNearbyApi.getCoverageRegionUriObstaclesNearby(
    region = "region_example",
    uri = "uri_example",
    path = "path_example",
    distance = 123,
    count = 123,
    coord = "coord_example",
    startPage = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

