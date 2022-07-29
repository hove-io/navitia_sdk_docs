# CoordsAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatCoord**](#getCoverageLonLatCoord) | **GET** /coverage/{lon};{lat}/coord
[**getCoverageLonLatCoordId**](#getCoverageLonLatCoordId) | **GET** /coverage/{lon};{lat}/coord/{id}
[**getCoverageLonLatCoords**](#getCoverageLonLatCoords) | **GET** /coverage/{lon};{lat}/coords
[**getCoverageLonLatCoordsId**](#getCoverageLonLatCoordsId) | **GET** /coverage/{lon};{lat}/coords/{id}
[**getCoverageLonLatUriCoord**](#getCoverageLonLatUriCoord) | **GET** /coverage/{lon};{lat}/{uri}/coord
[**getCoverageLonLatUriCoordId**](#getCoverageLonLatUriCoordId) | **GET** /coverage/{lon};{lat}/{uri}/coord/{id}
[**getCoverageLonLatUriCoords**](#getCoverageLonLatUriCoords) | **GET** /coverage/{lon};{lat}/{uri}/coords
[**getCoverageLonLatUriCoordsId**](#getCoverageLonLatUriCoordsId) | **GET** /coverage/{lon};{lat}/{uri}/coords/{id}
[**getCoverageRegionCoord**](#getCoverageRegionCoord) | **GET** /coverage/{region}/coord
[**getCoverageRegionCoordId**](#getCoverageRegionCoordId) | **GET** /coverage/{region}/coord/{id}
[**getCoverageRegionCoords**](#getCoverageRegionCoords) | **GET** /coverage/{region}/coords
[**getCoverageRegionCoordsId**](#getCoverageRegionCoordsId) | **GET** /coverage/{region}/coords/{id}
[**getCoverageRegionUriCoord**](#getCoverageRegionUriCoord) | **GET** /coverage/{region}/{uri}/coord
[**getCoverageRegionUriCoordId**](#getCoverageRegionUriCoordId) | **GET** /coverage/{region}/{uri}/coord/{id}
[**getCoverageRegionUriCoords**](#getCoverageRegionUriCoords) | **GET** /coverage/{region}/{uri}/coords
[**getCoverageRegionUriCoordsId**](#getCoverageRegionUriCoordsId) | **GET** /coverage/{region}/{uri}/coords/{id}

## **getCoverageLonLatCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatCoord(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatCoordId(
    lat: 3.4, 
    lon: 3.4, 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatCoords(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatCoordsId(
    lat: 3.4, 
    lon: 3.4, 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatUriCoord(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatUriCoordId(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatUriCoords(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageLonLatUriCoordsId(
    lat: 3.4, 
    lon: 3.4, 
    uri: "uri_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionCoord(
    region: "region_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionCoordId(
    region: "region_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionCoords(
    region: "region_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionCoordsId(
    region: "region_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriCoord**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionUriCoord(
    region: "region_example", 
    uri: "uri_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriCoordId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionUriCoordId(
    region: "region_example", 
    uri: "uri_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriCoords**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionUriCoords(
    region: "region_example", 
    uri: "uri_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriCoordsId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.coordsApi.getCoverageRegionUriCoordsId(
    region: "region_example", 
    uri: "uri_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

