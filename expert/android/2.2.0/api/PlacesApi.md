---
layout: main
title: PlacesApi
nav_exclude: true
permalink: /expert/android/api/PlacesApi
---

# PlacesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlaces**](#getCoverageLonLatPlaces) | **GET** /coverage/{lon};{lat}/places
[**getCoverageRegionPlaces**](#getCoverageRegionPlaces) | **GET** /coverage/{region}/places
[**getPlaces**](#getPlaces) | **GET** /places

## **getCoverageLonLatPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**type** | [**List&lt;String&gt;**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Integer**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Integer**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placesApi.newCoverageLonLatPlacesRequestBuilder()
    .withQ("q_example")
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withType(listOf("[u'stop_area', u'address', u'poi', u'administrative_region']"))
    .withCount(10)
    .withAdminUri(listOf("adminUri_example"))
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
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

## **getCoverageRegionPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**region** | **String**|  The region you want to query 
**type** | [**List&lt;String&gt;**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Integer**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Integer**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placesApi.newCoverageRegionPlacesRequestBuilder()
    .withQ("q_example")
    .withRegion("region_example")
    .withType(listOf("[u'stop_area', u'address', u'poi', u'administrative_region']"))
    .withCount(10)
    .withAdminUri(listOf("adminUri_example"))
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
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

## **getPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**type** | [**List&lt;String&gt;**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Integer**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Integer**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placesApi.newPlacesRequestBuilder()
    .withQ("q_example")
    .withType(listOf("[u'stop_area', u'address', u'poi', u'administrative_region']"))
    .withCount(10)
    .withAdminUri(listOf("adminUri_example"))
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
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

