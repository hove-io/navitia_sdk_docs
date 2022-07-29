# NextDeparturesAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatDepartures**](#getCoverageLonLatDepartures) | **GET** /coverage/{lon};{lat}/departures
[**getCoverageLonLatUriDepartures**](#getCoverageLonLatUriDepartures) | **GET** /coverage/{lon};{lat}/{uri}/departures
[**getCoverageRegionDepartures**](#getCoverageRegionDepartures) | **GET** /coverage/{region}/departures
[**getCoverageRegionUriDepartures**](#getCoverageRegionUriDepartures) | **GET** /coverage/{region}/{uri}/departures

## **getCoverageLonLatDepartures**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **Date** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**Departures**](../model/Departures.md)


<h3>Example</h3>
```swift
Expert.shared.nextDeparturesApi.getCoverageLonLatDepartures(
    lat: 3.4, 
    lon: 3.4, 
    filter: "filter_example", 
    fromDatetime: Date(), 
    untilDatetime: Date(), 
    duration: 86399, 
    depth: 2, 
    count: 10, 
    startPage: 56, 
    maxDateTimes: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    calendar: "calendar_example", 
    distance: 200, 
    dataFreshness: "dataFreshness_example", 
    itemsPerSchedule: 10000, 
    disableGeojson: true, 
    directionType: "directionType_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriDepartures**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **Date** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**Departures**](../model/Departures.md)


<h3>Example</h3>
```swift
Expert.shared.nextDeparturesApi.getCoverageLonLatUriDepartures(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    filter: "filter_example", 
    fromDatetime: Date(), 
    untilDatetime: Date(), 
    duration: 86399, 
    depth: 2, 
    count: 10, 
    startPage: 56, 
    maxDateTimes: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    calendar: "calendar_example", 
    distance: 200, 
    dataFreshness: "dataFreshness_example", 
    itemsPerSchedule: 10000, 
    disableGeojson: true, 
    directionType: "directionType_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionDepartures**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **Date** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**Departures**](../model/Departures.md)


<h3>Example</h3>
```swift
Expert.shared.nextDeparturesApi.getCoverageRegionDepartures(
    region: "region_example", 
    filter: "filter_example", 
    fromDatetime: Date(), 
    untilDatetime: Date(), 
    duration: 86399, 
    depth: 2, 
    count: 10, 
    startPage: 56, 
    maxDateTimes: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    calendar: "calendar_example", 
    distance: 200, 
    dataFreshness: "dataFreshness_example", 
    itemsPerSchedule: 10000, 
    disableGeojson: true, 
    directionType: "directionType_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriDepartures**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **Date** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **Date** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by &#x60;items_per_schedule&#x60; [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**Departures**](../model/Departures.md)


<h3>Example</h3>
```swift
Expert.shared.nextDeparturesApi.getCoverageRegionUriDepartures(
    region: "region_example", 
    uri: "uri_example", 
    filter: "filter_example", 
    fromDatetime: Date(), 
    untilDatetime: Date(), 
    duration: 86399, 
    depth: 2, 
    count: 10, 
    startPage: 56, 
    maxDateTimes: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    calendar: "calendar_example", 
    distance: 200, 
    dataFreshness: "dataFreshness_example", 
    itemsPerSchedule: 10000, 
    disableGeojson: true, 
    directionType: "directionType_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

