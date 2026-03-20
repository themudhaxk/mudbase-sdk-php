# # PaymentSubscription

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**merchant** | **string** | Merchant ID | [optional]
**project** | **string** | Project ID | [optional]
**amount** | **float** | Subscription amount | [optional]
**interval** | **string** |  | [optional]
**network** | **string** |  | [optional]
**token** | **string** |  | [optional]
**status** | **string** |  | [optional]
**next_payment_at** | **\DateTime** | Next payment due date | [optional]
**grace_period_days** | **int** | Grace period in days | [optional] [default to 3]
**early_payment_allowed** | **bool** |  | [optional] [default to true]
**late_payment_allowed** | **bool** |  | [optional] [default to true]
**proration_enabled** | **bool** |  | [optional] [default to false]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
