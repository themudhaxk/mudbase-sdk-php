# # AdminBillingCheckoutLinkRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**plan** | **string** |  |
**billing_cycle** | **string** |  | [optional] [default to 'monthly']
**amount_cents** | **int** | Monthly amount in cents (overrides catalog; enterprise default is contract) | [optional]
**charge_amount_cents** | **int** | Exact charge in cents for this checkout (overrides monthly math) | [optional]
**currency** | **string** |  | [optional]
**email** | **string** |  | [optional]
**name** | **string** |  | [optional]
**redirect_url** | **string** |  | [optional]
**send_email** | **bool** |  | [optional] [default to false]
**to_email** | **string** |  | [optional]
**message** | **string** | Optional note shown in org_billing_checkout email | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
