# CoverageAPI

Method | HTTP request
------------- | -------------
[**getCoverage**](#getCoverage) | **GET** /coverage/
[**getCoverageLonLat**](#getCoverageLonLat) | **GET** /coverage/{lon};{lat}/
[**getCoverageRegion**](#getCoverageRegion) | **GET** /coverage/{region}/

## **getCoverage**

### Parameters

Name | Type | Note
---- | ---- | ----
**disableGeojson** | **Bool** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)


<h3>Example</h3>
```swift
Expert.shared.coverageApi.getCoverage(
    disableGeojson: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLat**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**disableGeojson** | **Bool** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)


<h3>Example</h3>
```swift
Expert.shared.coverageApi.getCoverageLonLat(
    lat: 3.4, 
    lon: 3.4, 
    disableGeojson: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegion**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**disableGeojson** | **Bool** | hide the coverage geojson to reduce response size [optional] 

### Return
[**Coverages**](../model/Coverages.md)


<h3>Example</h3>
```swift
Expert.shared.coverageApi.getCoverageRegion(
    region: "region_example", 
    disableGeojson: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

