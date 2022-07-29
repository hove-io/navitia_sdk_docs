# FreeFloatingsNearbyAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLatFreefloatingsNearby**](#getCoordLonLatFreefloatingsNearby) | **GET** /coord/{lon};{lat}/freefloatings_nearby
[**getCoordsLonLatFreefloatingsNearby**](#getCoordsLonLatFreefloatingsNearby) | **GET** /coords/{lon};{lat}/freefloatings_nearby
[**getCoverageLonLatFreefloatingsNearby**](#getCoverageLonLatFreefloatingsNearby) | **GET** /coverage/{lon};{lat}/freefloatings_nearby
[**getCoverageLonLatUriFreefloatingsNearby**](#getCoverageLonLatUriFreefloatingsNearby) | **GET** /coverage/{lon};{lat}/{uri}/freefloatings_nearby
[**getCoverageRegionFreefloatingsNearby**](#getCoverageRegionFreefloatingsNearby) | **GET** /coverage/{region}/freefloatings_nearby
[**getCoverageRegionUriFreefloatingsNearby**](#getCoverageRegionUriFreefloatingsNearby) | **GET** /coverage/{region}/{uri}/freefloatings_nearby

## **getCoordLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoordLonLatFreefloatingsNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoordsLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoordsLonLatFreefloatingsNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoverageLonLatFreefloatingsNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoverageLonLatUriFreefloatingsNearby(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoverageRegionFreefloatingsNearby(
    region: "region_example", 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriFreefloatingsNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**type** | [**[String]**](String.md) | Type of free-floating objects to return [optional] [enum: BIKE, SCOOTER, MOTORSCOOTER, STATION, CAR, OTHER] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**coord** | **String** | Coordinates longitude;latitude used to search the objects around this coordinate [optional] 
**startPage** | **Int** | The current page [optional] 

### Return
[**FreeFloatings**](../model/FreeFloatings.md)


<h3>Example</h3>
```swift
Expert.shared.freeFloatingsNearbyApi.getCoverageRegionUriFreefloatingsNearby(
    region: "region_example", 
    uri: "uri_example", 
    type: ["type_example"], 
    distance: 500, 
    count: 10, 
    coord: "coord_example", 
    startPage: 56
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

