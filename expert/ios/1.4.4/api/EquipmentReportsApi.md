---
layout: main
title: EquipmentReportsApi
nav_exclude: true
permalink: /expert/ios/api/EquipmentReportsApi
---

# EquipmentReportsApi

---

Method | HTTP request
------------- | -------------
[**getCoordLonLatEquipmentReports**](#getCoordLonLatEquipmentReports) | **GET** /coord/{lon};{lat}/equipment_reports
[**getCoordsLonLatEquipmentReports**](#getCoordsLonLatEquipmentReports) | **GET** /coords/{lon};{lat}/equipment_reports
[**getCoverageLonLatEquipmentReports**](#getCoverageLonLatEquipmentReports) | **GET** /coverage/{lon};{lat}/equipment_reports
[**getCoverageLonLatUriEquipmentReports**](#getCoverageLonLatUriEquipmentReports) | **GET** /coverage/{lon};{lat}/{uri}/equipment_reports
[**getCoverageRegionEquipmentReports**](#getCoverageRegionEquipmentReports) | **GET** /coverage/{region}/equipment_reports
[**getCoverageRegionUriEquipmentReports**](#getCoverageRegionUriEquipmentReports) | **GET** /coverage/{region}/{uri}/equipment_reports

## **getCoordLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoordLonLatEquipmentReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoordsLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoordsLonLatEquipmentReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoverageLonLatEquipmentReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoverageLonLatUriEquipmentReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoverageRegionEquipmentReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)


### Example
```swift
navitiaSDK.equipmentReportsApi.newCoverageRegionUriEquipmentReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

