---
layout: main
title: PtobjectsApi
nav_exclude: true
permalink: /expert/android/api/PtobjectsApi
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
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**type** | [**List&lt;String&gt;**](String.md)| The type of data to search [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Integer**| The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Integer**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects)

### Example
```kotlin
navitiaSdk.ptobjectsApi.newCoverageLonLatPtObjectsRequestBuilder()
    .withQ("q_example")
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withType(listOf("[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"))
    .withCount(10)
    .withAdminUri(listOf("adminUri_example"))
    .withDepth(1)
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .get(object : ApiCallback<T> {
        override fun onSuccess(
            result: T,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Success result
        }

        override fun onFailure(
            e: ApiException?,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Failure result
        }

        override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            // Progress upload
        }

        override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            // Progress download
        }
    })
```

## **getCoverageRegionPtObjects**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**region** | **String**|  The region you want to query 
**type** | [**List&lt;String&gt;**](String.md)| The type of data to search [optional] [default to [u&#39;network&#39;, u&#39;commercial_mode&#39;, u&#39;line&#39;, u&#39;line_group&#39;, u&#39;route&#39;, u&#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Integer**| The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Integer**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects)

### Example
```kotlin
navitiaSdk.ptobjectsApi.newCoverageRegionPtObjectsRequestBuilder()
    .withQ("q_example")
    .withRegion("region_example")
    .withType(listOf("[u'network', u'commercial_mode', u'line', u'line_group', u'route', u'stop_area']"))
    .withCount(10)
    .withAdminUri(listOf("adminUri_example"))
    .withDepth(1)
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .get(object : ApiCallback<T> {
        override fun onSuccess(
            result: T,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Success result
        }

        override fun onFailure(
            e: ApiException?,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Failure result
        }

        override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            // Progress upload
        }

        override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            // Progress download
        }
    })
```

