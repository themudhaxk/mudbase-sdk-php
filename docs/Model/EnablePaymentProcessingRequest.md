# # EnablePaymentProcessingRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**country** | **string** | ISO-3166 alpha-2 payout country code, one of the codes returned by GET /payment-processing/countries (e.g. NG, GH, KE, US, GB). |
**business_name** | **string** |  |
**business_mobile** | **string** | Optional, used for payout provider account notifications. | [optional]
**account_bank** | **string** | Bank code, mobile-money network code, routing number, or sort code, depending on country. | [optional]
**account_number** | **string** | Bank/mobile-money account number, IBAN, or similar, depending on country. | [optional]
**bvn** | **string** | Required only when country is NG (Nigeria). | [optional]
**account_type** | **string** | Required only when country is US (checking or savings). | [optional]
**account_holder_name** | **string** | Required only when country is US or GB. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
