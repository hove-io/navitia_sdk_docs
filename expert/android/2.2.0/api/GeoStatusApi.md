---
layout: main
title: GeoStatusApi
nav_exclude: true
permalink: /expert/android/api/GeoStatusApi
---

# GeoStatusApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatGeoStatus**](#getCoverageLonLatGeoStatus) | **GET** /coverage/{lon};{lat}/_geo_status
[**getCoverageRegionGeoStatus**](#getCoverageRegionGeoStatus) | **GET** /coverage/{region}/_geo_status

## **getCoverageLonLatGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1)

### Example
```kotlin
navitiaSdk.geoStatusApi.newCoverageLonLatGeoStatusRequestBuilder()
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

## **getCoverageRegionGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1)

### Example
```kotlin
navitiaSdk.geoStatusApi.newCoverageRegionGeoStatusRequestBuilder()
    .withRegion("region_example")
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

