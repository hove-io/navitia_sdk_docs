---
layout: main
title: TrafficReportApi
nav_exclude: true
permalink: /expert/android/api/TrafficReportApi
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
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)

### Example
```kotlin
navitiaSdk.trafficReportApi.newCoverageLonLatTrafficReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
    .withDisableGeojson(true)
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

## **getCoverageLonLatUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)

### Example
```kotlin
navitiaSdk.trafficReportApi.newCoverageLonLatUriTrafficReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
    .withDisableGeojson(true)
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

## **getCoverageRegionTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)

### Example
```kotlin
navitiaSdk.trafficReportApi.newCoverageRegionTrafficReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
    .withDisableGeojson(true)
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

## **getCoverageRegionUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 

### Return
[**TrafficReports**](../model/TrafficReports)

### Example
```kotlin
navitiaSdk.trafficReportApi.newCoverageRegionUriTrafficReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
    .withDisableGeojson(true)
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

