# PlacesNearbyApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatPlacesNearby**](#getcoordlonlatplacesnearby) | **GET** coord/{lon};{lat}/places_nearby
[**getCoordsLonLatPlacesNearby**](#getcoordslonlatplacesnearby) | **GET** coords/{lon};{lat}/places_nearby
[**getCoverageLonLatPlacesNearby**](#getcoveragelonlatplacesnearby) | **GET** coverage/{lon};{lat}/places_nearby
[**getCoverageLonLatUriPlacesNearby**](#getcoveragelonlaturiplacesnearby) | **GET** coverage/{lon};{lat}/{uri}/places_nearby
[**getCoverageRegionPlacesNearby**](#getcoverageregionplacesnearby) | **GET** coverage/{region}/places_nearby
[**getCoverageRegionUriPlacesNearby**](#getcoverageregionuriplacesnearby) | **GET** coverage/{region}/{uri}/places_nearby

## **getCoordLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoordLonLatPlacesNearby(
    lat = 0.0,
    lon = 0.0,
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoordsLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoordsLonLatPlacesNearby(
    lat = 0.0,
    lon = 0.0,
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoverageLonLatPlacesNearby(
    lat = 0.0,
    lon = 0.0,
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoverageLonLatUriPlacesNearby(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example",
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoverageRegionPlacesNearby(
    region = "region_example",
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**type** | [**List<String>**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placesNearbyApi.getCoverageRegionUriPlacesNearby(
    region = "region_example",
    uri = "uri_example",
    type = listOf(),
    filter = "filter_example",
    distance = 123,
    count = 123,
    depth = 123,
    startPage = 123,
    bssStands = true,
    addPoiInfos = listOf(),
    disableGeojson = true,
    disableDisruption = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

