# EquipmentReportsAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLatEquipmentReports**](#getCoordLonLatEquipmentReports) | **GET** /coord/{lon};{lat}/equipment_reports
[**getCoordsLonLatEquipmentReports**](#getCoordsLonLatEquipmentReports) | **GET** /coords/{lon};{lat}/equipment_reports
[**getCoverageLonLatEquipmentReports**](#getCoverageLonLatEquipmentReports) | **GET** /coverage/{lon};{lat}/equipment_reports
[**getCoverageLonLatUriEquipmentReports**](#getCoverageLonLatUriEquipmentReports) | **GET** /coverage/{lon};{lat}/{uri}/equipment_reports
[**getCoverageRegionEquipmentReports**](#getCoverageRegionEquipmentReports) | **GET** /coverage/{region}/equipment_reports
[**getCoverageRegionUriEquipmentReports**](#getCoverageRegionUriEquipmentReports) | **GET** /coverage/{region}/{uri}/equipment_reports

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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoordLonLatEquipmentReports(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoordsLonLatEquipmentReports(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoverageLonLatEquipmentReports(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoverageLonLatUriEquipmentReports(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoverageRegionEquipmentReports(
    region: "region_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 

### Return
[**EquipmentReports**](../model/EquipmentReports.md)


<h3>Example</h3>
```swift
Expert.shared.equipmentReportsApi.getCoverageRegionUriEquipmentReports(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    filter: "filter_example", 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

