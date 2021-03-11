---
layout: main
title: PlaceUriApi
nav_exclude: true
permalink: /expert/android/api/PlaceUriApi
---

# PlaceUriApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlacesId**](#getCoverageLonLatPlacesId) | **GET** /coverage/{lon};{lat}/places/{id}
[**getCoverageRegionPlacesId**](#getCoverageRegionPlacesId) | **GET** /coverage/{region}/places/{id}
[**getPlacesId**](#getPlacesId) | **GET** /places/{id}

## **getCoverageLonLatPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placeUriApi.newCoverageLonLatPlacesIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(listOf("[u'bss_stands', u'car_park']"))
    .withDisableGeojson(true)
    .withDisableDisruption(true)
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

## **getCoverageRegionPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placeUriApi.newCoverageRegionPlacesIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(listOf("[u'bss_stands', u'car_park']"))
    .withDisableGeojson(true)
    .withDisableDisruption(true)
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

## **getPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**id** | **String**| Id of the object you want to query 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)

### Example
```kotlin
navitiaSdk.placeUriApi.newPlacesIdRequestBuilder()
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(listOf("[u'bss_stands', u'car_park']"))
    .withDisableGeojson(true)
    .withDisableDisruption(true)
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

