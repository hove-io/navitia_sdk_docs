# LineReportsAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatLineReports**](#getCoverageLonLatLineReports) | **GET** /coverage/{lon};{lat}/line_reports
[**getCoverageLonLatUriLineReports**](#getCoverageLonLatUriLineReports) | **GET** /coverage/{lon};{lat}/{uri}/line_reports
[**getCoverageRegionLineReports**](#getCoverageRegionLineReports) | **GET** /coverage/{region}/line_reports
[**getCoverageRegionUriLineReports**](#getCoverageRegionUriLineReports) | **GET** /coverage/{region}/{uri}/line_reports

## **getCoverageLonLatLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 
**filterStatus** | [**[String]**](String.md) | filter_status uris [optional] [enum: past, active, future] 

### Return
[**LineReports**](../model/LineReports.md)


<h3>Example</h3>
```swift
Expert.shared.lineReportsApi.getCoverageLonLatLineReports(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"], 
    disableGeojson: true, 
    since: Date(), 
    until: Date(), 
    filterStatus: ["filterStatus_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 
**filterStatus** | [**[String]**](String.md) | filter_status uris [optional] [enum: past, active, future] 

### Return
[**LineReports**](../model/LineReports.md)


<h3>Example</h3>
```swift
Expert.shared.lineReportsApi.getCoverageLonLatUriLineReports(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"], 
    disableGeojson: true, 
    since: Date(), 
    until: Date(), 
    filterStatus: ["filterStatus_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 
**filterStatus** | [**[String]**](String.md) | filter_status uris [optional] [enum: past, active, future] 

### Return
[**LineReports**](../model/LineReports.md)


<h3>Example</h3>
```swift
Expert.shared.lineReportsApi.getCoverageRegionLineReports(
    region: "region_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"], 
    disableGeojson: true, 
    since: Date(), 
    until: Date(), 
    filterStatus: ["filterStatus_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriLineReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 25] 
**startPage** | **Int** | The current page [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 
**filterStatus** | [**[String]**](String.md) | filter_status uris [optional] [enum: past, active, future] 

### Return
[**LineReports**](../model/LineReports.md)


<h3>Example</h3>
```swift
Expert.shared.lineReportsApi.getCoverageRegionUriLineReports(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 25, 
    startPage: 56, 
    forbiddenUris: ["forbiddenUris_example"], 
    disableGeojson: true, 
    since: Date(), 
    until: Date(), 
    filterStatus: ["filterStatus_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

