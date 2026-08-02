# # Withdraw200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**transaction_id** | **string** |  | [optional]
**status** | **string** |  | [optional]
**signed_tx** | **string** | Signed transaction (hex for EVM/UTXO, base64 for Solana, object for Tron). Send as-is in broadcast body. | [optional]
**chain** | **string** | Chain id for broadcast (e.g. ethereum, bitcoin, solana). | [optional]
**from_address** | **string** | Sender address; must be registered for org when broadcasting. | [optional]
**currency** | **string** |  | [optional]
**amount** | **float** |  | [optional]
**to_address** | **string** |  | [optional]
**message** | **string** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
