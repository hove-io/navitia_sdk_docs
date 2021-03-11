---
layout: main
title: CalendarsApi
nav_exclude: true
permalink: /expert/ios/api/CalendarsApi
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
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageLonLatCalendarsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageLonLatCalendarsIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageLonLatUriCalendarsRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageRegionCalendarsRequestBuilder()
    .withRegion("region_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageRegionCalendarsIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**depth** | **Int**| The depth of your object [optional] [default to 1] 
**count** | **Int**| Number of calendars per page [optional] [default to 10] 
**startPage** | **Int**| The current page [optional] 
**startDate** | **String**| Start date [optional] 
**endDate** | **String**| End date [optional] 
**forbiddenId** | [**[String]**](String.md)| DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md)| forbidden uris [optional] 
**distance** | **Int**| Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars)


### Example
```swift
navitiaSDK.calendarsApi.newCoverageRegionUriCalendarsRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withDepth(1)
    .withCount(10)
    .withStartPage(56)
    .withStartDate("startDate_example")
    .withEndDate("endDate_example")
    .withForbiddenId(["forbiddenId_example"])
    .withForbiddenUris(["forbiddenUris_example"])
    .withDistance(200)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

