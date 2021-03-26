---
layout: main
title: LineReportsApi
nav_exclude: true
permalink: /expert/ios/api/LineReportsApi
---

# LineReportsApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatLineReports**](#getCoverageLonLatLineReports) | **GET** /coverage/{lon};{lat}/line_reports
[**getCoverageLonLatUriLineReports**](#getCoverageLonLatUriLineReports) | **GET** /coverage/{lon};{lat}/{uri}/line_reports
[**getCoverageRegionLineReports**](#getCoverageRegionLineReports) | **GET** /coverage/{region}/line_reports
[**getCoverageRegionUriLineReports**](#getCoverageRegionUriLineReports) | **GET** /coverage/{region}/{uri}/line_reports

## **getCoverageLonLatLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**since** | **Date**| use disruptions valid after this date [optional] 
**until** | **Date**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)


### Example
```swift
navitiaSDK.lineReportsApi.newCoverageLonLatLineReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .withDisableGeojson(true)
    .withSince(Date())
    .withUntil(Date())
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**since** | **Date**| use disruptions valid after this date [optional] 
**until** | **Date**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)


### Example
```swift
navitiaSDK.lineReportsApi.newCoverageLonLatUriLineReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .withDisableGeojson(true)
    .withSince(Date())
    .withUntil(Date())
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**since** | **Date**| use disruptions valid after this date [optional] 
**until** | **Date**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)


### Example
```swift
navitiaSDK.lineReportsApi.newCoverageRegionLineReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .withDisableGeojson(true)
    .withSince(Date())
    .withUntil(Date())
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 25] 
**startPage** | **Int**| The current page [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**since** | **Date**| use disruptions valid after this date [optional] 
**until** | **Date**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)


### Example
```swift
navitiaSDK.lineReportsApi.newCoverageRegionUriLineReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(["forbiddenUris_example"])
    .withDisableGeojson(true)
    .withSince(Date())
    .withUntil(Date())
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

