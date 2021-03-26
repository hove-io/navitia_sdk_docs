---
layout: main
title: CoordsApi
nav_exclude: true
permalink: /expert/ios/api/CoordsApi
---

# CoordsApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCoord**](#getCoverageLonLatCoord) | **GET** /coverage/{lon};{lat}/coord
[**getCoverageLonLatCoordId**](#getCoverageLonLatCoordId) | **GET** /coverage/{lon};{lat}/coord/{id}
[**getCoverageLonLatCoords**](#getCoverageLonLatCoords) | **GET** /coverage/{lon};{lat}/coords
[**getCoverageLonLatCoordsId**](#getCoverageLonLatCoordsId) | **GET** /coverage/{lon};{lat}/coords/{id}
[**getCoverageLonLatUriCoord**](#getCoverageLonLatUriCoord) | **GET** /coverage/{lon};{lat}/{uri}/coord
[**getCoverageLonLatUriCoordId**](#getCoverageLonLatUriCoordId) | **GET** /coverage/{lon};{lat}/{uri}/coord/{id}
[**getCoverageLonLatUriCoords**](#getCoverageLonLatUriCoords) | **GET** /coverage/{lon};{lat}/{uri}/coords
[**getCoverageLonLatUriCoordsId**](#getCoverageLonLatUriCoordsId) | **GET** /coverage/{lon};{lat}/{uri}/coords/{id}
[**getCoverageRegionCoord**](#getCoverageRegionCoord) | **GET** /coverage/{region}/coord
[**getCoverageRegionCoordId**](#getCoverageRegionCoordId) | **GET** /coverage/{region}/coord/{id}
[**getCoverageRegionCoords**](#getCoverageRegionCoords) | **GET** /coverage/{region}/coords
[**getCoverageRegionCoordsId**](#getCoverageRegionCoordsId) | **GET** /coverage/{region}/coords/{id}
[**getCoverageRegionUriCoord**](#getCoverageRegionUriCoord) | **GET** /coverage/{region}/{uri}/coord
[**getCoverageRegionUriCoordId**](#getCoverageRegionUriCoordId) | **GET** /coverage/{region}/{uri}/coord/{id}
[**getCoverageRegionUriCoords**](#getCoverageRegionUriCoords) | **GET** /coverage/{region}/{uri}/coords
[**getCoverageRegionUriCoordsId**](#getCoverageRegionUriCoordsId) | **GET** /coverage/{region}/{uri}/coords/{id}

## **getCoverageLonLatCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatCoordRequestBuilder()
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

## **getCoverageLonLatCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatCoordIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatCoordsRequestBuilder()
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

## **getCoverageLonLatCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatCoordsIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatUriCoordRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatUriCoordIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatUriCoordsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageLonLatUriCoordsIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionCoordRequestBuilder()
    .withRegion("region_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionCoordIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionCoordsRequestBuilder()
    .withRegion("region_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionCoordsIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionUriCoordRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionUriCoordIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionUriCoordsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.coordsApi.newCoverageRegionUriCoordsIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

