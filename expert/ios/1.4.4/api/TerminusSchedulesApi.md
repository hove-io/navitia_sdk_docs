---
layout: main
title: TerminusSchedulesApi
nav_exclude: true
permalink: /expert/ios/api/TerminusSchedulesApi
---

# TerminusSchedulesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatUriTerminusSchedules**](#getCoverageLonLatUriTerminusSchedules) | **GET** /coverage/{lon};{lat}/{uri}/terminus_schedules
[**getCoverageRegionUriTerminusSchedules**](#getCoverageRegionUriTerminusSchedules) | **GET** /coverage/{region}/{uri}/terminus_schedules
[**getTerminusSchedules**](#getTerminusSchedules) | **GET** /terminus_schedules

## **getCoverageLonLatUriTerminusSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **Date**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date**| The datetime until which you want the schedules [optional] 
**duration** | **Int**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Int**| The depth of your object [optional] [default to 2] 
**count** | **Int**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**maxDateTimes** | **Int**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Bool**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**TerminusSchedules**](../model/TerminusSchedules)


### Example
```swift
navitiaSDK.terminusSchedulesApi.newCoverageLonLatUriTerminusSchedulesRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withFilter("filter_example")
    .withFromDatetime(Date())
    .withUntilDatetime(Date())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriTerminusSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **Date**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date**| The datetime until which you want the schedules [optional] 
**duration** | **Int**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Int**| The depth of your object [optional] [default to 2] 
**count** | **Int**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**maxDateTimes** | **Int**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Bool**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**TerminusSchedules**](../model/TerminusSchedules)


### Example
```swift
navitiaSDK.terminusSchedulesApi.newCoverageRegionUriTerminusSchedulesRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withFilter("filter_example")
    .withFromDatetime(Date())
    .withUntilDatetime(Date())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getTerminusSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**filter** | **String**| use to filter PT objects [optional] 
**fromDatetime** | **Date**| The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date**| The datetime until which you want the schedules [optional] 
**duration** | **Int**| Maximum duration between datetime and the retrieved stop time [optional] [default to 86400] 
**depth** | **Int**| The depth of your object [optional] [default to 2] 
**count** | **Int**| Number of schedules per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**maxDateTimes** | **Int**| DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**calendar** | **String**| Id of the calendar [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**showCodes** | **Bool**| show more identification codes [optional] 
**dataFreshness** | **String**| freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int**| maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**directionType** | **String**| Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**TerminusSchedules**](../model/TerminusSchedules)


### Example
```swift
navitiaSDK.terminusSchedulesApi.newTerminusSchedulesRequestBuilder()
    .withFilter("filter_example")
    .withFromDatetime(Date())
    .withUntilDatetime(Date())
    .withDuration(86400)
    .withDepth(2)
    .withCount(10)
    .withStartPage(56)
    .withMaxDateTimes(56)
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withCalendar("calendar_example")
    .withDistance(200)
    .withShowCodes(true)
    .withDataFreshness("dataFreshness_example")
    .withItemsPerSchedule(10000)
    .withDisableGeojson(true)
    .withDirectionType("directionType_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

