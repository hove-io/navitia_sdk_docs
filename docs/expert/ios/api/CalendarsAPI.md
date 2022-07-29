# CalendarsAPI

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
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageLonLatCalendars(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageLonLatCalendarsId(
    lat: 3.4, 
    lon: 3.4, 
    id: "id_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageLonLatUriCalendars(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageRegionCalendars(
    region: "region_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCalendarsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageRegionCalendarsId(
    region: "region_example", 
    id: "id_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriCalendars**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of calendars per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**startDate** | **String** | Start date [optional] 
**endDate** | **String** | End date [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)


<h3>Example</h3>
```swift
Expert.shared.calendarsApi.getCoverageRegionUriCalendars(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    startDate: "startDate_example", 
    endDate: "endDate_example", 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

