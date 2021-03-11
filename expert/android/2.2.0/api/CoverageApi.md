---
layout: main
title: CoverageApi
nav_exclude: true
permalink: /expert/android/api/CoverageApi
---

# CoverageApi

---

Method | HTTP request
------------- | -------------
[**getCoverage**](#getCoverage) | **GET** /coverage/
[**getCoverageLonLat**](#getCoverageLonLat) | **GET** /coverage/{lon};{lat}/
[**getCoverageRegion**](#getCoverageRegion) | **GET** /coverage/{region}/

## **getCoverage**

### Parameters

Name | Type | Note
---- | ---- | ----
**disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)

### Example
```kotlin
navitiaSdk.coverageApi.newCoverageRequestBuilder()
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

## **getCoverageLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)

### Example
```kotlin
navitiaSdk.coverageApi.newCoverageLonLatRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
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

## **getCoverageRegion**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**disableGeojson** | **Boolean**| hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages)

### Example
```kotlin
navitiaSdk.coverageApi.newCoverageRegionRequestBuilder()
    .withRegion("region_example")
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

