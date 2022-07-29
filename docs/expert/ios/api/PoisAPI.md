# PoisAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPois**](#getCoverageLonLatPois) | **GET** /coverage/{lon};{lat}/pois
[**getCoverageLonLatPoisId**](#getCoverageLonLatPoisId) | **GET** /coverage/{lon};{lat}/pois/{id}
[**getCoverageLonLatUriPois**](#getCoverageLonLatUriPois) | **GET** /coverage/{lon};{lat}/{uri}/pois
[**getCoverageLonLatUriPoisId**](#getCoverageLonLatUriPoisId) | **GET** /coverage/{lon};{lat}/{uri}/pois/{id}
[**getCoverageRegionPois**](#getCoverageRegionPois) | **GET** /coverage/{region}/pois
[**getCoverageRegionPoisId**](#getCoverageRegionPoisId) | **GET** /coverage/{region}/pois/{id}
[**getCoverageRegionUriPois**](#getCoverageRegionUriPois) | **GET** /coverage/{region}/{uri}/pois
[**getCoverageRegionUriPoisId**](#getCoverageRegionUriPoisId) | **GET** /coverage/{region}/{uri}/pois/{id}

## **getCoverageLonLatPois**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageLonLatPois(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatPoisId**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageLonLatPoisId(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriPois**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageLonLatUriPois(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriPoisId**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageLonLatUriPoisId(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionPois**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageRegionPois(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionPoisId**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageRegionPoisId(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriPois**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageRegionUriPois(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriPoisId**

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
**bssStands** | **Bool** | Deprecated - Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 

### Return
[**Pois**](../model/Pois.md)


<h3>Example</h3>
```swift
Expert.shared.poisApi.getCoverageRegionUriPoisId(
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
    originalId: "originalId_example", 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"]
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

