# PlacesNearbyAPI

Method | HTTP request
------------- | -------------
[**getCoordLonLatPlacesNearby**](#getCoordLonLatPlacesNearby) | **GET** /coord/{lon};{lat}/places_nearby
[**getCoordsLonLatPlacesNearby**](#getCoordsLonLatPlacesNearby) | **GET** /coords/{lon};{lat}/places_nearby
[**getCoverageLonLatPlacesNearby**](#getCoverageLonLatPlacesNearby) | **GET** /coverage/{lon};{lat}/places_nearby
[**getCoverageLonLatUriPlacesNearby**](#getCoverageLonLatUriPlacesNearby) | **GET** /coverage/{lon};{lat}/{uri}/places_nearby
[**getCoverageRegionPlacesNearby**](#getCoverageRegionPlacesNearby) | **GET** /coverage/{region}/places_nearby
[**getCoverageRegionUriPlacesNearby**](#getCoverageRegionUriPlacesNearby) | **GET** /coverage/{region}/{uri}/places_nearby

## **getCoordLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoordLonLatPlacesNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoordsLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoordsLonLatPlacesNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoverageLonLatPlacesNearby(
    lat: 3.4, 
    lon: 3.4, 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoverageLonLatUriPlacesNearby(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoverageRegionPlacesNearby(
    region: "region_example", 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**type** | [**[String]**](String.md) | Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String** | Filter your objects [optional] 
**distance** | **Int** | Distance range of the query in meters [optional] [default to 500] 
**count** | **Int** | Elements per page [optional] [default to 10] 
**depth** | **Int** | Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int** | The page number of the ptref result [optional] 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby.md)


<h3>Example</h3>
```swift
Expert.shared.placesNearbyApi.getCoverageRegionUriPlacesNearby(
    region: "region_example", 
    uri: "uri_example", 
    type: ["[u'stop_area', u'stop_point', u'poi']"], 
    filter: "filter_example", 
    distance: 500, 
    count: 10, 
    depth: 1, 
    startPage: 56, 
    bssStands: true, 
    addPoiInfos: ["[u'bss_stands', u'car_park']"], 
    disableGeojson: true, 
    disableDisruption: true
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

