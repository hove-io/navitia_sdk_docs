---
layout: main
title: TrafficReportApi
nav_exclude: true
permalink: /expert/ios/api/TrafficReportApi
---

# TrafficReportApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatTrafficReports**](#getCoverageLonLatTrafficReports) | **GET** /coverage/{lon};{lat}/traffic_reports
[**getCoverageLonLatUriTrafficReports**](#getCoverageLonLatUriTrafficReports) | **GET** /coverage/{lon};{lat}/{uri}/traffic_reports
[**getCoverageRegionTrafficReports**](#getCoverageRegionTrafficReports) | **GET** /coverage/{region}/traffic_reports
[**getCoverageRegionUriTrafficReports**](#getCoverageRegionUriTrafficReports) | **GET** /coverage/{region}/{uri}/traffic_reports

## **getCoverageLonLatTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)


### Example
```swift
navitiaSDK.trafficReportApi.newCoverageLonLatTrafficReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)


### Example
```swift
navitiaSDK.trafficReportApi.newCoverageLonLatUriTrafficReportsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)


### Example
```swift
navitiaSDK.trafficReportApi.newCoverageRegionTrafficReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of objects per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)


### Example
```swift
navitiaSDK.trafficReportApi.newCoverageRegionUriTrafficReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .withDisableGeojson(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

