# PlacesApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlaces**](#getcoveragelonlatplaces) | **GET** coverage/{lon};{lat}/places
[**getCoverageRegionPlaces**](#getcoverageregionplaces) | **GET** coverage/{region}/places
[**getPlaces**](#getplaces) | **GET** places

## **getCoverageLonLatPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | The type of data to search [optional] [default to [&#39;stop_area&#39;, &#39;address&#39;, &#39;poi&#39;, &#39;administrative_region&#39;]] [enum: stop_area, stop_point, address, poi, administrative_region] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List<String>**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**List<String>**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesApi.getCoverageLonLatPlaces(
    q = "q_example",
    lon = 0.0,
    lat = 0.0,
    type = listOf(),
    count = 123,
    adminUri = listOf(),
    depth = 123,
    disableGeojson = true,
    from = "from_example",
    shape = "shape_example",
    shapeScope = listOf(),
    placesProximityRadius = 0f
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**region** | **String** | The region you want to query 
**type** | [**List<String>**](String.md) | The type of data to search [optional] [default to [&#39;stop_area&#39;, &#39;address&#39;, &#39;poi&#39;, &#39;administrative_region&#39;]] [enum: stop_area, stop_point, address, poi, administrative_region] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List<String>**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**List<String>**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesApi.getCoverageRegionPlaces(
    q = "q_example",
    region = "region_example",
    type = listOf(),
    count = 123,
    adminUri = listOf(),
    depth = 123,
    disableGeojson = true,
    from = "from_example",
    shape = "shape_example",
    shapeScope = listOf(),
    placesProximityRadius = 0f
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**type** | [**List<String>**](String.md) | The type of data to search [optional] [default to [&#39;stop_area&#39;, &#39;address&#39;, &#39;poi&#39;, &#39;administrative_region&#39;]] [enum: stop_area, stop_point, address, poi, administrative_region] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**List<String>**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**List<String>**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesApi.getPlaces(
    q = "q_example",
    type = listOf(),
    count = 123,
    adminUri = listOf(),
    depth = 123,
    disableGeojson = true,
    from = "from_example",
    shape = "shape_example",
    shapeScope = listOf(),
    placesProximityRadius = 0f
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

