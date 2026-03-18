# # PaymentIntent

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**payment_id** | **string** | Unique payment identifier | [optional]
**merchant** | **string** | Merchant ID | [optional]
**project** | **string** | Project ID | [optional]
**amount** | **float** | Payment amount | [optional]
**currency** | **string** |  | [optional] [default to 'USD']
**network** | **string** |  | [optional]
**token** | **string** |  | [optional]
**type** | **string** |  | [optional]
**status** | **string** |  | [optional]
**finality_status** | **string** |  | [optional]
**total_due** | **float** | Total amount due including fees | [optional]
**commission** | **float** | Platform commission | [optional]
**merchant_receives** | **float** | Amount merchant receives after commission | [optional]
**expires_at** | **\DateTime** |  | [optional]
**metadata** | **object** | Additional metadata | [optional]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
