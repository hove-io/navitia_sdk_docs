---
layout: main
title: CoordApi
nav_exclude: true
permalink: /expert/ios/api/CoordApi
---

# CoordApi

---

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
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordApi.newCoordLonLatRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoordsLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordApi.newCoordsLonLatRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoordLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**region** | **String**|  The region you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordApi.newCoverageRegionCoordLonLatAddressesRequestBuilder()
    .withLat(3.4)
    .withRegion("region_example")
    .withLon(3.4)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoordsLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**region** | **String**|  The region you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordApi.newCoverageRegionCoordsLonLatAddressesRequestBuilder()
    .withLat(3.4)
    .withRegion("region_example")
    .withLon(3.4)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

