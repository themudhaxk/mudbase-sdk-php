# # WalletEstimateGas200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**chain** | **string** | Chain id (e.g. bsc, ethereum, bitcoin) | [optional]
**gas_limit** | **string** | (EVM only) Estimated gas limit from RPC eth_estimateGas | [optional]
**gas_price** | **string** | (EVM only) Gas price in wei | [optional]
**gas_price_gwei** | **float** | (EVM only) Gas price in Gwei | [optional]
**estimated_cost** | **string** | (EVM only) Total cost in wei (gasLimit * gasPrice) | [optional]
**network_fee** | **string** | Human-readable network fee from blockchain (e.g. \&quot;0.00063 ETH\&quot;, \&quot;0.00001 BTC\&quot;) | [optional]
**estimated_time** | **string** | Estimated confirmation time when available | [optional]
**currency** | **string** | Native currency for the chain (ETH, BNB, MATIC, BTC, SOL, TRX, etc.) | [optional]
**sat_per_vb** | **int** | (UTXO only) Satoshis per virtual byte | [optional]
**fee_sat** | **int** | (UTXO only) Estimated fee in satoshis | [optional]
**lamports** | **int** | (Solana only) Fee in lamports | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
