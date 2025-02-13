# Disruption

## Properties

Name | Type | Note
---- | ---- | ----
**id** | **String** | 
**disruptionId** | **String** | [optional] 
**impactId** | **String** | [optional] 
**applicationPeriods** | [**List<Period>**](Period.md) | [optional] 
**applicationPatterns** | [**List<ApplicationPattern>**](ApplicationPattern.md) | [optional] 
**status** | [**Status**](#Status) | [optional] 
**updatedAt** | **String** | [optional] 
**tags** | **List<String>** | [optional] 
**cause** | **String** | 
**category** | **String** | [optional] 
**severity** | [**Severity**](Severity.md) | [optional] 
**messages** | [**List<Message>**](Message.md) | [optional] 
**impactedObjects** | [**List<Impacted>**](Impacted.md) | [optional] 
**uri** | **String** | [optional] 
**disruptionUri** | **String** | [optional] 
**contributor** | **String** | 
**properties** | [**List<DisruptionProperty>**](DisruptionProperty.md) | [optional] 

## Status

Name | Value
---- | -----
PAST | "past"
ACTIVE | "active"
FUTURE | "future"

