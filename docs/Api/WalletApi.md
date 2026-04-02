# OpenAPI\Client\WalletApi

Cryptocurrency wallet management. Supports multiple chains (EVM, UTXO, Solana, Tron, TON, Cardano). **Production flow (non-custodial):** Register addresses (POST /api/wallet/non-custodial/register-address), get network fee (POST /api/wallet/estimate-network-fee or GET /api/wallet/fees), build and sign tx client-side, broadcast (POST /api/wallet/non-custodial/broadcast). Stuck EVM txs: GET replacement params (POST speed-up or cancel), sign and broadcast again. **Custodial endpoints (for testing only):** Create wallet (POST /api/wallet/create), get private key (GET /api/wallet/{walletId}/private-key), register that address in non-custodial, then use estimate-network-fee + broadcast to test the full flow. Custodial withdraw (POST /api/wallet/{walletId}/withdraw) returns a **semi-transaction** (signedTx, chain, fromAddress)—it does not broadcast; you broadcast it via POST /api/wallet/non-custodial/broadcast. Supports all platform chains/currencies. Transactions appear in the same transaction list and can be speed-up/canceled via nonce. **Network fee only:** POST /api/wallet/estimate-network-fee and POST /api/wallet/calculate-fee return **network fee only** (from blockchain). No platform or project fee in fee estimation. See docs/FEE_ARCHITECTURE.md.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**walletBroadcastTransaction()**](WalletApi.md#walletBroadcastTransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**walletCreateWebhook()**](WalletApi.md#walletCreateWebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**walletDeleteAddress()**](WalletApi.md#walletDeleteAddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete (soft-delete) a non-custodial address |
| [**walletDeleteWebhook()**](WalletApi.md#walletDeleteWebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**walletEstimateGas()**](WalletApi.md#walletEstimateGas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**walletGetAddress()**](WalletApi.md#walletGetAddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**walletGetBalance()**](WalletApi.md#walletGetBalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**walletGetCancelParams()**](WalletApi.md#walletGetCancelParams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**walletGetSpeedUpParams()**](WalletApi.md#walletGetSpeedUpParams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**walletGetTransactionByHash()**](WalletApi.md#walletGetTransactionByHash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**walletGetTransactions()**](WalletApi.md#walletGetTransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**walletGetWebhookLogs()**](WalletApi.md#walletGetWebhookLogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**walletListAddresses()**](WalletApi.md#walletListAddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**walletListWebhooks()**](WalletApi.md#walletListWebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**walletRegisterAddress()**](WalletApi.md#walletRegisterAddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**walletTestWebhook()**](WalletApi.md#walletTestWebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**walletUpdateWebhook()**](WalletApi.md#walletUpdateWebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |


## `walletBroadcastTransaction()`

```php
walletBroadcastTransaction($wallet_broadcast_transaction_request): \OpenAPI\Client\Model\WalletBroadcastTransaction200Response
```

Broadcast a client-signed transaction

Broadcast a transaction that has been signed client-side. The transaction must be fully signed before sending. The fromAddress must be registered and belong to your organization (POST /api/wallet/non-custodial/register-address). **Supported chains:** EVM (ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo), UTXO (bitcoin, litecoin, dogecoin), and chain-specific (tron, solana, ton, cardano). Use `binance` or `bsc` for BNB Smart Chain. **Testing with custodial:** You can create a wallet via POST /api/wallet/create, get its private key via GET /api/wallet/{walletId}/private-key, register that address with POST /api/wallet/non-custodial/register-address, then build a signed tx (using POST /api/wallet/estimate-network-fee or estimate-gas for fees) and broadcast it here to test the non-custodial flow end-to-end.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_broadcast_transaction_request = {"chain":"ethereum","signedTx":"0x02f87082012a80843b9aca0082520894def456789012345678901234567890123456789094742d35cc6634c0532925a3b844bc9e7595f0beb880de0b6b3a764000080c001a0...","fromAddress":"0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb"}; // \OpenAPI\Client\Model\WalletBroadcastTransactionRequest | Chain, signed transaction (hex), and fromAddress (must be registered).

try {
    $result = $apiInstance->walletBroadcastTransaction($wallet_broadcast_transaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletBroadcastTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_broadcast_transaction_request** | [**\OpenAPI\Client\Model\WalletBroadcastTransactionRequest**](../Model/WalletBroadcastTransactionRequest.md)| Chain, signed transaction (hex), and fromAddress (must be registered). | |

### Return type

[**\OpenAPI\Client\Model\WalletBroadcastTransaction200Response**](../Model/WalletBroadcastTransaction200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletCreateWebhook()`

```php
walletCreateWebhook($wallet_create_webhook_request): \OpenAPI\Client\Model\WalletCreateWebhook201Response
```

Create a wallet webhook

Register a webhook URL to receive wallet events (balance updates, transaction confirmed/failed/detected/broadcast, token balance, address created/deactivated). Optional filters by addresses and chains.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_create_webhook_request = {"url":"https://your-app.com/webhooks/wallet","events":["wallet.balance.updated","wallet.transaction.confirmed","wallet.transaction.failed"],"secret":"whsec_abc123xyz789"}; // \OpenAPI\Client\Model\WalletCreateWebhookRequest | Webhook URL, events array, optional secret and filters (addresses, chains, projectId).

try {
    $result = $apiInstance->walletCreateWebhook($wallet_create_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletCreateWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_create_webhook_request** | [**\OpenAPI\Client\Model\WalletCreateWebhookRequest**](../Model/WalletCreateWebhookRequest.md)| Webhook URL, events array, optional secret and filters (addresses, chains, projectId). | |

### Return type

[**\OpenAPI\Client\Model\WalletCreateWebhook201Response**](../Model/WalletCreateWebhook201Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletDeleteAddress()`

```php
walletDeleteAddress($address_id): \OpenAPI\Client\Model\FunctionsDelete200Response
```

Delete (soft-delete) a non-custodial address

Soft-deletes a registered non-custodial address. The address is marked inactive and no longer used for broadcasts or balance/transaction queries.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string | Registered address ID to delete.

try {
    $result = $apiInstance->walletDeleteAddress($address_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletDeleteAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**| Registered address ID to delete. | |

### Return type

[**\OpenAPI\Client\Model\FunctionsDelete200Response**](../Model/FunctionsDelete200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletDeleteWebhook()`

```php
walletDeleteWebhook($webhook_id): \OpenAPI\Client\Model\FunctionsDelete200Response
```

Delete a wallet webhook

Permanently delete a wallet webhook. Delivery will stop immediately.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string | Webhook ID (MongoDB ObjectId) to delete.

try {
    $result = $apiInstance->walletDeleteWebhook($webhook_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletDeleteWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**| Webhook ID (MongoDB ObjectId) to delete. | |

### Return type

[**\OpenAPI\Client\Model\FunctionsDelete200Response**](../Model/FunctionsDelete200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletEstimateGas()`

```php
walletEstimateGas($wallet_estimate_gas_request): \OpenAPI\Client\Model\WalletEstimateGas200Response
```

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require `transaction` (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only `chain` is required; `transaction` is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_estimate_gas_request = {"chain":"ethereum","transaction":{"from":"0x742d35Cc6634C0532925a3b844Bc454e4438f44e","to":"0x53d284357ec70cE289D6D64134DfAc8E511c8a3D","value":"1.0"}}; // \OpenAPI\Client\Model\WalletEstimateGasRequest | Chain and optional transaction shape (required for EVM). Returns network fee from blockchain.

try {
    $result = $apiInstance->walletEstimateGas($wallet_estimate_gas_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletEstimateGas: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_estimate_gas_request** | [**\OpenAPI\Client\Model\WalletEstimateGasRequest**](../Model/WalletEstimateGasRequest.md)| Chain and optional transaction shape (required for EVM). Returns network fee from blockchain. | |

### Return type

[**\OpenAPI\Client\Model\WalletEstimateGas200Response**](../Model/WalletEstimateGas200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetAddress()`

```php
walletGetAddress($address_id): \OpenAPI\Client\Model\NonCustodialAddressResponse
```

Get non-custodial address by ID

Returns metadata and status for a single registered non-custodial address (ID, address, chain, label, org, project, derivationPath, isActive, timestamps).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string | Registered address ID (MongoDB ObjectId).

try {
    $result = $apiInstance->walletGetAddress($address_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**| Registered address ID (MongoDB ObjectId). | |

### Return type

[**\OpenAPI\Client\Model\NonCustodialAddressResponse**](../Model/NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetBalance()`

```php
walletGetBalance($address_id): \OpenAPI\Client\Model\WalletGetBalance200Response
```

Get balance for a non-custodial address

Returns native token balance (confirmed, unconfirmed, total, currency) for a registered non-custodial address. Updated periodically from the chain.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string | Registered address ID.

try {
    $result = $apiInstance->walletGetBalance($address_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetBalance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**| Registered address ID. | |

### Return type

[**\OpenAPI\Client\Model\WalletGetBalance200Response**](../Model/WalletGetBalance200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetCancelParams()`

```php
walletGetCancelParams($wallet_get_cancel_params_request): \OpenAPI\Client\Model\WalletGetCancelParams200Response
```

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to=self, value=0, data=0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_get_cancel_params_request = {"txHash":"0xabc123...","chain":"ethereum"}; // \OpenAPI\Client\Model\WalletGetCancelParamsRequest | Stuck transaction identifier (txId or txHash) and EVM chain for cancel.

try {
    $result = $apiInstance->walletGetCancelParams($wallet_get_cancel_params_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetCancelParams: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_get_cancel_params_request** | [**\OpenAPI\Client\Model\WalletGetCancelParamsRequest**](../Model/WalletGetCancelParamsRequest.md)| Stuck transaction identifier (txId or txHash) and EVM chain for cancel. | |

### Return type

[**\OpenAPI\Client\Model\WalletGetCancelParams200Response**](../Model/WalletGetCancelParams200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetSpeedUpParams()`

```php
walletGetSpeedUpParams($wallet_get_speed_up_params_request): \OpenAPI\Client\Model\WalletGetSpeedUpParams200Response
```

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending >5 min (stuck). EVM chains only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_get_speed_up_params_request = {"txHash":"0xabc123...","chain":"ethereum"}; // \OpenAPI\Client\Model\WalletGetSpeedUpParamsRequest | Stuck transaction identifier (txId or txHash) and EVM chain.

try {
    $result = $apiInstance->walletGetSpeedUpParams($wallet_get_speed_up_params_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetSpeedUpParams: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_get_speed_up_params_request** | [**\OpenAPI\Client\Model\WalletGetSpeedUpParamsRequest**](../Model/WalletGetSpeedUpParamsRequest.md)| Stuck transaction identifier (txId or txHash) and EVM chain. | |

### Return type

[**\OpenAPI\Client\Model\WalletGetSpeedUpParams200Response**](../Model/WalletGetSpeedUpParams200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetTransactionByHash()`

```php
walletGetTransactionByHash($tx_hash, $chain): \OpenAPI\Client\Model\WalletGetTransactionByHash200Response
```

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$tx_hash = 'tx_hash_example'; // string | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO)
$chain = 'chain_example'; // string | Chain the transaction belongs to (required for lookup)

try {
    $result = $apiInstance->walletGetTransactionByHash($tx_hash, $chain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetTransactionByHash: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **tx_hash** | **string**| Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO) | |
| **chain** | **string**| Chain the transaction belongs to (required for lookup) | |

### Return type

[**\OpenAPI\Client\Model\WalletGetTransactionByHash200Response**](../Model/WalletGetTransactionByHash200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetTransactions()`

```php
walletGetTransactions($address_id, $limit, $page): \OpenAPI\Client\Model\WalletGetTransactions200Response
```

Get transaction history for a non-custodial address

Returns paginated transaction history for a registered non-custodial address (incoming/outgoing, status, confirmations, amounts).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string | Registered address ID.
$limit = 50; // int | Number of transactions per page.
$page = 1; // int | Page number (1-based).

try {
    $result = $apiInstance->walletGetTransactions($address_id, $limit, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetTransactions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**| Registered address ID. | |
| **limit** | **int**| Number of transactions per page. | [optional] [default to 50] |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |

### Return type

[**\OpenAPI\Client\Model\WalletGetTransactions200Response**](../Model/WalletGetTransactions200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletGetWebhookLogs()`

```php
walletGetWebhookLogs($webhook_id, $limit): \OpenAPI\Client\Model\WalletGetWebhookLogs200Response
```

Get webhook delivery logs

List delivery attempts for a wallet webhook (success/failure, payload, response, duration). Paginated by limit.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string | Webhook ID (MongoDB ObjectId) to get logs for.
$limit = 50; // int | Maximum number of log entries to return.

try {
    $result = $apiInstance->walletGetWebhookLogs($webhook_id, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletGetWebhookLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**| Webhook ID (MongoDB ObjectId) to get logs for. | |
| **limit** | **int**| Maximum number of log entries to return. | [optional] [default to 50] |

### Return type

[**\OpenAPI\Client\Model\WalletGetWebhookLogs200Response**](../Model/WalletGetWebhookLogs200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletListAddresses()`

```php
walletListAddresses($chain, $project_id): \OpenAPI\Client\Model\WalletListAddresses200Response
```

List registered non-custodial addresses

Returns all non-custodial addresses registered for the current project/organization. Optional filters by chain and projectId. Addresses must be registered via POST /api/wallet/non-custodial/register-address before use.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$chain = 'chain_example'; // string | Filter by chain (optional)
$project_id = 'project_id_example'; // string | Filter by project ID (optional).

try {
    $result = $apiInstance->walletListAddresses($chain, $project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletListAddresses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **chain** | **string**| Filter by chain (optional) | [optional] |
| **project_id** | **string**| Filter by project ID (optional). | [optional] |

### Return type

[**\OpenAPI\Client\Model\WalletListAddresses200Response**](../Model/WalletListAddresses200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletListWebhooks()`

```php
walletListWebhooks($project_id): \OpenAPI\Client\Model\WalletListWebhooks200Response
```

List wallet webhooks

Returns all wallet webhooks for the current context, optionally filtered by projectId. Includes delivery stats and active status.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Filter by project ID (optional).

try {
    $result = $apiInstance->walletListWebhooks($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletListWebhooks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Filter by project ID (optional). | [optional] |

### Return type

[**\OpenAPI\Client\Model\WalletListWebhooks200Response**](../Model/WalletListWebhooks200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletRegisterAddress()`

```php
walletRegisterAddress($wallet_register_address_request): \OpenAPI\Client\Model\NonCustodialAddressResponse
```

Register a non-custodial wallet address

Register a public wallet address for balance monitoring, transaction indexing, and webhook notifications. Keys are never sent to the server; generation and signing happen client-side only. Supports EVM, UTXO, Solana, Tron, TON, Cardano, and other chains. Optionally provide derivation path and label for multi-address tracking.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_register_address_request = {"address":"0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb","chain":"ethereum","derivationPath":"m/44'/60'/0'/0/5","label":"Main Ethereum Wallet"}; // \OpenAPI\Client\Model\WalletRegisterAddressRequest | Public address, chain identifier, and optional derivation path and label. projectId scopes the registration to a project.

try {
    $result = $apiInstance->walletRegisterAddress($wallet_register_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletRegisterAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_register_address_request** | [**\OpenAPI\Client\Model\WalletRegisterAddressRequest**](../Model/WalletRegisterAddressRequest.md)| Public address, chain identifier, and optional derivation path and label. projectId scopes the registration to a project. | |

### Return type

[**\OpenAPI\Client\Model\NonCustodialAddressResponse**](../Model/NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletTestWebhook()`

```php
walletTestWebhook($wallet_test_webhook_request): \OpenAPI\Client\Model\MultiRoleGetPermissionsMatrix200Response
```

Test a webhook delivery (sends a single test payload)

Sends a test payload to the given URL to verify webhook connectivity and signature. Uses the same signing as real deliveries.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_test_webhook_request = {"url":"https://your-app.com/webhooks/test","secret":"whsec_test_abc123","projectId":"685ad30be129932fbb7a1047","event":"wallet.transaction.detected"}; // \OpenAPI\Client\Model\WalletTestWebhookRequest | URL to send the test POST to; optional secret and projectId for scoping; optional event type to simulate.

try {
    $result = $apiInstance->walletTestWebhook($wallet_test_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletTestWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_test_webhook_request** | [**\OpenAPI\Client\Model\WalletTestWebhookRequest**](../Model/WalletTestWebhookRequest.md)| URL to send the test POST to; optional secret and projectId for scoping; optional event type to simulate. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleGetPermissionsMatrix200Response**](../Model/MultiRoleGetPermissionsMatrix200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `walletUpdateWebhook()`

```php
walletUpdateWebhook($webhook_id, $wallet_update_webhook_request): \OpenAPI\Client\Model\WalletUpdateWebhook200Response
```

Update a wallet webhook

Update webhook URL, events, secret, or filters. Partially applied; only provided fields are updated.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string | Webhook ID (MongoDB ObjectId) to update.
$wallet_update_webhook_request = {"url":"https://your-app.com/webhooks/updated","events":["wallet.transaction.confirmed","wallet.transaction.detected"],"secret":"whsec_newsecret123","filters":{"addresses":["65a1b2c3d4e5f6789012345a"],"chains":["celo","ethereum"]}}; // \OpenAPI\Client\Model\WalletUpdateWebhookRequest | Fields to update (url, events, secret, filters). Omitted fields are left unchanged.

try {
    $result = $apiInstance->walletUpdateWebhook($webhook_id, $wallet_update_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->walletUpdateWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**| Webhook ID (MongoDB ObjectId) to update. | |
| **wallet_update_webhook_request** | [**\OpenAPI\Client\Model\WalletUpdateWebhookRequest**](../Model/WalletUpdateWebhookRequest.md)| Fields to update (url, events, secret, filters). Omitted fields are left unchanged. | |

### Return type

[**\OpenAPI\Client\Model\WalletUpdateWebhook200Response**](../Model/WalletUpdateWebhook200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
