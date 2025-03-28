# FreeFloatingsNearbyApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatFreefloatingsNearby**](#getcoordlonlatfreefloatingsnearby) | **GET** coord/{lon};{lat}/freefloatings_nearby
[**getCoordsLonLatFreefloatingsNearby**](#getcoordslonlatfreefloatingsnearby) | **GET** coords/{lon};{lat}/freefloatings_nearby
[**getCoverageLonLatFreefloatingsNearby**](#getcoveragelonlatfreefloatingsnearby) | **GET** coverage/{lon};{lat}/freefloatings_nearby
[**getCoverageLonLatUriFreefloatingsNearby**](#getcoveragelonlaturifreefloatingsnearby) | **GET** coverage/{lon};{lat}/{uri}/freefloatings_nearby
[**getCoverageRegionFreefloatingsNearby**](#getcoverageregionfreefloatingsnearby) | **GET** coverage/{region}/freefloatings_nearby
[**getCoverageRegionUriFreefloatingsNearby**](#getcoverageregionurifreefloatingsnearby) | **GET** coverage/{region}/{uri}/freefloatings_nearby

## **getCoordLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoordLonLatFreefloatingsNearby(
    lon = 0.0,
    lat = 0.0,
    type = listOf(),
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

## **getCoordsLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoordsLonLatFreefloatingsNearby(
    lon = 0.0,
    lat = 0.0,
    type = listOf(),
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

## **getCoverageLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoverageLonLatFreefloatingsNearby(
    lon = 0.0,
    lat = 0.0,
    type = listOf(),
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

## **getCoverageLonLatUriFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoverageLonLatUriFreefloatingsNearby(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    type = listOf(),
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

## **getCoverageRegionFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoverageRegionFreefloatingsNearby(
    region = "region_example",
    type = listOf(),
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

## **getCoverageRegionUriFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**type** | [**List<String>**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().freeFloatingsNearbyApi.getCoverageRegionUriFreefloatingsNearby(
    region = "region_example",
    uri = "uri_example",
    type = listOf(),
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

