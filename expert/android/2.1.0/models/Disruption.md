---
layout: default
title: Address
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/address
---

# Disruption

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**status** | [**StatusEnum**](#StatusEnum) |  |  [optional]
**category** | **String** |  |  [optional]
**severity** | [**Severity**](Severity.md) |  |  [optional]
**tags** | **List&lt;String&gt;** |  |  [optional]
**messages** | [**List&lt;Message&gt;**](Message.md) |  |  [optional]
**applicationPeriods** | [**List&lt;Period&gt;**](Period.md) |  |  [optional]
**impactId** | **String** |  |  [optional]
**disruptionId** | **String** |  |  [optional]
**updatedAt** | **String** |  |  [optional]
**uri** | **String** |  |  [optional]
**impactedObjects** | [**List&lt;Impacted&gt;**](Impacted.md) |  |  [optional]
**id** | **String** |  | 
**disruptionUri** | **String** |  |  [optional]
**contributor** | **String** |  | 
**cause** | **String** |  | 
**properties** | [**List&lt;DisruptionProperty&gt;**](DisruptionProperty.md) |  |  [optional]


<a name="StatusEnum"></a>
## Enum: StatusEnum
Name | Value
---- | -----
PAST | &quot;past&quot;
ACTIVE | &quot;active&quot;
FUTURE | &quot;future&quot;



