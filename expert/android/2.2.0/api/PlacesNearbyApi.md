---
layout: main
title: PlacesNearbyApi
nav_exclude: true
permalink: /expert/android/api/PlacesNearbyApi
---

# PlacesNearbyApi

---

Method | HTTP request
------------- | -------------
[**getCoordLonLatPlacesNearby**](#getCoordLonLatPlacesNearby) | **GET** /coord/{lon};{lat}/places_nearby
[**getCoordsLonLatPlacesNearby**](#getCoordsLonLatPlacesNearby) | **GET** /coords/{lon};{lat}/places_nearby
[**getCoverageLonLatPlacesNearby**](#getCoverageLonLatPlacesNearby) | **GET** /coverage/{lon};{lat}/places_nearby
[**getCoverageLonLatUriPlacesNearby**](#getCoverageLonLatUriPlacesNearby) | **GET** /coverage/{lon};{lat}/{uri}/places_nearby
[**getCoverageRegionPlacesNearby**](#getCoverageRegionPlacesNearby) | **GET** /coverage/{region}/places_nearby
[**getCoverageRegionUriPlacesNearby**](#getCoverageRegionUriPlacesNearby) | **GET** /coverage/{region}/{uri}/places_nearby

## **getCoordLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoordLonLatPlacesNearbyRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoordsLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoordsLonLatPlacesNearbyRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoverageLonLatPlacesNearbyRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageLonLatUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoverageLonLatUriPlacesNearbyRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageRegionPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoverageRegionPlacesNearbyRequestBuilder()
    .withRegion("region_example")
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageRegionUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**type** | [**List&lt;String&gt;**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Integer**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Integer**| Elements per page [optional] [default to 10] 
**depth** | **Integer**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Integer**| The page number of the ptref result [optional] 
**bssStands** | **Boolean**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**List&lt;String&gt;**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)

### Example
```kotlin
navitiaSdk.placesNearbyApi.newCoverageRegionUriPlacesNearbyRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withType(listOf("[u'stop_area', u'stop_point', u'poi']"))
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

