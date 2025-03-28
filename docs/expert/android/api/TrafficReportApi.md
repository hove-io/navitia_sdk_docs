# TrafficReportApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatTrafficReports**](#getcoveragelonlattrafficreports) | **GET** coverage/{lon};{lat}/traffic_reports
[**getCoverageLonLatUriTrafficReports**](#getcoveragelonlaturitrafficreports) | **GET** coverage/{lon};{lat}/{uri}/traffic_reports
[**getCoverageRegionTrafficReports**](#getcoverageregiontrafficreports) | **GET** coverage/{region}/traffic_reports
[**getCoverageRegionUriTrafficReports**](#getcoverageregionuritrafficreports) | **GET** coverage/{region}/{uri}/traffic_reports

## **getCoverageLonLatTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().trafficReportApi.getCoverageLonLatTrafficReports(
    lon = 0.0,
    lat = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123,
    disableGeojson = true,
    language = "language_example",
    since = LocalDateTime.now(),
    until = LocalDateTime.now()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().trafficReportApi.getCoverageLonLatUriTrafficReports(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123,
    disableGeojson = true,
    language = "language_example",
    since = LocalDateTime.now(),
    until = LocalDateTime.now()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().trafficReportApi.getCoverageRegionTrafficReports(
    region = "region_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123,
    disableGeojson = true,
    language = "language_example",
    since = LocalDateTime.now(),
    until = LocalDateTime.now()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().trafficReportApi.getCoverageRegionUriTrafficReports(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    distance = 123,
    disableGeojson = true,
    language = "language_example",
    since = LocalDateTime.now(),
    until = LocalDateTime.now()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

