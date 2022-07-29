# CalendarsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCalendars**](#getcoveragelonlatcalendars) | **GET** coverage/{lon};{lat}/calendars
[**getCoverageLonLatCalendarsId**](#getcoveragelonlatcalendarsid) | **GET** coverage/{lon};{lat}/calendars/{id}
[**getCoverageLonLatUriCalendars**](#getcoveragelonlaturicalendars) | **GET** coverage/{lon};{lat}/{uri}/calendars
[**getCoverageRegionCalendars**](#getcoverageregioncalendars) | **GET** coverage/{region}/calendars
[**getCoverageRegionCalendarsId**](#getcoverageregioncalendarsid) | **GET** coverage/{region}/calendars/{id}
[**getCoverageRegionUriCalendars**](#getcoverageregionuricalendars) | **GET** coverage/{region}/{uri}/calendars

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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageLonLatCalendars(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageLonLatCalendarsId(
    lat = 0.0,
    lon = 0.0,
    id = "id_example",
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageLonLatUriCalendars(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageRegionCalendars(
    region = "region_example",
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageRegionCalendarsId(
    region = "region_example",
    id = "id_example",
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 

### Return
[**Calendars**](../model/Calendars.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().calendarsApi.getCoverageRegionUriCalendars(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    startDate = "startDate_example",
    endDate = "endDate_example",
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

