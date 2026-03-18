# # PaymentRefund

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**payment_intent** | **string** | Payment intent ID | [optional]
**merchant** | **string** | Merchant ID | [optional]
**amount** | **float** | Refund amount | [optional]
**reason** | **string** | Refund reason | [optional]
**status** | **string** |  | [optional]
**is_cross_chain** | **bool** | True if cross-chain refund | [optional] [default to false]
**source_network** | **string** | Source network for refund | [optional]
**target_network** | **string** | Target network for cross-chain refund | [optional]
**approved_by** | **string** | User ID who approved | [optional]
**approved_at** | **\DateTime** |  | [optional]
**refund_tx** | **string** | Refund transaction hash | [optional]
**refunded_at** | **\DateTime** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
