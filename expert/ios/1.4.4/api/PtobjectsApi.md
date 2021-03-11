---
layout: main
title: PtobjectsApi
nav_exclude: true
permalink: /expert/ios/api/PtobjectsApi
---

# PtobjectsApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPtObjects**](#getCoverageLonLatPtObjects) | **GET** /coverage/{lon};{lat}/pt_objects
[**getCoverageRegionPtObjects**](#getCoverageRegionPtObjects) | **GET** /coverage/{region}/pt_objects

## **getCoverageLonLatPtObjects**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**type** | [**[String]**](String.md)| The type of data to search [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Int**| The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects)


### Example
```swift
navitiaSDK.ptobjectsApi.newCoverageLonLatPtObjectsRequestBuilder()
    .withQ("q_example")
    .withLat(3.4)
    .withLon(3.4)
    .withType(["[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"])
    .withCount(10)
    .withAdminUri(["adminUri_example"])
    .withDepth(1)
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionPtObjects**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**region** | **String**|  The region you want to query 
**type** | [**[String]**](String.md)| The type of data to search [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Int**| The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects)


### Example
```swift
navitiaSDK.ptobjectsApi.newCoverageRegionPtObjectsRequestBuilder()
    .withQ("q_example")
    .withRegion("region_example")
    .withType(["[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"])
    .withCount(10)
    .withAdminUri(["adminUri_example"])
    .withDepth(1)
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

