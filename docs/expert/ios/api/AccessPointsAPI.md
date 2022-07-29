# AccessPointsAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLatAccessPoints**](#getCoordLonLatAccessPoints) | **GET** /coord/{lon};{lat}/access_points
[**getCoordsLonLatAccessPoints**](#getCoordsLonLatAccessPoints) | **GET** /coords/{lon};{lat}/access_points
[**getCoverageLonLatAccessPoints**](#getCoverageLonLatAccessPoints) | **GET** /coverage/{lon};{lat}/access_points
[**getCoverageLonLatUriAccessPoints**](#getCoverageLonLatUriAccessPoints) | **GET** /coverage/{lon};{lat}/{uri}/access_points
[**getCoverageRegionAccessPoints**](#getCoverageRegionAccessPoints) | **GET** /coverage/{region}/access_points
[**getCoverageRegionUriAccessPoints**](#getCoverageRegionUriAccessPoints) | **GET** /coverage/{region}/{uri}/access_points

## **getCoordLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoordLonLatAccessPoints(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoordsLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoordsLonLatAccessPoints(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoverageLonLatAccessPoints(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriAccessPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoverageLonLatUriAccessPoints(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoverageRegionAccessPoints(
    region: "region_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**AccessPoints**](../model/AccessPoints.md)


<h3>Example</h3>
```swift
Expert.shared.accessPointsApi.getCoverageRegionUriAccessPoints(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

