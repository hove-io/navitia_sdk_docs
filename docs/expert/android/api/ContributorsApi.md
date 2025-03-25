# ContributorsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatContributors**](#getcoveragelonlatcontributors) | **GET** coverage/{lon};{lat}/contributors
[**getCoverageLonLatContributorsId**](#getcoveragelonlatcontributorsid) | **GET** coverage/{lon};{lat}/contributors/{id}
[**getCoverageLonLatUriContributors**](#getcoveragelonlaturicontributors) | **GET** coverage/{lon};{lat}/{uri}/contributors
[**getCoverageLonLatUriContributorsId**](#getcoveragelonlaturicontributorsid) | **GET** coverage/{lon};{lat}/{uri}/contributors/{id}
[**getCoverageRegionContributors**](#getcoverageregioncontributors) | **GET** coverage/{region}/contributors
[**getCoverageRegionContributorsId**](#getcoverageregioncontributorsid) | **GET** coverage/{region}/contributors/{id}
[**getCoverageRegionUriContributors**](#getcoverageregionuricontributors) | **GET** coverage/{region}/{uri}/contributors
[**getCoverageRegionUriContributorsId**](#getcoverageregionuricontributorsid) | **GET** coverage/{region}/{uri}/contributors/{id}

## **getCoverageLonLatContributors**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageLonLatContributors(
    lon = 0.0,
    lat = 0.0,
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatContributorsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageLonLatContributorsId(
    lon = 0.0,
    lat = 0.0,
    id = "id_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriContributors**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageLonLatUriContributors(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriContributorsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageLonLatUriContributorsId(
    lon = 0.0,
    lat = 0.0,
    uri = "uri_example",
    id = "id_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionContributors**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageRegionContributors(
    region = "region_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionContributorsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageRegionContributorsId(
    region = "region_example",
    id = "id_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriContributors**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageRegionUriContributors(
    region = "region_example",
    uri = "uri_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriContributorsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: all, with_stops, zonal, scheduled] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **LocalDateTime** | filters objects not valid before this date [optional] 
**until** | **LocalDateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**language** | **String** | Here, select a specific language for disruption message [optional] [enum: nl-NL, en-US, en-GB, fr-FR, de-DE, hi-IN, it-IT, ja-JP, pt-PT, ru-RU, es-ES] 

### Return
[**Contributors**](../model/Contributors.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().contributorsApi.getCoverageRegionUriContributorsId(
    region = "region_example",
    uri = "uri_example",
    id = "id_example",
    startPage = 123,
    count = 123,
    depth = 123,
    forbiddenId = listOf(),
    forbiddenUris = listOf(),
    externalCode = "externalCode_example",
    headsign = "headsign_example",
    odtLevel = "odtLevel_example",
    dataFreshness = "dataFreshness_example",
    distance = 123,
    since = LocalDateTime.now(),
    until = LocalDateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    language = "language_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

