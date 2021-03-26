---
layout: main
title: PlaceUriApi
nav_exclude: true
permalink: /expert/ios/api/PlaceUriApi
---

# PlaceUriApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlacesId**](#getCoverageLonLatPlacesId) | **GET** /coverage/{lon};{lat}/places/{id}
[**getCoverageRegionPlacesId**](#getCoverageRegionPlacesId) | **GET** /coverage/{region}/places/{id}
[**getPlacesId**](#getPlacesId) | **GET** /places/{id}

## **getCoverageLonLatPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placeUriApi.newCoverageLonLatPlacesIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(["[u'bss_stands', u'car_park']"])
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placeUriApi.newCoverageRegionPlacesIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(["[u'bss_stands', u'car_park']"])
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getPlacesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**id** | **String**| Id of the object you want to query 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placeUriApi.newPlacesIdRequestBuilder()
    .withId("id_example")
    .withBssStands(true)
    .withAddPoiInfos(["[u'bss_stands', u'car_park']"])
    .withDisableGeojson(true)
    .withDisableDisruption(true)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

