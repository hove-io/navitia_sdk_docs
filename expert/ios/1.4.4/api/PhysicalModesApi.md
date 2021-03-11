---
layout: main
title: PhysicalModesApi
nav_exclude: true
permalink: /expert/ios/api/PhysicalModesApi
---

# PhysicalModesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPhysicalModes**](#getCoverageLonLatPhysicalModes) | **GET** /coverage/{lon};{lat}/physical_modes
[**getCoverageLonLatPhysicalModesId**](#getCoverageLonLatPhysicalModesId) | **GET** /coverage/{lon};{lat}/physical_modes/{id}
[**getCoverageLonLatUriPhysicalModes**](#getCoverageLonLatUriPhysicalModes) | **GET** /coverage/{lon};{lat}/{uri}/physical_modes
[**getCoverageLonLatUriPhysicalModesId**](#getCoverageLonLatUriPhysicalModesId) | **GET** /coverage/{lon};{lat}/{uri}/physical_modes/{id}
[**getCoverageRegionPhysicalModes**](#getCoverageRegionPhysicalModes) | **GET** /coverage/{region}/physical_modes
[**getCoverageRegionPhysicalModesId**](#getCoverageRegionPhysicalModesId) | **GET** /coverage/{region}/physical_modes/{id}
[**getCoverageRegionUriPhysicalModes**](#getCoverageRegionUriPhysicalModes) | **GET** /coverage/{region}/{uri}/physical_modes
[**getCoverageRegionUriPhysicalModesId**](#getCoverageRegionUriPhysicalModesId) | **GET** /coverage/{region}/{uri}/physical_modes/{id}

## **getCoverageLonLatPhysicalModes**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageLonLatPhysicalModesRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatPhysicalModesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageLonLatPhysicalModesIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriPhysicalModes**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageLonLatUriPhysicalModesRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriPhysicalModesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageLonLatUriPhysicalModesIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionPhysicalModes**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageRegionPhysicalModesRequestBuilder()
    .withRegion("region_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionPhysicalModesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageRegionPhysicalModesIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriPhysicalModes**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**filter** | **String**| The filter parameter [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageRegionUriPhysicalModesRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withFilter("filter_example")
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriPhysicalModesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 
**startPage** | **Int**| The page where you want to start [optional] 
**count** | **Int**| Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**externalCode** | **String**| An external code to query [optional] 
**headsign** | **String**| filter vehicle journeys on headsign [optional] 
**showCodes** | **Bool**| show more identification codes [optional] 
**odtLevel** | **String**| odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String**| Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date**| filters objects not valid before this date [optional] 
**until** | **Date**| filters objects not valid after this date [optional] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md)| If filled, will restrain the search within the given disruption tags [optional] 

### Return
[**PhysicalModes**](../model/PhysicalModes)


### Example
```swift
navitiaSDK.physicalModesApi.newCoverageRegionUriPhysicalModesIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
    .withStartPage(56)
    .withCount(25)
    .withDepth(1)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withExternalCode("externalCode_example")
    .withHeadsign("headsign_example")
    .withShowCodes(true)
    .withOdtLevel("all")
    .withDataFreshness("base_schedule")
    .withDistance(200)
    .withSince(Date())
    .withUntil(Date())
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .withTags(["tags_example"])
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

