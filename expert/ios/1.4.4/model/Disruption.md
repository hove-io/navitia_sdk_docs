---
layout: main
title: Disruption
nav_exclude: true
permalink: /expert/ios/model/Disruption
---

# Disruption

---

## Properties

Name | Type | Note
---- | ---- | ----
**status** | [**Status**](#Status) | [optional] 
**category** | **String** | [optional] 
**cause** | **String** | 
**severity** | [**Severity**](Severity.md) | [optional] 
**tags** | **[String]** | [optional] 
**messages** | [**[Message]**](Message.md) | [optional] 
**applicationPeriods** | [**[Period]**](Period.md) | [optional] 
**impactId** | **String** | [optional] 
**disruptionId** | **String** | [optional] 
**updatedAt** | **String** | [optional] 
**uri** | **String** | [optional] 
**impactedObjects** | [**[Impacted]**](Impacted.md) | [optional] 
**id** | **String** | 
**disruptionUri** | **String** | [optional] 
**contributor** | **String** | 
**applicationPatterns** | [**[ApplicationPattern]**](ApplicationPattern.md) | [optional] 
**properties** | [**[DisruptionProperty]**](DisruptionProperty.md) | [optional] 

## Status

Name | Value
---- | -----
past | past
active | active
future | future

