---
layout: main
title: GeoStatusApi
nav_exclude: true
permalink: /expert/ios/api/GeoStatusApi
---

# GeoStatusApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatGeoStatus**](#getCoverageLonLatGeoStatus) | **GET** /coverage/{lon};{lat}/_geo_status
[**getCoverageRegionGeoStatus**](#getCoverageRegionGeoStatus) | **GET** /coverage/{region}/_geo_status

## **getCoverageLonLatGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1)


### Example
```swift
navitiaSDK.geoStatusApi.newCoverageLonLatGeoStatusRequestBuilder()
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

## **getCoverageRegionGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1)


### Example
```swift
navitiaSDK.geoStatusApi.newCoverageRegionGeoStatusRequestBuilder()
    .withRegion("region_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

