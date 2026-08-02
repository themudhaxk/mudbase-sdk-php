# # CreatePlanRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** | Display name; also used to generate a unique slug per project. |
**description** | **string** |  | [optional]
**price** | **float** | Amount for the chosen interval. The server fills the other billing period (e.g. yearly ≈ monthly × 12 × 0.8 when interval is month). |
**currency** | **string** | ISO currency code (stored lowercased). |
**interval** | **string** | Which period &#x60;price&#x60; applies to; drives pricing.monthly vs pricing.yearly. |
**features** | [**\OpenAPI\Client\Model\CreatePlanRequestFeaturesInner[]**](CreatePlanRequestFeaturesInner.md) | Strings become &#x60;{ name, included: true }&#x60;. You may send full feature objects instead. | [optional]
**limits** | [**\OpenAPI\Client\Model\CreatePlanRequestLimits**](CreatePlanRequestLimits.md) |  | [optional]
**trial** | [**\OpenAPI\Client\Model\CreatePlanRequestTrial**](CreatePlanRequestTrial.md) |  | [optional]
**is_active** | **bool** |  | [optional] [default to true]
**is_default** | **bool** | Only one default plan per project is allowed server-side. | [optional] [default to false]
**sort_order** | **float** | Lower numbers list first in UIs. | [optional]
**metadata** | **array<string,mixed>** | Arbitrary key/value data stored on the plan document. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
