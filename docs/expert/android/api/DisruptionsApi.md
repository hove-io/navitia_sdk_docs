# DisruptionsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatDisruptions**](#getcoveragelonlatdisruptions) | **GET** coverage/{lon};{lat}/disruptions
[**getCoverageLonLatDisruptionsId**](#getcoveragelonlatdisruptionsid) | **GET** coverage/{lon};{lat}/disruptions/{id}
[**getCoverageLonLatUriDisruptions**](#getcoveragelonlaturidisruptions) | **GET** coverage/{lon};{lat}/{uri}/disruptions
[**getCoverageLonLatUriDisruptionsId**](#getcoveragelonlaturidisruptionsid) | **GET** coverage/{lon};{lat}/{uri}/disruptions/{id}
[**getCoverageRegionDisruptions**](#getcoverageregiondisruptions) | **GET** coverage/{region}/disruptions
[**getCoverageRegionDisruptionsId**](#getcoverageregiondisruptionsid) | **GET** coverage/{region}/disruptions/{id}
[**getCoverageRegionUriDisruptions**](#getcoverageregionuridisruptions) | **GET** coverage/{region}/{uri}/disruptions
[**getCoverageRegionUriDisruptionsId**](#getcoverageregionuridisruptionsid) | **GET** coverage/{region}/{uri}/disruptions/{id}

## **getCoverageLonLatDisruptions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageLonLatDisruptions(
    lat = 0.0,
    lon = 0.0,
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatDisruptionsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageLonLatDisruptionsId(
    lat = 0.0,
    lon = 0.0,
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriDisruptions**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageLonLatUriDisruptions(
    lat = 0.0,
    lon = 0.0,
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriDisruptionsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**List<String>**](String.md) | DEPRECATED, replaced by `forbidden_uris[]` [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageLonLatUriDisruptionsId(
    lat = 0.0,
    lon = 0.0,
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionDisruptions**

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
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageRegionDisruptions(
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionDisruptionsId**

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
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageRegionDisruptionsId(
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriDisruptions**

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
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageRegionUriDisruptions(
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example",
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriDisruptionsId**

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
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &since and/or &until . Provides only the vehicle_journeys valid for the data freshness level requested. Using `&data_freshness=base_schedule` will return all original vehicle_journeys onlywhereas using `&data_freshness=realtime` will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **DateTime** | filters objects not valid before this date [optional] 
**until** | **DateTime** | filters objects not valid after this date [optional] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**tags** | [**List<String>**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Disruptions**](../model/Disruptions.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().disruptionsApi.getCoverageRegionUriDisruptionsId(
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
    since = DateTime.now(),
    until = DateTime.now(),
    disableGeojson = true,
    disableDisruption = true,
    tags = listOf(),
    originalId = "originalId_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

