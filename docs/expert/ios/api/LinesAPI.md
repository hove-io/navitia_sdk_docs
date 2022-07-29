# LinesAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatLines**](#getCoverageLonLatLines) | **GET** /coverage/{lon};{lat}/lines
[**getCoverageLonLatLinesId**](#getCoverageLonLatLinesId) | **GET** /coverage/{lon};{lat}/lines/{id}
[**getCoverageLonLatUriLines**](#getCoverageLonLatUriLines) | **GET** /coverage/{lon};{lat}/{uri}/lines
[**getCoverageLonLatUriLinesId**](#getCoverageLonLatUriLinesId) | **GET** /coverage/{lon};{lat}/{uri}/lines/{id}
[**getCoverageRegionLines**](#getCoverageRegionLines) | **GET** /coverage/{region}/lines
[**getCoverageRegionLinesId**](#getCoverageRegionLinesId) | **GET** /coverage/{region}/lines/{id}
[**getCoverageRegionUriLines**](#getCoverageRegionUriLines) | **GET** /coverage/{region}/{uri}/lines
[**getCoverageRegionUriLinesId**](#getCoverageRegionUriLinesId) | **GET** /coverage/{region}/{uri}/lines/{id}
[**getLines**](#getLines) | **GET** /lines

## **getCoverageLonLatLines**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageLonLatLines(
    lat: 3.4, 
    lon: 3.4, 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    filter: "filter_example", 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatLinesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageLonLatLinesId(
    lat: 3.4, 
    lon: 3.4, 
    id: "id_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriLines**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageLonLatUriLines(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    filter: "filter_example", 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriLinesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageLonLatUriLinesId(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    id: "id_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionLines**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageRegionLines(
    region: "region_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    filter: "filter_example", 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionLinesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageRegionLinesId(
    region: "region_example", 
    id: "id_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriLines**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageRegionUriLines(
    region: "region_example", 
    uri: "uri_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    filter: "filter_example", 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriLinesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**externalCode** | **String** | An external code to query [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getCoverageRegionUriLinesId(
    region: "region_example", 
    uri: "uri_example", 
    id: "id_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    externalCode: "externalCode_example", 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getLines**

### Parameters

Name | Type | Note
---- | ---- | ----
**externalCode** | **String** | An external code to query 
**startPage** | **Int** | The page where you want to start [optional] 
**count** | **Int** | Number of objects you want on a page [optional] [default to 25] 
**depth** | **Int** | The depth of your object [optional] [default to 1] 
**forbiddenId** | [**[String]**](String.md) | DEPRECATED, replaced by &#x60;forbidden_uris[]&#x60; [optional] 
**forbiddenUris** | [**[String]**](String.md) | forbidden uris [optional] 
**headsign** | **String** | filter vehicle journeys on headsign [optional] 
**odtLevel** | **String** | odt level [optional] [default to all] [enum: scheduled, all, zonal, with_stops] 
**dataFreshness** | **String** | Define the freshness of data to use to filter vehicle_journeys along with parameters &amp;since and/or &amp;until . Provides only the vehicle_journeys valid for the data freshness level requested. Using &#x60;&amp;data_freshness&#x3D;base_schedule&#x60; will return all original vehicle_journeys onlywhereas using &#x60;&amp;data_freshness&#x3D;realtime&#x60; will return vehicle_journeys after applyingmodifications by realtime (amended vehicle_journeys, and non-impacted original vehicle_journeys). [optional] [default to base_schedule] [enum: base_schedule, adapted_schedule, realtime] 
**distance** | **Int** | Distance range of the query. Used only if a coord is in the query [optional] [default to 200] 
**since** | **Date** | filters objects not valid before this date [optional] 
**until** | **Date** | filters objects not valid after this date [optional] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 
**filter** | **String** | The filter parameter [optional] 
**tags** | [**[String]**](String.md) | If filled, will restrain the search within the given disruption tags [optional] 
**originalId** | **String** | original uri of the object you want to query [optional] 

### Return
[**Lines**](../model/Lines.md)


<h3>Example</h3>
```swift
Expert.shared.linesApi.getLines(
    externalCode: "externalCode_example", 
    startPage: 56, 
    count: 25, 
    depth: 1, 
    forbiddenId: ["forbiddenId_example"], 
    forbiddenUris: ["forbiddenUris_example"], 
    headsign: "headsign_example", 
    odtLevel: "all", 
    dataFreshness: "base_schedule", 
    distance: 200, 
    since: Date(), 
    until: Date(), 
    disableGeojson: true, 
    disableDisruption: true, 
    filter: "filter_example", 
    tags: ["tags_example"], 
    originalId: "originalId_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

