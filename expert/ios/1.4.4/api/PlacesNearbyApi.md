---
layout: main
title: PlacesNearbyApi
nav_exclude: true
permalink: /expert/ios/api/PlacesNearbyApi
---

# PlacesNearbyApi

---

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
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoordLonLatPlacesNearbyRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoordsLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoordsLonLatPlacesNearbyRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageLonLatPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoverageLonLatPlacesNearbyRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageLonLatUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoverageLonLatUriPlacesNearbyRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageRegionPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoverageRegionPlacesNearbyRequestBuilder()
    .withRegion("region_example")
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

## **getCoverageRegionUriPlacesNearby**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**type** | [**[String]**](String.md)| Type of the objects to return [optional] [default to [u&#39;stop_area&#39;, u&#39;stop_point&#39;, u&#39;poi&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**filter** | **String**| Filter your objects [optional] 
**distance** | **Int**| Distance range of the query in meters [optional] [default to 500] 
**count** | **Int**| Elements per page [optional] [default to 10] 
**depth** | **Int**| Maximum depth on objects [optional] [default to 1] 
**startPage** | **Int**| The page number of the ptref result [optional] 
**bssStands** | **Bool**| DEPRECATED, Use add_poi_infos[]&#x3D;bss_stands [optional] 
**addPoiInfos** | [**[String]**](String.md)| Show more information about the poi if it&#39;s available, for instance, show BSS/car park availability in the pois(BSS/car park) of the response [optional] [default to [u&#39;bss_stands&#39;, u&#39;car_park&#39;]] [enum: bss_stands, car_park, , none] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**disableDisruption** | **Bool**| remove disruptions from the response [optional] 

### Return
[**PlacesNearby**](../model/PlacesNearby)


### Example
```swift
navitiaSDK.placesNearbyApi.newCoverageRegionUriPlacesNearbyRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withType(["[u'stop_area', u'stop_point', u'poi']"])
    .withFilter("filter_example")
    .withDistance(500)
    .withCount(10)
    .withDepth(1)
    .withStartPage(56)
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

