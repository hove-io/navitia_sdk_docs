# AddressesAPI

Method | HTTP request
------------- | -------------
[**getCoverageLonLatAddresses**](#getCoverageLonLatAddresses) | **GET** /coverage/{lon};{lat}/addresses
[**getCoverageLonLatAddressesId**](#getCoverageLonLatAddressesId) | **GET** /coverage/{lon};{lat}/addresses/{id}
[**getCoverageLonLatUriAddresses**](#getCoverageLonLatUriAddresses) | **GET** /coverage/{lon};{lat}/{uri}/addresses
[**getCoverageLonLatUriAddressesId**](#getCoverageLonLatUriAddressesId) | **GET** /coverage/{lon};{lat}/{uri}/addresses/{id}
[**getCoverageRegionAddresses**](#getCoverageRegionAddresses) | **GET** /coverage/{region}/addresses
[**getCoverageRegionAddressesId**](#getCoverageRegionAddressesId) | **GET** /coverage/{region}/addresses/{id}
[**getCoverageRegionUriAddresses**](#getCoverageRegionUriAddresses) | **GET** /coverage/{region}/{uri}/addresses
[**getCoverageRegionUriAddressesId**](#getCoverageRegionUriAddressesId) | **GET** /coverage/{region}/{uri}/addresses/{id}

## **getCoverageLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.addressesApi.getCoverageLonLatAddresses(
    lat: 3.4, 
    lon: 3.4
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageLonLatAddressesId**

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
Expert.shared.addressesApi.getCoverageLonLatAddressesId(
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

## **getCoverageLonLatUriAddresses**

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
Expert.shared.addressesApi.getCoverageLonLatUriAddresses(
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

## **getCoverageLonLatUriAddressesId**

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
Expert.shared.addressesApi.getCoverageLonLatUriAddressesId(
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

## **getCoverageRegionAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.addressesApi.getCoverageRegionAddresses(
    region: "region_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**id** | **String** | Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.addressesApi.getCoverageRegionAddressesId(
    region: "region_example", 
    id: "id_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String** | The region you want to query 
**uri** | **String** | First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses.md)


<h3>Example</h3>
```swift
Expert.shared.addressesApi.getCoverageRegionUriAddresses(
    region: "region_example", 
    uri: "uri_example"
) { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
```

## **getCoverageRegionUriAddressesId**

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
Expert.shared.addressesApi.getCoverageRegionUriAddressesId(
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

