---
layout: main
title: LineReportsApi
nav_exclude: true
permalink: /expert/android/api/LineReportsApi
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
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**since** | **DateTime**| use disruptions valid after this date [optional] 
**until** | **DateTime**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)

### Example
```kotlin
navitiaSdk.lineReportsApi.newCoverageLonLatLineReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDisableGeojson(true)
    .withSince(DateTime())
    .withUntil(DateTime())
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

## **getCoverageLonLatUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**since** | **DateTime**| use disruptions valid after this date [optional] 
**until** | **DateTime**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)

### Example
```kotlin
navitiaSdk.lineReportsApi.newCoverageLonLatUriLineReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDisableGeojson(true)
    .withSince(DateTime())
    .withUntil(DateTime())
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

## **getCoverageRegionLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**since** | **DateTime**| use disruptions valid after this date [optional] 
**until** | **DateTime**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)

### Example
```kotlin
navitiaSdk.lineReportsApi.newCoverageRegionLineReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDisableGeojson(true)
    .withSince(DateTime())
    .withUntil(DateTime())
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

## **getCoverageRegionUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**since** | **DateTime**| use disruptions valid after this date [optional] 
**until** | **DateTime**| use disruptions valid before this date [optional] 

### Return
[**LineReports**](../model/LineReports)

### Example
```kotlin
navitiaSdk.lineReportsApi.newCoverageRegionUriLineReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDisableGeojson(true)
    .withSince(DateTime())
    .withUntil(DateTime())
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

