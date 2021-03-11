---
layout: main
title: CoordApi
nav_exclude: true
permalink: /expert/android/api/CoordApi
---

# CoordApi

---

Method | HTTP request
------------- | -------------
[**getCoordLonLat**](#getCoordLonLat) | **GET** /coord/{lon};{lat}/
[**getCoordsLonLat**](#getCoordsLonLat) | **GET** /coords/{lon};{lat}/
[**getCoverageRegionCoordLonLatAddresses**](#getCoverageRegionCoordLonLatAddresses) | **GET** /coverage/{region}/coord/{lon};{lat}/addresses
[**getCoverageRegionCoordsLonLatAddresses**](#getCoverageRegionCoordsLonLatAddresses) | **GET** /coverage/{region}/coords/{lon};{lat}/addresses

## **getCoordLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.coordApi.newCoordLonLatRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
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

## **getCoordsLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.coordApi.newCoordsLonLatRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
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

## **getCoverageRegionCoordLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**region** | **String**|  The region you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.coordApi.newCoverageRegionCoordLonLatAddressesRequestBuilder()
    .withLat(BigDecimal())
    .withRegion("region_example")
    .withLon(BigDecimal())
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

## **getCoverageRegionCoordsLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**region** | **String**|  The region you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.coordApi.newCoverageRegionCoordsLonLatAddressesRequestBuilder()
    .withLat(BigDecimal())
    .withRegion("region_example")
    .withLon(BigDecimal())
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

