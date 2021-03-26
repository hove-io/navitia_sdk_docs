---
layout: main
title: EquipmentReportsApi
nav_exclude: true
permalink: /expert/android/api/EquipmentReportsApi
---

# EquipmentReportsApi

---

Method | HTTP request
------------- | -------------
[**getCoordLonLatEquipmentReports**](#getCoordLonLatEquipmentReports) | **GET** /coord/{lon};{lat}/equipment_reports
[**getCoordsLonLatEquipmentReports**](#getCoordsLonLatEquipmentReports) | **GET** /coords/{lon};{lat}/equipment_reports
[**getCoverageLonLatEquipmentReports**](#getCoverageLonLatEquipmentReports) | **GET** /coverage/{lon};{lat}/equipment_reports
[**getCoverageLonLatUriEquipmentReports**](#getCoverageLonLatUriEquipmentReports) | **GET** /coverage/{lon};{lat}/{uri}/equipment_reports
[**getCoverageRegionEquipmentReports**](#getCoverageRegionEquipmentReports) | **GET** /coverage/{region}/equipment_reports
[**getCoverageRegionUriEquipmentReports**](#getCoverageRegionUriEquipmentReports) | **GET** /coverage/{region}/{uri}/equipment_reports

## **getCoordLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoordLonLatEquipmentReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

## **getCoordsLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoordsLonLatEquipmentReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

## **getCoverageLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoverageLonLatEquipmentReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

## **getCoverageLonLatUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoverageLonLatUriEquipmentReportsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

## **getCoverageRegionEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoverageRegionEquipmentReportsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

## **getCoverageRegionUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of objects per page [optional] [default to 25] 
**filter** | **String**| Filter your objects [optional] 
**startPage** | **Integer**| The current page [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports)

### Example
```kotlin
navitiaSdk.equipmentReportsApi.newCoverageRegionUriEquipmentReportsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(25)
    .withFilter("filter_example")
    .withStartPage(56)
    .withForbiddenUris(listOf("forbiddenUris_example"))
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

