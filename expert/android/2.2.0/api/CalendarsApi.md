---
layout: main
title: CalendarsApi
nav_exclude: true
permalink: /expert/android/api/CalendarsApi
---

# CalendarsApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCalendars**](#getCoverageLonLatCalendars) | **GET** /coverage/{lon};{lat}/calendars
[**getCoverageLonLatCalendarsId**](#getCoverageLonLatCalendarsId) | **GET** /coverage/{lon};{lat}/calendars/{id}
[**getCoverageLonLatUriCalendars**](#getCoverageLonLatUriCalendars) | **GET** /coverage/{lon};{lat}/{uri}/calendars
[**getCoverageRegionCalendars**](#getCoverageRegionCalendars) | **GET** /coverage/{region}/calendars
[**getCoverageRegionCalendarsId**](#getCoverageRegionCalendarsId) | **GET** /coverage/{region}/calendars/{id}
[**getCoverageRegionUriCalendars**](#getCoverageRegionUriCalendars) | **GET** /coverage/{region}/{uri}/calendars

## **getCoverageLonLatCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageLonLatCalendarsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

## **getCoverageLonLatCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageLonLatCalendarsIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withId("id_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

## **getCoverageLonLatUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageLonLatUriCalendarsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

## **getCoverageRegionCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageRegionCalendarsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

## **getCoverageRegionCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageRegionCalendarsIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

## **getCoverageRegionUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**count** | **Integer**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)

### Example
```kotlin
navitiaSdk.calendarsApi.newCoverageRegionUriCalendarsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withDistance(200)
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

