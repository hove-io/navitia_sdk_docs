# TrafficReportAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatTrafficReports**](#getCoverageLonLatTrafficReports) | **GET** /coverage/{lon};{lat}/traffic_reports
[**getCoverageLonLatUriTrafficReports**](#getCoverageLonLatUriTrafficReports) | **GET** /coverage/{lon};{lat}/{uri}/traffic_reports
[**getCoverageRegionTrafficReports**](#getCoverageRegionTrafficReports) | **GET** /coverage/{region}/traffic_reports
[**getCoverageRegionUriTrafficReports**](#getCoverageRegionUriTrafficReports) | **GET** /coverage/{region}/{uri}/traffic_reports

## **getCoverageLonLatTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)


<h3>Example</h3>
```swift
Expert.shared.trafficReportApi.getCoverageLonLatTrafficReports(
    lat: 3.4, 
    lon: 3.4, 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200, 
    disableGeojson: true, 
    since: Date(), 
    until: Date()
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)


<h3>Example</h3>
```swift
Expert.shared.trafficReportApi.getCoverageLonLatUriTrafficReports(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200, 
    disableGeojson: true, 
    since: Date(), 
    until: Date()
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)


<h3>Example</h3>
```swift
Expert.shared.trafficReportApi.getCoverageRegionTrafficReports(
    region: "region_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200, 
    disableGeojson: true, 
    since: Date(), 
    until: Date()
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriTrafficReports**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**count** | **Int** | Number of objects per page [optional] [default to 10] 
**startPage** | **Int** | The current page [optional] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**since** | **Date** | use disruptions valid after this date [optional] 
**until** | **Date** | use disruptions valid before this date [optional] 

### Return
[**TrafficReports**](../model/TrafficReports.md)


<h3>Example</h3>
```swift
Expert.shared.trafficReportApi.getCoverageRegionUriTrafficReports(
    region: "region_example", 
    uri: "uri_example", 
    depth: 1, 
    count: 10, 
    startPage: 56, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    distance: 200, 
    disableGeojson: true, 
    since: Date(), 
    until: Date()
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

