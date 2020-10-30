---
layout: default
title: Disruption
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/disruption
---

# Disruption

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**status** | [**StatusEnum**](#StatusEnum) |  |  [optional]
**category** | **String** |  |  [optional]
**severity** | [**Severity**](/navitia_sdk_docs/expert/android/endpoints/severity) |  |  [optional]
**tags** | **List&lt;String&gt;** |  |  [optional]
**messages** | [**List&lt;Message&gt;**](/navitia_sdk_docs/expert/android/endpoints/message) |  |  [optional]
**applicationPeriods** | [**List&lt;Period&gt;**](/navitia_sdk_docs/expert/android/endpoints/period) |  |  [optional]
**impactId** | **String** |  |  [optional]
**disruptionId** | **String** |  |  [optional]
**updatedAt** | **String** |  |  [optional]
**uri** | **String** |  |  [optional]
**impactedObjects** | [**List&lt;Impacted&gt;**](/navitia_sdk_docs/expert/android/endpoints/impacted) |  |  [optional]
**id** | **String** |  | 
**disruptionUri** | **String** |  |  [optional]
**contributor** | **String** |  | 
**cause** | **String** |  | 
**properties** | [**List&lt;DisruptionProperty&gt;**](Disruption/navitia_sdk_docs/expert/android/endpoints/property) |  |  [optional]


<a name="StatusEnum"></a>
## Enum: StatusEnum
| Name | Value
| ---- | -----
PAST | &quot;past&quot;
ACTIVE | &quot;active&quot;
FUTURE | &quot;future&quot;



