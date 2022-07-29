# GeoStatusApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatGeoStatus**](#getcoveragelonlatgeostatus) | **GET** coverage/{lon};{lat}/_geo_status
[**getCoverageRegionGeoStatus**](#getcoverageregiongeostatus) | **GET** coverage/{region}/_geo_status

## **getCoverageLonLatGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().geoStatusApi.getCoverageLonLatGeoStatus(
    lat = 0.0,
    lon = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().geoStatusApi.getCoverageRegionGeoStatus(
    region = "region_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

