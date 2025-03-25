# LineReportsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatLineReports**](#getcoveragelonlatlinereports) | **GET** coverage/{lon};{lat}/line_reports
[**getCoverageLonLatUriLineReports**](#getcoveragelonlaturilinereports) | **GET** coverage/{lon};{lat}/{uri}/line_reports
[**getCoverageRegionLineReports**](#getcoverageregionlinereports) | **GET** coverage/{region}/line_reports
[**getCoverageRegionUriLineReports**](#getcoverageregionurilinereports) | **GET** coverage/{region}/{uri}/line_reports

## **getCoverageLonLatLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 
**filterStatus** | [**List<String>**](String.md) | filter_status uris [optional] [enum: past, active, future] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**LineReports**](../model/LineReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().lineReportsApi.getCoverageLonLatLineReports(
    lon = 0.0,
    lat = 0.0,
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf(),
    disableGeojson = true,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    filterStatus = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 
**filterStatus** | [**List<String>**](String.md) | filter_status uris [optional] [enum: past, active, future] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**LineReports**](../model/LineReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().lineReportsApi.getCoverageLonLatUriLineReports(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf(),
    disableGeojson = true,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    filterStatus = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 
**filterStatus** | [**List<String>**](String.md) | filter_status uris [optional] [enum: past, active, future] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**LineReports**](../model/LineReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().lineReportsApi.getCoverageRegionLineReports(
    region = "region_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf(),
    disableGeojson = true,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    filterStatus = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**since** | **LocalDateTime** | use disruptions valid after this date [optional] 
**until** | **LocalDateTime** | use disruptions valid before this date [optional] 
**filterStatus** | [**List<String>**](String.md) | filter_status uris [optional] [enum: past, active, future] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**LineReports**](../model/LineReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().lineReportsApi.getCoverageRegionUriLineReports(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    startPage = 123,
    forbiddenUris = listOf(),
    disableGeojson = true,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    filterStatus = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

