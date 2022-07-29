# EquipmentReportsApi

Method | HTTP request
------------- | -------------
[**getCoordLonLatEquipmentReports**](#getcoordlonlatequipmentreports) | **GET** coord/{lon};{lat}/equipment_reports
[**getCoordsLonLatEquipmentReports**](#getcoordslonlatequipmentreports) | **GET** coords/{lon};{lat}/equipment_reports
[**getCoverageLonLatEquipmentReports**](#getcoveragelonlatequipmentreports) | **GET** coverage/{lon};{lat}/equipment_reports
[**getCoverageLonLatUriEquipmentReports**](#getcoveragelonlaturiequipmentreports) | **GET** coverage/{lon};{lat}/{uri}/equipment_reports
[**getCoverageRegionEquipmentReports**](#getcoverageregionequipmentreports) | **GET** coverage/{region}/equipment_reports
[**getCoverageRegionUriEquipmentReports**](#getcoverageregionuriequipmentreports) | **GET** coverage/{region}/{uri}/equipment_reports

## **getCoordLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoordLonLatEquipmentReports(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoordsLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoordsLonLatEquipmentReports(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoverageLonLatEquipmentReports(
    lat = 0.0,
    lon = 0.0,
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageLonLatUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoverageLonLatUriEquipmentReports(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoverageRegionEquipmentReports(
    region = "region_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

## **getCoverageRegionUriEquipmentReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**filter** | **String** | Filter your objects [optional] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**List<String>**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().equipmentReportsApi.getCoverageRegionUriEquipmentReports(
    region = "region_example",
    uri = "uri_example",
    depth = 123,
    count = 123,
    filter = "filter_example",
    startPage = 123,
    forbiddenUris = listOf()
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

