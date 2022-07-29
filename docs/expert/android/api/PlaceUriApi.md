# PlaceUriApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlacesId**](#getcoveragelonlatplacesid) | **GET** coverage/{lon};{lat}/places/{id}
[**getCoverageRegionPlacesId**](#getcoverageregionplacesid) | **GET** coverage/{region}/places/{id}
[**getPlacesId**](#getplacesid) | **GET** places/{id}

## **getCoverageLonLatPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placeUriApi.getCoverageLonLatPlacesId(
    lat = 0.0,
    lon = 0.0,
    id = "id_example",
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

## **getCoverageRegionPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placeUriApi.getCoverageRegionPlacesId(
    region = "region_example",
    id = "id_example",
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

## **getPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**id** | **String** | Id of the object you want to query 
**bssStands** | **Boolean** | DEPRECATED, Use add_poi_infos[]=bss_stands [optional] 
**addPoiInfos** | [**List<String>**](String.md) | Show more information about the poi if it's available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Boolean** | remove geojson from the response [optional] 
**disableDisruption** | **Boolean** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().placeUriApi.getPlacesId(
    id = "id_example",
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

