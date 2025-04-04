# RouteSchedulesApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatUriRouteSchedules**](#getcoveragelonlaturirouteschedules) | **GET** coverage/{lon};{lat}/{uri}/route_schedules
[**getCoverageRegionUriRouteSchedules**](#getcoverageregionurirouteschedules) | **GET** coverage/{region}/{uri}/route_schedules
[**getRouteSchedules**](#getrouteschedules) | **GET** route_schedules

## **getCoverageLonLatUriRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **LocalDateTime** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **LocalDateTime** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by `items_per_schedule` [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().routeSchedulesApi.getCoverageLonLatUriRouteSchedules(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    filter = "filter_example",
    fromDatetime = LocalDateTime.now(),
    untilDatetime = LocalDateTime.now(),
    duration = 123,
    depth = 123,
    count = 123,
    startPage = 123,
    maxDateTimes = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    calendar = "calendar_example",
    distance = 123,
    dataFreshness = "dataFreshness_example",
    itemsPerSchedule = 123,
    disableGeojson = true,
    directionType = "directionType_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **LocalDateTime** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **LocalDateTime** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by `items_per_schedule` [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().routeSchedulesApi.getCoverageRegionUriRouteSchedules(
    region = "region_example",
    uri = "uri_example",
    filter = "filter_example",
    fromDatetime = LocalDateTime.now(),
    untilDatetime = LocalDateTime.now(),
    duration = 123,
    depth = 123,
    count = 123,
    startPage = 123,
    maxDateTimes = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    calendar = "calendar_example",
    distance = 123,
    dataFreshness = "dataFreshness_example",
    itemsPerSchedule = 123,
    disableGeojson = true,
    directionType = "directionType_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getRouteSchedules**

### Parameters

Name | Type | Note
---- | ---- | ----
**filter** | **String** | use to filter PT objects [optional] 
**fromDatetime** | **LocalDateTime** | The datetime from which you want the schedules [optional] 
**untilDatetime** | **LocalDateTime** | The datetime until which you want the schedules [optional] 
**duration** | **Int** | Maximum duration between datetime and the retrieved stop time [optional] [default to 86399] 
**depth** | **Int** | The depth of your object [optional] [default to 2] 
**count** | **Int** | Number of schedules per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**maxDateTimes** | **Int** | DEPRECATED, replaced by `items_per_schedule` [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**calendar** | **String** | Id of the calendar [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**dataFreshness** | **String** | freshness of the data. base_schedule is the long term planned schedule. adapted_schedule is for planned ahead disruptions (strikes, maintenances, ...). realtime is to have the freshest possible data [optional] [enum: base_schedule, adapted_schedule, realtime] 
**itemsPerSchedule** | **Int** | maximum number of date_times per schedule [optional] [default to 10000] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**directionType** | **String** | Provide a route direction type to filter results. Note: forward is equivalent to clockwise and inbound. When you select forward, you filter with: [forward, clockwise, inbound]. On the other hand, backward is equivalent to anticlockwise and outbound. When you select backward, you filter with: [backward, anticlockwise, outbound]. [optional] [enum: all, forward, backward] 

### Return
[**RouteSchedules**](../model/RouteSchedules.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().routeSchedulesApi.getRouteSchedules(
    filter = "filter_example",
    fromDatetime = LocalDateTime.now(),
    untilDatetime = LocalDateTime.now(),
    duration = 123,
    depth = 123,
    count = 123,
    startPage = 123,
    maxDateTimes = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    calendar = "calendar_example",
    distance = 123,
    dataFreshness = "dataFreshness_example",
    itemsPerSchedule = 123,
    disableGeojson = true,
    directionType = "directionType_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

