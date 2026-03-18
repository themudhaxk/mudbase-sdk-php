# # BillingCreateCheckoutSession200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**checkout_url** | **string** | Checkout/page URL (crypto) or null when Flutterwave | [optional]
**authorization_url** | **string** | Flutterwave redirect URL (when Flutterwave is used) | [optional]
**access_code** | **string** | Flutterwave access code | [optional]
**reference** | **string** | Payment reference (e.g. mudbase_xxx or pmt_xxx) | [optional]
**payment_id** | **string** | Payment intent ID (crypto) | [optional]
**payment_options** | [**\OpenAPI\Client\Model\BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner[]**](BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner.md) | Multi-chain payment options (crypto) | [optional]
**payment_address** | **string** |  | [optional]
**network** | **string** |  | [optional]
**asset** | **string** |  | [optional]
**amount** | **float** |  | [optional]
**currency** | **string** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
