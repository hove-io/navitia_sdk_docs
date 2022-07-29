# GeoStatusAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatGeoStatus**](#getCoverageLonLatGeoStatus) | **GET** /coverage/{lon};{lat}/_geo_status
[**getCoverageRegionGeoStatus**](#getCoverageRegionGeoStatus) | **GET** /coverage/{region}/_geo_status

## **getCoverageLonLatGeoStatus**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**GeoStatus1**](../model/GeoStatus1.md)


<h3>Example</h3>
```swift
Expert.shared.geoStatusApi.getCoverageLonLatGeoStatus(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
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
```swift
Expert.shared.geoStatusApi.getCoverageRegionGeoStatus(
    region: "region_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

