# CoordAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLat**](#getCoordLonLat) | **GET** /coord/{lon};{lat}/
[**getCoordsLonLat**](#getCoordsLonLat) | **GET** /coords/{lon};{lat}/
[**getCoverageRegionCoordLonLatAddresses**](#getCoverageRegionCoordLonLatAddresses) | **GET** /coverage/{region}/coord/{lon};{lat}/addresses
[**getCoverageRegionCoordsLonLatAddresses**](#getCoverageRegionCoordsLonLatAddresses) | **GET** /coverage/{region}/coords/{lon};{lat}/addresses

## **getCoordLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordApi.getCoordLonLat(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoordsLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordApi.getCoordsLonLat(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoordLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**region** | **String** | The region you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordApi.getCoverageRegionCoordLonLatAddresses(
    lat: 3.4, 
    region: "region_example", 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoordsLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**region** | **String** | The region you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordApi.getCoverageRegionCoordsLonLatAddresses(
    lat: 3.4, 
    region: "region_example", 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

