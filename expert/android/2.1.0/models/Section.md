
# Section

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**links** | [**List&lt;LinkSchema&gt;**](LinkSchema.md) |  | 
**departureDateTime** | **String** | Departure date and time of the section |  [optional]
**baseDepartureDateTime** | **String** | Base-schedule departure date and time of the section |  [optional]
**duration** | **Integer** | Duration of the section (seconds) | 
**id** | **String** |  | 
**from** | [**Place**](Place.md) |  |  [optional]
**arrivalDateTime** | **String** | Arrival date and time of the section |  [optional]
**additionalInformations** | [**List&lt;AdditionalInformationsEnum&gt;**](#List&lt;AdditionalInformationsEnum&gt;) |  |  [optional]
**geojson** | [**SectionGeoJsonSchema**](SectionGeoJsonSchema.md) | GeoJSON of the shape of the section |  [optional]
**ridesharingInformations** | [**RidesharingInformation**](RidesharingInformation.md) |  |  [optional]
**to** | [**Place**](Place.md) |  |  [optional]
**baseArrivalDateTime** | **String** | Base-schedule arrival date and time of the section |  [optional]
**transferType** | [**TransferTypeEnum**](#TransferTypeEnum) |  |  [optional]
**type** | [**TypeEnum**](#TypeEnum) |  |  [optional]
**dataFreshness** | [**DataFreshnessEnum**](#DataFreshnessEnum) |  |  [optional]
**co2Emission** | [**Amount**](Amount.md) |  | 
**path** | [**List&lt;Path&gt;**](Path.md) |  |  [optional]
**cycleLaneLength** | **Integer** |  |  [optional]
**displayInformations** | [**VJDisplayInformation**](VJDisplayInformation.md) |  |  [optional]
**mode** | [**ModeEnum**](#ModeEnum) |  |  [optional]
**ridesharingJourneys** | [**List&lt;Journey&gt;**](Journey.md) |  |  [optional]
**stopDateTimes** | [**List&lt;StopDateTime&gt;**](StopDateTime.md) |  |  [optional]


<a name="List<AdditionalInformationsEnum>"></a>
## Enum: List&lt;AdditionalInformationsEnum&gt;
Name | Value
---- | -----
ODT_WITH_ZONE | &quot;odt_with_zone&quot;
ODT_WITH_STOP_POINT | &quot;odt_with_stop_point&quot;
ODT_WITH_STOP_TIME | &quot;odt_with_stop_time&quot;
HAS_DATETIME_ESTIMATED | &quot;has_datetime_estimated&quot;
REGULAR | &quot;regular&quot;
STAY_IN | &quot;stay_in&quot;


<a name="TransferTypeEnum"></a>
## Enum: TransferTypeEnum
Name | Value
---- | -----
WALKING | &quot;walking&quot;
STAY_IN | &quot;stay_in&quot;


<a name="TypeEnum"></a>
## Enum: TypeEnum
Name | Value
---- | -----
PUBLIC_TRANSPORT | &quot;public_transport&quot;
STREET_NETWORK | &quot;street_network&quot;
WAITING | &quot;waiting&quot;
TRANSFER | &quot;transfer&quot;
BOARDING | &quot;boarding&quot;
LANDING | &quot;landing&quot;
BSS_RENT | &quot;bss_rent&quot;
BSS_PUT_BACK | &quot;bss_put_back&quot;
CROW_FLY | &quot;crow_fly&quot;
PARK | &quot;park&quot;
LEAVE_PARKING | &quot;leave_parking&quot;
ALIGHTING | &quot;alighting&quot;
RIDESHARING | &quot;ridesharing&quot;
ON_DEMAND_TRANSPORT | &quot;on_demand_transport&quot;


<a name="DataFreshnessEnum"></a>
## Enum: DataFreshnessEnum
Name | Value
---- | -----
BASE_SCHEDULE | &quot;base_schedule&quot;
ADAPTED_SCHEDULE | &quot;adapted_schedule&quot;
REALTIME | &quot;realtime&quot;


<a name="ModeEnum"></a>
## Enum: ModeEnum
Name | Value
---- | -----
WALKING | &quot;walking&quot;
BIKE | &quot;bike&quot;
CAR | &quot;car&quot;
BSS | &quot;bss&quot;
RIDESHARING | &quot;ridesharing&quot;
CARNOPARK | &quot;carnopark&quot;
TAXI | &quot;taxi&quot;



