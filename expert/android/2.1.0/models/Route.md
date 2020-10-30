---
layout: default
title: Route
parent: Endpoints
grand_parent: Expert Android
permalink: /expert/android/endpoints/route
---

# Route

---

## Properties

| Name | Type | Description | Notes
| ------------ | ------------- | ------------- | -------------
**direction** | [**Place**](/navitia_sdk_docs/expert/android/endpoints/place) |  |  [optional]
**codes** | [**List&lt;Code&gt;**](/navitia_sdk_docs/expert/android/endpoints/code) |  |  [optional]
**name** | **String** | Name of the object | 
**links** | [**List&lt;LinkSchema&gt;**](/navitia_sdk_docs/expert/android/endpoints/link_schema) |  | 
**physicalModes** | [**List&lt;PhysicalMode&gt;**](/navitia_sdk_docs/expert/android/endpoints/physical_mode) |  |  [optional]
**isFrequence** | [**IsFrequenceEnum**](#IsFrequenceEnum) |  |  [optional]
**comments** | [**List&lt;Comment&gt;**](/navitia_sdk_docs/expert/android/endpoints/comment) |  |  [optional]
**directionType** | **String** |  | 
**geojson** | [**MultiLineStringSchema**](/navitia_sdk_docs/expert/android/endpoints/multi_line_string_schema) |  |  [optional]
**stopPoints** | [**List&lt;StopPoint&gt;**](/navitia_sdk_docs/expert/android/endpoints/stop_point) |  |  [optional]
**line** | [**Line**](/navitia_sdk_docs/expert/android/endpoints/line) |  |  [optional]
**id** | **String** | Identifier of the object | 


<a name="IsFrequenceEnum"></a>
## Enum: IsFrequenceEnum
| Name | Value
| ---- | -----
FALSE | &quot;False&quot;



