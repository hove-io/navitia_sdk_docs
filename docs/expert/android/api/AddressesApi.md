# AddressesApi

Method | HTTP request
------------- | -------------
[**getCoverageLonLatAddresses**](#getcoveragelonlataddresses) | **GET** coverage/{lon};{lat}/addresses
[**getCoverageLonLatAddressesId**](#getcoveragelonlataddressesid) | **GET** coverage/{lon};{lat}/addresses/{id}
[**getCoverageLonLatUriAddresses**](#getcoveragelonlaturiaddresses) | **GET** coverage/{lon};{lat}/{uri}/addresses
[**getCoverageLonLatUriAddressesId**](#getcoveragelonlaturiaddressesid) | **GET** coverage/{lon};{lat}/{uri}/addresses/{id}
[**getCoverageRegionAddresses**](#getcoverageregionaddresses) | **GET** coverage/{region}/addresses
[**getCoverageRegionAddressesId**](#getcoverageregionaddressesid) | **GET** coverage/{region}/addresses/{id}
[**getCoverageRegionUriAddresses**](#getcoverageregionuriaddresses) | **GET** coverage/{region}/{uri}/addresses
[**getCoverageRegionUriAddressesId**](#getcoverageregionuriaddressesid) | **GET** coverage/{region}/{uri}/addresses/{id}

## **getCoverageLonLatAddresses**

### Parameters

Name | Type | Note
---- | ---- | ----
**lat** | **Double** | The latitude of where the coord you want to query 
**lon** | **Double** | The longitude of where the coord you want to query 

### Return
[**DictAddresses**](../model/DictAddresses.md)

<h3>Example</h3>
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageLonLatAddresses(
    lat = 0.0,
    lon = 0.0
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageLonLatAddressesId(
    lat = 0.0,
    lon = 0.0,
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageLonLatUriAddresses(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageLonLatUriAddressesId(
    lat = 0.0,
    lon = 0.0,
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageRegionAddresses(
    region = "region_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageRegionAddressesId(
    region = "region_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageRegionUriAddresses(
    region = "region_example",
    uri = "uri_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
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
```kotlin
ExpertSdk.getInstance().addressesApi.getCoverageRegionUriAddressesId(
    region = "region_example",
    uri = "uri_example",
    id = "id_example"
)

if (response.isSuccessful && response.body() != null) {  
    // Success
    val content = response.body()  
} else {  
    // Error
} 
```

