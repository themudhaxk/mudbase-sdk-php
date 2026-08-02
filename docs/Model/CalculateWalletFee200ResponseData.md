# # CalculateWalletFee200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **string** | Request currency / native currency for the chain | [optional]
**network** | **string** |  | [optional]
**amount** | **float** |  | [optional]
**chain** | **string** | Chain id used for estimation | [optional]
**network_fee** | **string** | Human-readable network fee from blockchain | [optional]
**estimated_time** | **string** |  | [optional]
**congestion** | **string** | Network congestion level (EVM from gas price; UTXO from sat/vB) | [optional]
**gas_limit** | **string** | (EVM only) Gas limit | [optional]
**gas_price** | **string** | (EVM only) Gas price in wei | [optional]
**gas_price_gwei** | **float** | (EVM only) Gas price in Gwei | [optional]
**estimated_cost** | **string** | (EVM only) Cost in wei | [optional]
**sat_per_vb** | **int** | (UTXO only) Satoshis per vbyte | [optional]
**fee_sat** | **int** | (UTXO only) Fee in satoshis | [optional]
**lamports** | **int** | (Solana only) Fee in lamports | [optional]
**fee_tiers** | [**array<string,\OpenAPI\Client\Model\CalculateWalletFee200ResponseDataFeeTiersValue>**](CalculateWalletFee200ResponseDataFeeTiersValue.md) | (EVM only) slow / normal / fast tiers; each has gasPriceGwei, networkFee | [optional]
**gas_spike_warning** | **bool** | True when current gas is ≥5× chain minimum (consider warning user) | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
