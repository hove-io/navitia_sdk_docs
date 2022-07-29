# CoverageApi

Method | HTTP request
------------- | -------------
[**getCoverage**](#getcoverage) | **GET** coverage/
[**getCoverageLonLat**](#getcoveragelonlat) | **GET** coverage/{lon};{lat}/
[**getCoverageRegion**](#getcoverageregion) | **GET** coverage/{region}/

## **getCoverage**

### Parameters

Name | Type | Note
---- | ---- | ----
**disableGeojson** | **Boolean** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coverageApi.getCoverage(
    disableGeojson = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**disableGeojson** | **Boolean** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coverageApi.getCoverageLonLat(
    lat = 0.0,
    lon = 0.0,
    disableGeojson = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegion**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**disableGeojson** | **Boolean** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().coverageApi.getCoverageRegion(
    region = "region_example",
    disableGeojson = true
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

