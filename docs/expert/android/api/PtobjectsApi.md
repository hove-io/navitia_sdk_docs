# PtobjectsApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPtObjects**](#getcoveragelonlatptobjects) | **GET** coverage/{lon};{lat}/pt_objects
[**getCoverageRegionPtObjects**](#getcoverageregionptobjects) | **GET** coverage/{region}/pt_objects

## **getCoverageLonLatPtObjects**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | The type of data to search [optional] [default to [&#39;network&#39;, &#39;commercial_mode&#39;, &#39;line&#39;, &#39;line_group&#39;, &#39;route&#39;, &#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Int** | The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**List<String>**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().ptobjectsApi.getCoverageLonLatPtObjects(
    q = "q_example",
    lon = 0.0,
    lat = 0.0,
    type = listOf(),
    count = 123,
    adminUri = listOf(),
    depth = 123,
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionPtObjects**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**region** | **String** | The region you want to query 
**type** | [**List<String>**](String.md) | The type of data to search [optional] [default to [&#39;network&#39;, &#39;commercial_mode&#39;, &#39;line&#39;, &#39;line_group&#39;, &#39;route&#39;, &#39;stop_area&#39;]] [enum: network, commercial_mode, line, line_group, route, stop_area, stop_point] 
**count** | **Int** | The maximum number of ptobjects returned [optional] [default to 10] 
**adminUri** | [**List<String>**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 
**filter** | **String** | Filter your objects [optional] 

### Return
[**PtObjects**](../model/PtObjects.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().ptobjectsApi.getCoverageRegionPtObjects(
    q = "q_example",
    region = "region_example",
    type = listOf(),
    count = 123,
    adminUri = listOf(),
    depth = 123,
    disableGeojson = true,
    disableDisruption = true,
    filter = "filter_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

