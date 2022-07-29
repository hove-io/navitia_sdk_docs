# VehicleJourneysAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatUriVehicleJourneys**](#getCoverageLonLatUriVehicleJourneys) | **GET** /coverage/{lon};{lat}/{uri}/vehicle_journeys
[**getCoverageLonLatUriVehicleJourneysId**](#getCoverageLonLatUriVehicleJourneysId) | **GET** /coverage/{lon};{lat}/{uri}/vehicle_journeys/{id}
[**getCoverageLonLatVehicleJourneys**](#getCoverageLonLatVehicleJourneys) | **GET** /coverage/{lon};{lat}/vehicle_journeys
[**getCoverageLonLatVehicleJourneysId**](#getCoverageLonLatVehicleJourneysId) | **GET** /coverage/{lon};{lat}/vehicle_journeys/{id}
[**getCoverageRegionUriVehicleJourneys**](#getCoverageRegionUriVehicleJourneys) | **GET** /coverage/{region}/{uri}/vehicle_journeys
[**getCoverageRegionUriVehicleJourneysId**](#getCoverageRegionUriVehicleJourneysId) | **GET** /coverage/{region}/{uri}/vehicle_journeys/{id}
[**getCoverageRegionVehicleJourneys**](#getCoverageRegionVehicleJourneys) | **GET** /coverage/{region}/vehicle_journeys
[**getCoverageRegionVehicleJourneysId**](#getCoverageRegionVehicleJourneysId) | **GET** /coverage/{region}/vehicle_journeys/{id}
[**getVehicleJourneys**](#getVehicleJourneys) | **GET** /vehicle_journeys

## **getCoverageLonLatUriVehicleJourneys**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageLonLatUriVehicleJourneys(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriVehicleJourneysId**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageLonLatUriVehicleJourneysId(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatVehicleJourneys**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageLonLatVehicleJourneys(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatVehicleJourneysId**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageLonLatVehicleJourneysId(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriVehicleJourneys**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageRegionUriVehicleJourneys(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriVehicleJourneysId**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageRegionUriVehicleJourneysId(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionVehicleJourneys**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageRegionVehicleJourneys(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionVehicleJourneysId**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getCoverageRegionVehicleJourneysId(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getVehicleJourneys**

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

### Return
[**VehicleJourneys**](../model/VehicleJourneys.md)


<h3>Example</h3>
```swift
Expert.shared.vehicleJourneysApi.getVehicleJourneys(
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
    tags: ["tags_example"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

