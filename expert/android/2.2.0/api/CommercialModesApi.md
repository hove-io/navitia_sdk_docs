---
layout: main
title: CommercialModesApi
nav_exclude: true
permalink: /expert/android/api/CommercialModesApi
---

# CommercialModesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCommercialModes**](#getCoverageLonLatCommercialModes) | **GET** /coverage/{lon};{lat}/commercial_modes
[**getCoverageLonLatCommercialModesId**](#getCoverageLonLatCommercialModesId) | **GET** /coverage/{lon};{lat}/commercial_modes/{id}
[**getCoverageLonLatUriCommercialModes**](#getCoverageLonLatUriCommercialModes) | **GET** /coverage/{lon};{lat}/{uri}/commercial_modes
[**getCoverageLonLatUriCommercialModesId**](#getCoverageLonLatUriCommercialModesId) | **GET** /coverage/{lon};{lat}/{uri}/commercial_modes/{id}
[**getCoverageRegionCommercialModes**](#getCoverageRegionCommercialModes) | **GET** /coverage/{region}/commercial_modes
[**getCoverageRegionCommercialModesId**](#getCoverageRegionCommercialModesId) | **GET** /coverage/{region}/commercial_modes/{id}
[**getCoverageRegionUriCommercialModes**](#getCoverageRegionUriCommercialModes) | **GET** /coverage/{region}/{uri}/commercial_modes
[**getCoverageRegionUriCommercialModesId**](#getCoverageRegionUriCommercialModesId) | **GET** /coverage/{region}/{uri}/commercial_modes/{id}

## **getCoverageLonLatCommercialModes**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageLonLatCommercialModesRequestBuilder()
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

## **getCoverageLonLatCommercialModesId**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageLonLatCommercialModesIdRequestBuilder()
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

## **getCoverageLonLatUriCommercialModes**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageLonLatUriCommercialModesRequestBuilder()
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

## **getCoverageLonLatUriCommercialModesId**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageLonLatUriCommercialModesIdRequestBuilder()
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

## **getCoverageRegionCommercialModes**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageRegionCommercialModesRequestBuilder()
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

## **getCoverageRegionCommercialModesId**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageRegionCommercialModesIdRequestBuilder()
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

## **getCoverageRegionUriCommercialModes**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageRegionUriCommercialModesRequestBuilder()
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

## **getCoverageRegionUriCommercialModesId**

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
[**CommercialModes**](../model/CommercialModes)

### Example
```kotlin
navitiaSdk.commercialModesApi.newCoverageRegionUriCommercialModesIdRequestBuilder()
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

