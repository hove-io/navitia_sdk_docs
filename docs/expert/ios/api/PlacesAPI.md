# PlacesAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatPlaces**](#getCoverageLonLatPlaces) | **GET** /coverage/{lon};{lat}/places
[**getCoverageRegionPlaces**](#getCoverageRegionPlaces) | **GET** /coverage/{region}/places
[**getPlaces**](#getPlaces) | **GET** /places

## **getCoverageLonLatPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**type** | [**[String]**](String.md) | The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**[String]**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placesApi.getCoverageLonLatPlaces(
    q: "q_example", 
    lat: 3.4, 
    lon: 3.4, 
    type: ["[u'stop_area', u'address', u'poi', u'administrative_region']"], 
    count: 10, 
    adminUri: ["adminUri_example"], 
    depth: 1, 
    disableGeojson: true, 
    from: "from_example", 
    shape: "shape_example", 
    shapeScope: ["shapeScope_example"], 
    placesProximityRadius: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**region** | **String** | The region you want to query 
**type** | [**[String]**](String.md) | The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**[String]**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placesApi.getCoverageRegionPlaces(
    q: "q_example", 
    region: "region_example", 
    type: ["[u'stop_area', u'address', u'poi', u'administrative_region']"], 
    count: 10, 
    adminUri: ["adminUri_example"], 
    depth: 1, 
    disableGeojson: true, 
    from: "from_example", 
    shape: "shape_example", 
    shapeScope: ["shapeScope_example"], 
    placesProximityRadius: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getPlaces**

### Parameters

Name | Type | Note
---- | ---- | ----
**q** | **String** | The data to search 
**type** | [**[String]**](String.md) | The type of data to search [optional] [default to [u&#39;stop_area&#39;, u&#39;address&#39;, u&#39;poi&#39;, u&#39;administrative_region&#39;]] [enum: stop_point, poi, administrative_region, stop_area, address] 
**count** | **Int** | The maximum number of places returned [optional] [default to 10] 
**adminUri** | [**[String]**](String.md) | If filled, will restrain the search within the given admin uris [optional] 
**depth** | **Int** | The depth of objects [optional] [default to 1] 
**disableGeojson** | **Bool** | remove geojson from the response [optional] 
**from** | **String** | Coordinates longitude;latitude used to prioritize the objects around this coordinate [optional] 
**shape** | **String** | Geographical shape to limit the search. [optional] 
**shapeScope** | [**[String]**](String.md) | The scope shape on data to search [optional] [enum: admin, street, addr, poi, stop] 
**placesProximityRadius** | **Float** | Radius used to prioritize the objects around coordinate from [optional] 

### Return
[**Places**](../model/Places.md)


<h3>Example</h3>
```swift
Expert.shared.placesApi.getPlaces(
    q: "q_example", 
    type: ["[u'stop_area', u'address', u'poi', u'administrative_region']"], 
    count: 10, 
    adminUri: ["adminUri_example"], 
    depth: 1, 
    disableGeojson: true, 
    from: "from_example", 
    shape: "shape_example", 
    shapeScope: ["shapeScope_example"], 
    placesProximityRadius: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

