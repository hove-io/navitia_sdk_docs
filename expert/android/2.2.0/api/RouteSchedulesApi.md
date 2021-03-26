---
layout: main
title: RouteSchedulesApi
nav_exclude: true
permalink: /expert/android/api/RouteSchedulesApi
---

# RouteSchedulesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatUriRouteSchedules**](#getCoverageLonLatUriRouteSchedules) | **GET** /coverage/{lon};{lat}/{uri}/route_schedules
[**getCoverageRegionUriRouteSchedules**](#getCoverageRegionUriRouteSchedules) | **GET** /coverage/{region}/{uri}/route_schedules
[**getRouteSchedules**](#getRouteSchedules) | **GET** /route_schedules

## **getCoverageLonLatUriRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **DateTime**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **DateTime**| The datetime until which you want the schedules [optional] 
**duration** | **Integer**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Integer**| The depth of your object [optional] [default to 2] 
**count** | **Integer**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Integer**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules)

### Example
```kotlin
navitiaSdk.routeSchedulesApi.newCoverageLonLatUriRouteSchedulesRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withFilter("filter_example")
    .withFromDatetime(DateTime())
    .withUntilDatetime(DateTime())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
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

## **getCoverageRegionUriRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **DateTime**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **DateTime**| The datetime until which you want the schedules [optional] 
**duration** | **Integer**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Integer**| The depth of your object [optional] [default to 2] 
**count** | **Integer**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Integer**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules)

### Example
```kotlin
navitiaSdk.routeSchedulesApi.newCoverageRegionUriRouteSchedulesRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withFilter("filter_example")
    .withFromDatetime(DateTime())
    .withUntilDatetime(DateTime())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
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

## **getRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **DateTime**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **DateTime**| The datetime until which you want the schedules [optional] 
**duration** | **Integer**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Integer**| The depth of your object [optional] [default to 2] 
**count** | **Integer**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Integer**| The current page [optional] 
**maxDateTimes** | **Integer**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Integer**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules)

### Example
```kotlin
navitiaSdk.routeSchedulesApi.newRouteSchedulesRequestBuilder()
    .withFilter("filter_example")
    .withFromDatetime(DateTime())
    .withUntilDatetime(DateTime())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
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

