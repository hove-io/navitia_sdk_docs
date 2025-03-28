# CoordApi

Method | HTTP request
------------- | -------------
[**getCoordLonLat**](#getcoordlonlat) | **GET** coord/{lon};{lat}/
[**getCoordsLonLat**](#getcoordslonlat) | **GET** coords/{lon};{lat}/
[**getCoverageRegionCoordLonLatAddresses**](#getcoverageregioncoordlonlataddresses) | **GET** coverage/{region}/coord/{lon};{lat}/addresses
[**getCoverageRegionCoordsLonLatAddresses**](#getcoverageregioncoordslonlataddresses) | **GET** coverage/{region}/coords/{lon};{lat}/addresses

## **getCoordLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordApi.getCoordLonLat(
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoordsLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordApi.getCoordsLonLat(
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoordLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordApi.getCoverageRegionCoordLonLatAddresses(
    region = "region_example",
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionCoordsLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**lat** | **Double** | The latitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coordApi.getCoverageRegionCoordsLonLatAddresses(
    region = "region_example",
    lon = 0.0,
    lat = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

