---
layout: main
title: AddressesApi
nav_exclude: true
permalink: /expert/ios/api/AddressesApi
---

# AddressesApi

---

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
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageLonLatAddressesRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageLonLatAddressesIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageLonLatUriAddressesRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageLonLatUriAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double**|  The latitude of where the coord you want to query 
**lon** | **Double**|  The longitude of where the coord you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageLonLatUriAddressesIdRequestBuilder()
    .withLat(3.4)
    .withLon(3.4)
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageRegionAddressesRequestBuilder()
    .withRegion("region_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageRegionAddressesIdRequestBuilder()
    .withRegion("region_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageRegionUriAddressesRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

## **getCoverageRegionUriAddressesId**

### Parameters

Name | Type | Note
---- | ---- | ----
**region** | **String**|  The region you want to query 
**uri** | **String**| First part of the uri 
**id** | **String**| Id of the object you want to query 

### Return
[**DictAddresses**](../model/DictAddresses)


### Example
```swift
navitiaSDK.addressesApi.newCoverageRegionUriAddressesIdRequestBuilder()
    .withRegion("region_example")
    .withUri("uri_example")
    .withId("id_example")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```

