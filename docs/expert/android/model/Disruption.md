# Disruption

## Properties

Name | Type | Note
---- | ---- | ----
**status** | [**Status**](#Status) | [optional] 
**category** | **String** | [optional] 
**cause** | **String** | 
**severity** | [**Severity**](Severity.md) | [optional] 
**tags** | **List<String>** | [optional] 
**messages** | [**List<Message>**](Message.md) | [optional] 
**applicationPeriods** | [**List<Period>**](Period.md) | [optional] 
**impactId** | **String** | [optional] 
**disruptionId** | **String** | [optional] 
**updatedAt** | **String** | [optional] 
**uri** | **String** | [optional] 
**impactedObjects** | [**List<Impacted>**](Impacted.md) | [optional] 
**id** | **String** | 
**disruptionUri** | **String** | [optional] 
**contributor** | **String** | 
**applicationPatterns** | [**List<ApplicationPattern>**](ApplicationPattern.md) | [optional] 
**properties** | [**List<DisruptionProperty>**](DisruptionProperty.md) | [optional] 

## Status

Name | Value
---- | -----
PAST | "past"
ACTIVE | "active"
FUTURE | "future"

