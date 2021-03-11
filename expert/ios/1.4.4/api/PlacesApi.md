---
layout: main
title: PlacesApi
nav_exclude: true
permalink: /expert/ios/api/PlacesApi
---

# PlacesApi

---

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlaces**](#getCoverageLonLatPlaces) | **GET** /coverage/{lon};{lat}/places
[**getCoverageRegionPlaces**](#getCoverageRegionPlaces) | **GET** /coverage/{region}/places
[**getPlaces**](#getPlaces) | **GET** /places

## **getCoverageLonLatPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**type** | [**[String]**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placesApi.newCoverageLonLatPlacesRequestBuilder()
    .withQ("q_example")
    .withLat(3.4)
    .withLon(3.4)
    .withType(["[u'stop_area', u'address', u'poi', u'administrative_region']"])
    .withCount(10)
    .withAdminUri(["adminUri_example"])
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**region** | **String**|  The region you want to query 
**type** | [**[String]**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placesApi.newCoverageRegionPlacesRequestBuilder()
    .withQ("q_example")
    .withRegion("region_example")
    .withType(["[u'stop_area', u'address', u'poi', u'administrative_region']"])
    .withCount(10)
    .withAdminUri(["adminUri_example"])
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String**| The data to search 
**type** | [**[String]**](String.md)| The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int**| The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md)| If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int**| The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool**| remove geojson from the response [optional] 
**from** | **String**| Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String**| Geographical shape to limit the search. [optional] 

### Return
[**Places**](../model/Places)


### Example
```swift
navitiaSDK.placesApi.newPlacesRequestBuilder()
    .withQ("q_example")
    .withType(["[u'stop_area', u'address', u'poi', u'administrative_region']"])
    .withCount(10)
    .withAdminUri(["adminUri_example"])
    .withDepth(1)
    .withDisableGeojson(true)
    .withFrom("from_example")
    .withShape("shape_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

