# VehiclePositionsAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLatVehiclePositions**](#getCoordLonLatVehiclePositions) | **GET** /coord/{lon};{lat}/vehicle_positions
[**getCoordsLonLatVehiclePositions**](#getCoordsLonLatVehiclePositions) | **GET** /coords/{lon};{lat}/vehicle_positions
[**getCoverageLonLatUriVehiclePositions**](#getCoverageLonLatUriVehiclePositions) | **GET** /coverage/{lon};{lat}/{uri}/vehicle_positions
[**getCoverageLonLatVehiclePositions**](#getCoverageLonLatVehiclePositions) | **GET** /coverage/{lon};{lat}/vehicle_positions
[**getCoverageRegionUriVehiclePositions**](#getCoverageRegionUriVehiclePositions) | **GET** /coverage/{region}/{uri}/vehicle_positions
[**getCoverageRegionVehiclePositions**](#getCoverageRegionVehiclePositions) | **GET** /coverage/{region}/vehicle_positions

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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoordLonLatVehiclePositions(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoordsLonLatVehiclePositions(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoverageLonLatUriVehiclePositions(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoverageLonLatVehiclePositions(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoverageRegionUriVehiclePositions(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**VehiclePositions1**](../model/VehiclePositions1.md)


<h3>Example</h3>
```swift
Expert.shared.vehiclePositionsApi.getCoverageRegionVehiclePositions(
    region: "region_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

