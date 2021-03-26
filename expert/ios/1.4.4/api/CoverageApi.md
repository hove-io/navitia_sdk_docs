---
layout: main
title: CoverageApi
nav_exclude: true
permalink: /expert/ios/api/CoverageApi
---

# CoverageApi

---

Method | HTTP request
------------- | -------------
[**getCoverage**](#getCoverage) | **GET** /coverage/
[**getCoverageLonLat**](#getCoverageLonLat) | **GET** /coverage/{lon};{lat}/
[**getCoverageRegion**](#getCoverageRegion) | **GET** /coverage/{region}/

## **getCoverage**

### Parameters

Name | Type | Note
---- | ---- | ----
**disableGeojson** | **Bool**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)


### Example
```swift
navitiaSDK.coverageApi.newCoverageRequestBuilder()
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**disableGeojson** | **Bool**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)


### Example
```swift
navitiaSDK.coverageApi.newCoverageLonLatRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegion**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**disableGeojson** | **Bool**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)


### Example
```swift
navitiaSDK.coverageApi.newCoverageRegionRequestBuilder()
    .withRegion("region_example")
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

