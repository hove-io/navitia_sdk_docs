# PlaceUriAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlacesId**](#getCoverageLonLatPlacesId) | **GET** /coverage/{lon};{lat}/places/{id}
[**getCoverageRegionPlacesId**](#getCoverageRegionPlacesId) | **GET** /coverage/{region}/places/{id}
[**getPlacesId**](#getPlacesId) | **GET** /places/{id}

## **getCoverageLonLatPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placeUriApi.getCoverageLonLatPlacesId(
    lat: 3.4, 
    lon: 3.4, 
    id: "id_example", 
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

## **getCoverageRegionPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placeUriApi.getCoverageRegionPlacesId(
    region: "region_example", 
    id: "id_example", 
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

## **getPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**id** | **String** | Id of the object you want to query 
**bssStands** | **Bool** | DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md) | Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**disableDisruption** | **Bool** | remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placeUriApi.getPlacesId(
    id: "id_example", 
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

