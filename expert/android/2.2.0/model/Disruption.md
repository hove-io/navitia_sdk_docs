---
layout: main
title: Disruption
nav_exclude: true
permalink: /expert/android/model/Disruption
---

# Disruption

---

## Properties

Name | Type | Note
---- | ---- | ----
**status** | [**StatusEnum**](#StatusEnum)[optional] 
**category** | **String** | [optional] 
**cause** | **String** | 
**severity** | [**Severity**](Severity.md) | [optional] 
**tags** | **List&lt;String&gt;** | [optional] 
**messages** | [**List&lt;Message&gt;**](Message.md) | [optional] 
**applicationPeriods** | [**List&lt;Period&gt;**](Period.md) | [optional] 
**impactId** | **String** | [optional] 
**disruptionId** | **String** | [optional] 
**updatedAt** | **String** | [optional] 
**uri** | **String** | [optional] 
**impactedObjects** | [**List&lt;Impacted&gt;**](Impacted.md) | [optional] 
**id** | **String** | 
**disruptionUri** | **String** | [optional] 
**contributor** | **String** | 
**applicationPatterns** | [**List&lt;ApplicationPattern&gt;**](ApplicationPattern.md) | [optional] 
**properties** | [**List&lt;DisruptionProperty&gt;**](DisruptionProperty.md) | [optional] 

## StatusEnum
Name | Value
---- | -----
PAST | &quot;past&quot;
ACTIVE | &quot;active&quot;
FUTURE | &quot;future&quot;

