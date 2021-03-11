---
layout: main
title: JourneyPatternPointsApi
nav_exclude: true
permalink: /expert/android/api/JourneyPatternPointsApi
---

# JourneyPatternPointsApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatJourneyPatternPoints**](#getCoverageLonLatJourneyPatternPoints) | **GET** /coverage/{lon};{lat}/journey_pattern_points
[**getCoverageLonLatJourneyPatternPointsId**](#getCoverageLonLatJourneyPatternPointsId) | **GET** /coverage/{lon};{lat}/journey_pattern_points/{id}
[**getCoverageLonLatUriJourneyPatternPoints**](#getCoverageLonLatUriJourneyPatternPoints) | **GET** /coverage/{lon};{lat}/{uri}/journey_pattern_points
[**getCoverageLonLatUriJourneyPatternPointsId**](#getCoverageLonLatUriJourneyPatternPointsId) | **GET** /coverage/{lon};{lat}/{uri}/journey_pattern_points/{id}
[**getCoverageRegionJourneyPatternPoints**](#getCoverageRegionJourneyPatternPoints) | **GET** /coverage/{region}/journey_pattern_points
[**getCoverageRegionJourneyPatternPointsId**](#getCoverageRegionJourneyPatternPointsId) | **GET** /coverage/{region}/journey_pattern_points/{id}
[**getCoverageRegionUriJourneyPatternPoints**](#getCoverageRegionUriJourneyPatternPoints) | **GET** /coverage/{region}/{uri}/journey_pattern_points
[**getCoverageRegionUriJourneyPatternPointsId**](#getCoverageRegionUriJourneyPatternPointsId) | **GET** /coverage/{region}/{uri}/journey_pattern_points/{id}

## **getCoverageLonLatJourneyPatternPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageLonLatJourneyPatternPointsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(listOf("tags_example"))
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

## **getCoverageLonLatJourneyPatternPointsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageLonLatJourneyPatternPointsIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(listOf("tags_example"))
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

## **getCoverageLonLatUriJourneyPatternPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageLonLatUriJourneyPatternPointsRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(listOf("tags_example"))
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

## **getCoverageLonLatUriJourneyPatternPointsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **BigDecimal**|  The latitude of where the coord you want to query 
**lon** | **BigDecimal**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageLonLatUriJourneyPatternPointsIdRequestBuilder()
    .withLat(BigDecimal())
    .withLon(BigDecimal())
    .withUri("uri_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(listOf("tags_example"))
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

## **getCoverageRegionJourneyPatternPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageRegionJourneyPatternPointsRequestBuilder()
    .withRegion("region_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(listOf("tags_example"))
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

## **getCoverageRegionJourneyPatternPointsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageRegionJourneyPatternPointsIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(listOf("tags_example"))
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

## **getCoverageRegionUriJourneyPatternPoints**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageRegionUriJourneyPatternPointsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(listOf("tags_example"))
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

## **getCoverageRegionUriJourneyPatternPointsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 
**startPage** | **Integer**| The page where you want to start [optional] 
**count** | **Integer**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Integer**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List&lt;String&gt;**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**List&lt;String&gt;**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Boolean**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Integer**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime**| filters objects not valid before this date [optional] 
**until** | **DateTime**| filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean**| remove geojson from the response [optional] 
**disableDisruption** | **Boolean**| remove disruptions from the response [optional] 
**tags** | [**List&lt;String&gt;**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**JourneyPatternPoints**](../model/JourneyPatternPoints)

### Example
```kotlin
navitiaSdk.journeyPatternPointsApi.newCoverageRegionUriJourneyPatternPointsIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(listOf("forbiddenId_example"))
    .withForbiddenUris(listOf("forbiddenUris_example"))
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(DateTime())
    .withUntil(DateTime())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(listOf("tags_example"))
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

