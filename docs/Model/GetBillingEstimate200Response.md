# # GetBillingEstimate200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**period** | **string** | Current month YYYY-MM | [optional]
**line_items** | [**\OpenAPI\Client\Model\GetBillingEstimate200ResponseLineItemsInner[]**](GetBillingEstimate200ResponseLineItemsInner.md) |  | [optional]
**estimated_overage_cents** | **float** |  | [optional]
**estimated_overage** | **string** |  | [optional]
**forecast_overage_cents** | **float** |  | [optional]
**forecast_overage** | **string** |  | [optional]
**message** | **string** | Human-readable forecast when applicable | [optional]
**spend_limits** | [**\OpenAPI\Client\Model\GetBillingEstimate200ResponseSpendLimits**](GetBillingEstimate200ResponseSpendLimits.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
