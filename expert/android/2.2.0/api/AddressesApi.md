---
layout: main
title: AddressesApi
nav_exclude: true
permalink: /expert/android/api/AddressesApi
---

# AddressesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatAddresses**](#getCoverageLonLatAddresses) | **GET** /coverage/{lon};{lat}/addresses
[**getCoverageLonLatAddressesId**](#getCoverageLonLatAddressesId) | **GET** /coverage/{lon};{lat}/addresses/{id}
[**getCoverageLonLatUriAddresses**](#getCoverageLonLatUriAddresses) | **GET** /coverage/{lon};{lat}/{uri}/addresses
[**getCoverageLonLatUriAddressesId**](#getCoverageLonLatUriAddressesId) | **GET** /coverage/{lon};{lat}/{uri}/addresses/{id}
[**getCoverageRegionAddresses**](#getCoverageRegionAddresses) | **GET** /coverage/{region}/addresses
[**getCoverageRegionAddressesId**](#getCoverageRegionAddressesId) | **GET** /coverage/{region}/addresses/{id}
[**getCoverageRegionUriAddresses**](#getCoverageRegionUriAddresses) | **GET** /coverage/{region}/{uri}/addresses
[**getCoverageRegionUriAddressesId**](#getCoverageRegionUriAddressesId) | **GET** /coverage/{region}/{uri}/addresses/{id}

## **getCoverageLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageLonLatAddressesRequestBuilder()
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

## **getCoverageLonLatAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageLonLatAddressesIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withId("id_example")
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

## **getCoverageLonLatUriAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageLonLatUriAddressesRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
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

## **getCoverageLonLatUriAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageLonLatUriAddressesIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withId("id_example")
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

## **getCoverageRegionAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageRegionAddressesRequestBuilder()
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

## **getCoverageRegionAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageRegionAddressesIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
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

## **getCoverageRegionUriAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageRegionUriAddressesRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
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

## **getCoverageRegionUriAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)

### Example
```kotlin
navitiaSdk.addressesApi.newCoverageRegionUriAddressesIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
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

