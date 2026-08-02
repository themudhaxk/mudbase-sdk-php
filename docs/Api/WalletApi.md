# OpenAPI\Client\WalletApi

Cryptocurrency wallet management. Supports multiple chains (EVM, UTXO, Solana, Tron, TON, Cardano). **Production flow (non-custodial):** Register addresses (POST /api/wallet/non-custodial/register-address), get network fee (POST /api/wallet/estimate-network-fee or GET /api/wallet/fees), build and sign tx client-side, broadcast (POST /api/wallet/non-custodial/broadcast). Stuck EVM txs: GET replacement params (POST speed-up or cancel), sign and broadcast again. **Custodial endpoints (for testing only):** Create wallet (POST /api/wallet/create), get private key (GET /api/wallet/{walletId}/private-key), register that address in non-custodial, then use estimate-network-fee + broadcast to test the full flow. Custodial withdraw (POST /api/wallet/{walletId}/withdraw) returns a **semi-transaction** (signedTx, chain, fromAddress)—it does not broadcast; you broadcast it via POST /api/wallet/non-custodial/broadcast. Supports all platform chains/currencies. Transactions appear in the same transaction list and can be speed-up/canceled via nonce. **Network fee only:** POST /api/wallet/estimate-network-fee and POST /api/wallet/calculate-fee return **network fee only** (from blockchain). No platform or project fee in fee estimation. See docs/FEE_ARCHITECTURE.md.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**broadcastNonCustodialTransaction()**](WalletApi.md#broadcastNonCustodialTransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**calculateWalletFee()**](WalletApi.md#calculateWalletFee) | **POST** /api/wallet/calculate-fee | Get network fee only (alias for POST /api/wallet/estimate-network-fee) |
| [**createWallet()**](WalletApi.md#createWallet) | **POST** /api/wallet/create | Create new wallet (for testing non-custodial) |
| [**createWalletWebhook()**](WalletApi.md#createWalletWebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**deleteNonCustodialAddress()**](WalletApi.md#deleteNonCustodialAddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete or deactivate a monitored wallet address |
| [**deleteWalletWebhook()**](WalletApi.md#deleteWalletWebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**estimateNetworkFee()**](WalletApi.md#estimateNetworkFee) | **POST** /api/wallet/estimate-network-fee | Estimate network fee (preferred; reads from fee oracle cache) |
| [**estimateNonCustodialGas()**](WalletApi.md#estimateNonCustodialGas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**generatePrivateKey()**](WalletApi.md#generatePrivateKey) | **POST** /api/wallet/generate-key | Generate private key |
| [**getAllFees()**](WalletApi.md#getAllFees) | **GET** /api/wallet/fees | Get all chain network fees (fee oracle snapshot) |
| [**getBalance()**](WalletApi.md#getBalance) | **GET** /api/wallet/{walletId}/balance | Get wallet balance |
| [**getCancelParams()**](WalletApi.md#getCancelParams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**getNetworkStatus()**](WalletApi.md#getNetworkStatus) | **GET** /api/wallet/network-status | Get network status (congestion + fee metric per chain) |
| [**getNonCustodialAddress()**](WalletApi.md#getNonCustodialAddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**getNonCustodialBalance()**](WalletApi.md#getNonCustodialBalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**getNonCustodialTransactionByHash()**](WalletApi.md#getNonCustodialTransactionByHash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**getNonCustodialTransactions()**](WalletApi.md#getNonCustodialTransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**getSpeedUpParams()**](WalletApi.md#getSpeedUpParams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**getSupportedCurrencies()**](WalletApi.md#getSupportedCurrencies) | **GET** /api/wallet/currencies | Get supported currencies and chains |
| [**getTransaction()**](WalletApi.md#getTransaction) | **GET** /api/wallet/transactions/{transactionId} | Get transaction details |
| [**getTransactionHistory()**](WalletApi.md#getTransactionHistory) | **GET** /api/wallet/transactions | Get transaction history (custodial wallets; same monitoring as non-custodial) |
| [**getUserWallets()**](WalletApi.md#getUserWallets) | **GET** /api/wallet | Get user wallets |
| [**getWalletFeeConfig()**](WalletApi.md#getWalletFeeConfig) | **GET** /api/wallet/projects/{projectId}/fee-config | Get project fee configuration (for non-custodial / external users) |
| [**getWalletPrivateKey()**](WalletApi.md#getWalletPrivateKey) | **GET** /api/wallet/{walletId}/private-key | Get wallet private key (WARNING: Sensitive data; for testing non-custodial) |
| [**getWalletWebhookLogs()**](WalletApi.md#getWalletWebhookLogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**listNonCustodialAddresses()**](WalletApi.md#listNonCustodialAddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**listWalletWebhooks()**](WalletApi.md#listWalletWebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**registerNonCustodialAddress()**](WalletApi.md#registerNonCustodialAddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**testWalletWebhook()**](WalletApi.md#testWalletWebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**updateNonCustodialAddress()**](WalletApi.md#updateNonCustodialAddress) | **PUT** /api/wallet/non-custodial/addresses/{addressId} | Update a monitored wallet address |
| [**updateWalletFeeConfig()**](WalletApi.md#updateWalletFeeConfig) | **PATCH** /api/wallet/projects/{projectId}/fee-config | Update project fee configuration (for non-custodial / external users) |
| [**updateWalletWebhook()**](WalletApi.md#updateWalletWebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |
| [**validateAddress()**](WalletApi.md#validateAddress) | **POST** /api/wallet/validate-address | Validate cryptocurrency address |
| [**withdraw()**](WalletApi.md#withdraw) | **POST** /api/wallet/{walletId}/withdraw | Prepare withdrawal (semi-transaction; broadcast via non-custodial) |


## `broadcastNonCustodialTransaction()`

```php
broadcastNonCustodialTransaction($broadcast_non_custodial_transaction_request): \OpenAPI\Client\Model\BroadcastNonCustodialTransaction200Response
```

Broadcast a client-signed transaction

Broadcast a transaction that has been signed client-side. The transaction must be fully signed before sending. The fromAddress must be registered and belong to your organization (POST /api/wallet/non-custodial/register-address). **Supported chains:** EVM (ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo), UTXO (bitcoin, litecoin, dogecoin), and chain-specific (tron, solana, ton, cardano). Use `binance` or `bsc` for BNB Smart Chain. **Testing with custodial:** You can create a wallet via POST /api/wallet/create, get its private key via GET /api/wallet/{walletId}/private-key, register that address with POST /api/wallet/non-custodial/register-address, then build a signed tx (using POST /api/wallet/estimate-network-fee or estimate-gas for fees) and broadcast it here to test the non-custodial flow end-to-end.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$broadcast_non_custodial_transaction_request = {"chain":"ethereum","signedTx":"0x02f87082012a80843b9aca0082520894def456789012345678901234567890123456789094742d35cc6634c0532925a3b844bc9e7595f0beb880de0b6b3a764000080c001a0...","fromAddress":"0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb"}; // \OpenAPI\Client\Model\BroadcastNonCustodialTransactionRequest

try {
    $result = $apiInstance->broadcastNonCustodialTransaction($broadcast_non_custodial_transaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->broadcastNonCustodialTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **broadcast_non_custodial_transaction_request** | [**\OpenAPI\Client\Model\BroadcastNonCustodialTransactionRequest**](../Model/BroadcastNonCustodialTransactionRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\BroadcastNonCustodialTransaction200Response**](../Model/BroadcastNonCustodialTransaction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `calculateWalletFee()`

```php
calculateWalletFee($estimate_network_fee_request, $fresh): \OpenAPI\Client\Model\CalculateWalletFee200Response
```

Get network fee only (alias for POST /api/wallet/estimate-network-fee)

Returns **network fee only**, estimated from the blockchain (RPC / fee APIs). No platform fee or project fee. **Same as POST /api/wallet/estimate-network-fee.** Prefer estimate-network-fee for clarity. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). Use `?fresh=1` or header `X-Fee-Fresh: true` for a fresh estimate (bypass cache) right before building the transaction for broadcast.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$estimate_network_fee_request = {"currency":"BTC","amount":0.01}; // \OpenAPI\Client\Model\EstimateNetworkFeeRequest
$fresh = 'fresh_example'; // string | Bypass cache and fetch current fee (use right before building tx for broadcast)

try {
    $result = $apiInstance->calculateWalletFee($estimate_network_fee_request, $fresh);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->calculateWalletFee: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **estimate_network_fee_request** | [**\OpenAPI\Client\Model\EstimateNetworkFeeRequest**](../Model/EstimateNetworkFeeRequest.md)|  | |
| **fresh** | **string**| Bypass cache and fetch current fee (use right before building tx for broadcast) | [optional] |

### Return type

[**\OpenAPI\Client\Model\CalculateWalletFee200Response**](../Model/CalculateWalletFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createWallet()`

```php
createWallet($create_wallet_request): \OpenAPI\Client\Model\CreateWallet201Response
```

Create new wallet (for testing non-custodial)

Create a custodial wallet. **Custodial is not used in production.** Use this to **test non-custodial flows**: create a wallet, get its private key (GET /api/wallet/{walletId}/private-key), register the same address with POST /api/wallet/non-custodial/register-address, then use estimate-network-fee and POST /api/wallet/non-custodial/broadcast to build and send a signed transaction. Transaction monitoring (pending/confirmed) applies to both custodial and non-custodial WalletTransaction records.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_wallet_request = {"currency":"CELO","projectId":"6954562e2be74c6233ee53b9","label":"Main Wallet"}; // \OpenAPI\Client\Model\CreateWalletRequest

try {
    $result = $apiInstance->createWallet($create_wallet_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->createWallet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_wallet_request** | [**\OpenAPI\Client\Model\CreateWalletRequest**](../Model/CreateWalletRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreateWallet201Response**](../Model/CreateWallet201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createWalletWebhook()`

```php
createWalletWebhook($create_wallet_webhook_request): \OpenAPI\Client\Model\CreateWalletWebhook201Response
```

Create a wallet webhook

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_wallet_webhook_request = {"url":"https://your-app.com/webhooks/wallet","events":["wallet.balance.updated","wallet.transaction.confirmed","wallet.transaction.failed"],"secret":"whsec_abc123xyz789"}; // \OpenAPI\Client\Model\CreateWalletWebhookRequest

try {
    $result = $apiInstance->createWalletWebhook($create_wallet_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->createWalletWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_wallet_webhook_request** | [**\OpenAPI\Client\Model\CreateWalletWebhookRequest**](../Model/CreateWalletWebhookRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreateWalletWebhook201Response**](../Model/CreateWalletWebhook201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteNonCustodialAddress()`

```php
deleteNonCustodialAddress($address_id, $permanent): \OpenAPI\Client\Model\DeleteFunction200Response
```

Delete or deactivate a monitored wallet address

**Soft delete (default):** Omit **permanent** or set to false. The address is deactivated (isActive = false); it no longer appears in list or receives monitoring but the record remains for audit. **Permanent delete:** Set query **permanent=true** to remove the address record from the database. Use when you need to fully remove the monitored address.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string
$permanent = false; // bool | If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete)

try {
    $result = $apiInstance->deleteNonCustodialAddress($address_id, $permanent);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->deleteNonCustodialAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**|  | |
| **permanent** | **bool**| If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete) | [optional] [default to false] |

### Return type

[**\OpenAPI\Client\Model\DeleteFunction200Response**](../Model/DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteWalletWebhook()`

```php
deleteWalletWebhook($webhook_id): \OpenAPI\Client\Model\DeleteFunction200Response
```

Delete a wallet webhook

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string

try {
    $result = $apiInstance->deleteWalletWebhook($webhook_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->deleteWalletWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\DeleteFunction200Response**](../Model/DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `estimateNetworkFee()`

```php
estimateNetworkFee($estimate_network_fee_request, $fresh): \OpenAPI\Client\Model\EstimateNetworkFee200Response
```

Estimate network fee (preferred; reads from fee oracle cache)

Returns **network fee only** from the blockchain. **Preferred endpoint** for network fee. Uses a fee oracle: fees are polled every 15–20s and cached, so responses are fast and RPC load is minimal (same strategy as large wallets). No platform fee. Request/response identical to POST /api/wallet/calculate-fee (which is an alias). See docs/FEE_ARCHITECTURE.md. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). **Fresh fee before broadcast:** To avoid stuck transactions, get a fresh estimate right before building/signing: use query `?fresh=1` or header `X-Fee-Fresh: true` to bypass cache.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$estimate_network_fee_request = {"currency":"BTC","amount":0.01}; // \OpenAPI\Client\Model\EstimateNetworkFeeRequest
$fresh = 'fresh_example'; // string | Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast)

try {
    $result = $apiInstance->estimateNetworkFee($estimate_network_fee_request, $fresh);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->estimateNetworkFee: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **estimate_network_fee_request** | [**\OpenAPI\Client\Model\EstimateNetworkFeeRequest**](../Model/EstimateNetworkFeeRequest.md)|  | |
| **fresh** | **string**| Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast) | [optional] |

### Return type

[**\OpenAPI\Client\Model\EstimateNetworkFee200Response**](../Model/EstimateNetworkFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `estimateNonCustodialGas()`

```php
estimateNonCustodialGas($estimate_non_custodial_gas_request): \OpenAPI\Client\Model\EstimateNonCustodialGas200Response
```

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require `transaction` (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only `chain` is required; `transaction` is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$estimate_non_custodial_gas_request = {"chain":"ethereum","transaction":{"from":"0x742d35Cc6634C0532925a3b844Bc454e4438f44e","to":"0x53d284357ec70cE289D6D64134DfAc8E511c8a3D","value":"1.0"}}; // \OpenAPI\Client\Model\EstimateNonCustodialGasRequest

try {
    $result = $apiInstance->estimateNonCustodialGas($estimate_non_custodial_gas_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->estimateNonCustodialGas: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **estimate_non_custodial_gas_request** | [**\OpenAPI\Client\Model\EstimateNonCustodialGasRequest**](../Model/EstimateNonCustodialGasRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\EstimateNonCustodialGas200Response**](../Model/EstimateNonCustodialGas200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generatePrivateKey()`

```php
generatePrivateKey($generate_private_key_request): \OpenAPI\Client\Model\GeneratePrivateKey200Response
```

Generate private key

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$generate_private_key_request = {"currency":"BTC"}; // \OpenAPI\Client\Model\GeneratePrivateKeyRequest

try {
    $result = $apiInstance->generatePrivateKey($generate_private_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->generatePrivateKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **generate_private_key_request** | [**\OpenAPI\Client\Model\GeneratePrivateKeyRequest**](../Model/GeneratePrivateKeyRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GeneratePrivateKey200Response**](../Model/GeneratePrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getAllFees()`

```php
getAllFees(): \OpenAPI\Client\Model\GetAllFees200Response
```

Get all chain network fees (fee oracle snapshot)

Returns **all chain network fees** in one call. Reads from the fee oracle cache (no RPC during the request). Each chain returns the **full fee object** (networkFee, gasPriceGwei, congestion, estimatedTime, feeTiers for EVM, etc.) for frontend/UX. Use for dashboards or \"current fees\" screens.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getAllFees();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getAllFees: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetAllFees200Response**](../Model/GetAllFees200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getBalance()`

```php
getBalance($wallet_id): \OpenAPI\Client\Model\GetBalance200Response
```

Get wallet balance

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_id = 'wallet_id_example'; // string

try {
    $result = $apiInstance->getBalance($wallet_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getBalance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetBalance200Response**](../Model/GetBalance200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCancelParams()`

```php
getCancelParams($get_cancel_params_request): \OpenAPI\Client\Model\GetCancelParams200Response
```

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to=self, value=0, data=0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$get_cancel_params_request = {"txHash":"0xabc123...","chain":"ethereum"}; // \OpenAPI\Client\Model\GetCancelParamsRequest

try {
    $result = $apiInstance->getCancelParams($get_cancel_params_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getCancelParams: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **get_cancel_params_request** | [**\OpenAPI\Client\Model\GetCancelParamsRequest**](../Model/GetCancelParamsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GetCancelParams200Response**](../Model/GetCancelParams200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getNetworkStatus()`

```php
getNetworkStatus(): \OpenAPI\Client\Model\GetNetworkStatus200Response
```

Get network status (congestion + fee metric per chain)

Returns **network status** per chain (congestion and main fee metric). Use to show network health before sending transactions. Same data as GET /fees but trimmed to congestion + gasPriceGwei (EVM) or satPerVb (UTXO) and networkFee.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getNetworkStatus();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getNetworkStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetNetworkStatus200Response**](../Model/GetNetworkStatus200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getNonCustodialAddress()`

```php
getNonCustodialAddress($address_id): \OpenAPI\Client\Model\NonCustodialAddressResponse
```

Get non-custodial address by ID

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string

try {
    $result = $apiInstance->getNonCustodialAddress($address_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getNonCustodialAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\NonCustodialAddressResponse**](../Model/NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getNonCustodialBalance()`

```php
getNonCustodialBalance($address_id): \OpenAPI\Client\Model\GetNonCustodialBalance200Response
```

Get balance for a non-custodial address

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string

try {
    $result = $apiInstance->getNonCustodialBalance($address_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getNonCustodialBalance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetNonCustodialBalance200Response**](../Model/GetNonCustodialBalance200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getNonCustodialTransactionByHash()`

```php
getNonCustodialTransactionByHash($tx_hash, $chain): \OpenAPI\Client\Model\GetNonCustodialTransactionByHash200Response
```

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
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
    $result = $apiInstance->getNonCustodialTransactionByHash($tx_hash, $chain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getNonCustodialTransactionByHash: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **tx_hash** | **string**| Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO) | |
| **chain** | **string**| Chain the transaction belongs to (required for lookup) | |

### Return type

[**\OpenAPI\Client\Model\GetNonCustodialTransactionByHash200Response**](../Model/GetNonCustodialTransactionByHash200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getNonCustodialTransactions()`

```php
getNonCustodialTransactions($address_id, $limit, $page): \OpenAPI\Client\Model\GetNonCustodialTransactions200Response
```

Get transaction history for a non-custodial address

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string
$limit = 50; // int
$page = 1; // int

try {
    $result = $apiInstance->getNonCustodialTransactions($address_id, $limit, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getNonCustodialTransactions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 50] |
| **page** | **int**|  | [optional] [default to 1] |

### Return type

[**\OpenAPI\Client\Model\GetNonCustodialTransactions200Response**](../Model/GetNonCustodialTransactions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSpeedUpParams()`

```php
getSpeedUpParams($get_speed_up_params_request): \OpenAPI\Client\Model\GetSpeedUpParams200Response
```

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending >5 min (stuck). EVM chains only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$get_speed_up_params_request = {"txHash":"0xabc123...","chain":"ethereum"}; // \OpenAPI\Client\Model\GetSpeedUpParamsRequest

try {
    $result = $apiInstance->getSpeedUpParams($get_speed_up_params_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getSpeedUpParams: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **get_speed_up_params_request** | [**\OpenAPI\Client\Model\GetSpeedUpParamsRequest**](../Model/GetSpeedUpParamsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GetSpeedUpParams200Response**](../Model/GetSpeedUpParams200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSupportedCurrencies()`

```php
getSupportedCurrencies(): \OpenAPI\Client\Model\GetSupportedCurrencies200Response
```

Get supported currencies and chains

Returns the list of **platform-supported cryptocurrencies and chains** for non-custodial wallets, broadcast, and multi-chain use. Custodial wallet is no longer used in production; this endpoint is the source of truth for supported chains and currencies. **Supported:** BTC, LTC, DOGE, ETH, ETC, CELO, SOL, TRX, TON, Polygon (MATIC), Arbitrum, Optimism, Base, BSC/BNB, Avalanche (AVAX), Cardano (ADA), USDT. Each item includes **code** (currency symbol), **name** (display name), **chain** (chain id for API calls). USDT includes **networks** (ETH, BSC, TRX, SOL, POLYGON). Use **chain** with non-custodial endpoints (register-address, broadcast, estimate-gas). Use **code** for display and fee/currency selection. This is a public endpoint - no authentication required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getSupportedCurrencies();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getSupportedCurrencies: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetSupportedCurrencies200Response**](../Model/GetSupportedCurrencies200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getTransaction()`

```php
getTransaction($transaction_id): \OpenAPI\Client\Model\GetTransaction200Response
```

Get transaction details

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$transaction_id = 'transaction_id_example'; // string

try {
    $result = $apiInstance->getTransaction($transaction_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **transaction_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetTransaction200Response**](../Model/GetTransaction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getTransactionHistory()`

```php
getTransactionHistory($wallet_id, $limit, $page): \OpenAPI\Client\Model\GetTransactionHistory200Response
```

Get transaction history (custodial wallets; same monitoring as non-custodial)

Returns transaction history for custodial wallets. Transactions are stored and monitored the same way as non-custodial (WalletTransaction); status updates (pending, broadcast, confirmed, failed) and stuck detection apply to both.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_id = 'wallet_id_example'; // string
$limit = 20; // int
$page = 1; // int

try {
    $result = $apiInstance->getTransactionHistory($wallet_id, $limit, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getTransactionHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_id** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 20] |
| **page** | **int**|  | [optional] [default to 1] |

### Return type

[**\OpenAPI\Client\Model\GetTransactionHistory200Response**](../Model/GetTransactionHistory200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getUserWallets()`

```php
getUserWallets($project_id, $currency): \OpenAPI\Client\Model\GetUserWallets200Response
```

Get user wallets

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$currency = 'currency_example'; // string

try {
    $result = $apiInstance->getUserWallets($project_id, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getUserWallets: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | [optional] |
| **currency** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\GetUserWallets200Response**](../Model/GetUserWallets200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getWalletFeeConfig()`

```php
getWalletFeeConfig($project_id): \OpenAPI\Client\Model\GetWalletFeeConfig200Response
```

Get project fee configuration (for non-custodial / external users)

Get project-level fee settings (enabled flag and fee percentage). **For non-custodial / external users** — e.g. when your app charges a fee on payouts or transfers. Custodial wallet is no longer used in production. Applies to all supported chains/currencies for that project.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID

try {
    $result = $apiInstance->getWalletFeeConfig($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getWalletFeeConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID | |

### Return type

[**\OpenAPI\Client\Model\GetWalletFeeConfig200Response**](../Model/GetWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getWalletPrivateKey()`

```php
getWalletPrivateKey($wallet_id): \OpenAPI\Client\Model\GetWalletPrivateKey200Response
```

Get wallet private key (WARNING: Sensitive data; for testing non-custodial)

Returns the wallet private key. **For testing non-custodial only:** use this key to sign a transaction locally, then register the wallet address via POST /api/wallet/non-custodial/register-address and broadcast the signed tx via POST /api/wallet/non-custodial/broadcast.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_id = 'wallet_id_example'; // string

try {
    $result = $apiInstance->getWalletPrivateKey($wallet_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getWalletPrivateKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetWalletPrivateKey200Response**](../Model/GetWalletPrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getWalletWebhookLogs()`

```php
getWalletWebhookLogs($webhook_id, $limit): \OpenAPI\Client\Model\GetWalletWebhookLogs200Response
```

Get webhook delivery logs

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string
$limit = 50; // int

try {
    $result = $apiInstance->getWalletWebhookLogs($webhook_id, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->getWalletWebhookLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\OpenAPI\Client\Model\GetWalletWebhookLogs200Response**](../Model/GetWalletWebhookLogs200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listNonCustodialAddresses()`

```php
listNonCustodialAddresses($chain, $project_id): \OpenAPI\Client\Model\ListNonCustodialAddresses200Response
```

List registered non-custodial addresses

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$chain = 'chain_example'; // string | Filter by chain (optional)
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->listNonCustodialAddresses($chain, $project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->listNonCustodialAddresses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **chain** | **string**| Filter by chain (optional) | [optional] |
| **project_id** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\ListNonCustodialAddresses200Response**](../Model/ListNonCustodialAddresses200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listWalletWebhooks()`

```php
listWalletWebhooks($project_id): \OpenAPI\Client\Model\ListWalletWebhooks200Response
```

List wallet webhooks

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->listWalletWebhooks($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->listWalletWebhooks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\ListWalletWebhooks200Response**](../Model/ListWalletWebhooks200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `registerNonCustodialAddress()`

```php
registerNonCustodialAddress($register_non_custodial_address_request): \OpenAPI\Client\Model\NonCustodialAddressResponse
```

Register a non-custodial wallet address

Register a public wallet address for monitoring and indexing. All key operations (generation, signing) occur client-side only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$register_non_custodial_address_request = {"address":"0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb","chain":"ethereum","derivationPath":"m/44'/60'/0'/0/5","label":"Main Ethereum Wallet"}; // \OpenAPI\Client\Model\RegisterNonCustodialAddressRequest

try {
    $result = $apiInstance->registerNonCustodialAddress($register_non_custodial_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->registerNonCustodialAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **register_non_custodial_address_request** | [**\OpenAPI\Client\Model\RegisterNonCustodialAddressRequest**](../Model/RegisterNonCustodialAddressRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\NonCustodialAddressResponse**](../Model/NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `testWalletWebhook()`

```php
testWalletWebhook($test_wallet_webhook_request): \OpenAPI\Client\Model\TestWalletWebhook200Response
```

Test a webhook delivery (sends a single test payload)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$test_wallet_webhook_request = {"url":"https://your-app.com/webhooks/test","secret":"whsec_test_abc123","projectId":"685ad30be129932fbb7a1047","event":"wallet.transaction.detected"}; // \OpenAPI\Client\Model\TestWalletWebhookRequest

try {
    $result = $apiInstance->testWalletWebhook($test_wallet_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->testWalletWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **test_wallet_webhook_request** | [**\OpenAPI\Client\Model\TestWalletWebhookRequest**](../Model/TestWalletWebhookRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\TestWalletWebhook200Response**](../Model/TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateNonCustodialAddress()`

```php
updateNonCustodialAddress($address_id, $update_non_custodial_address_request): \OpenAPI\Client\Model\UpdateNonCustodialAddress200Response
```

Update a monitored wallet address

Update metadata for a registered non-custodial address. Only **label** and **derivationPath** can be updated; address and chain are immutable.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address_id = 'address_id_example'; // string
$update_non_custodial_address_request = {"label":"Main cold wallet","derivationPath":"m/44'/60'/0'/0/1"}; // \OpenAPI\Client\Model\UpdateNonCustodialAddressRequest

try {
    $result = $apiInstance->updateNonCustodialAddress($address_id, $update_non_custodial_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->updateNonCustodialAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address_id** | **string**|  | |
| **update_non_custodial_address_request** | [**\OpenAPI\Client\Model\UpdateNonCustodialAddressRequest**](../Model/UpdateNonCustodialAddressRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\UpdateNonCustodialAddress200Response**](../Model/UpdateNonCustodialAddress200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateWalletFeeConfig()`

```php
updateWalletFeeConfig($project_id, $update_wallet_fee_config_request): \OpenAPI\Client\Model\UpdateWalletFeeConfig200Response
```

Update project fee configuration (for non-custodial / external users)

Update project-level fee settings. **For non-custodial / external users** — e.g. fee charged on payouts or transfers. Custodial wallet is no longer used in production. Applies to **all supported currencies** (BTC, ETH, BNB, LTC, SOL, TRX, USDT). **feePercentage** is a decimal: use `0.01` for 1%, `0.005` for 0.5%, etc. (min 0, max 1).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID
$update_wallet_fee_config_request = {"enabled":true,"feePercentage":0.01}; // \OpenAPI\Client\Model\UpdateWalletFeeConfigRequest

try {
    $result = $apiInstance->updateWalletFeeConfig($project_id, $update_wallet_fee_config_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->updateWalletFeeConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID | |
| **update_wallet_fee_config_request** | [**\OpenAPI\Client\Model\UpdateWalletFeeConfigRequest**](../Model/UpdateWalletFeeConfigRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\UpdateWalletFeeConfig200Response**](../Model/UpdateWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateWalletWebhook()`

```php
updateWalletWebhook($webhook_id, $update_wallet_webhook_request): \OpenAPI\Client\Model\UpdateWalletWebhook200Response
```

Update a wallet webhook

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string
$update_wallet_webhook_request = {"url":"https://your-app.com/webhooks/updated","events":["wallet.transaction.confirmed","wallet.transaction.detected"],"secret":"whsec_newsecret123","filters":{"addresses":["65a1b2c3d4e5f6789012345a"],"chains":["celo","ethereum"]}}; // \OpenAPI\Client\Model\UpdateWalletWebhookRequest

try {
    $result = $apiInstance->updateWalletWebhook($webhook_id, $update_wallet_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->updateWalletWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**|  | |
| **update_wallet_webhook_request** | [**\OpenAPI\Client\Model\UpdateWalletWebhookRequest**](../Model/UpdateWalletWebhookRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateWalletWebhook200Response**](../Model/UpdateWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `validateAddress()`

```php
validateAddress($validate_address_request): \OpenAPI\Client\Model\ValidateAddress200Response
```

Validate cryptocurrency address

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$validate_address_request = {"currency":"BTC","address":"bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh"}; // \OpenAPI\Client\Model\ValidateAddressRequest

try {
    $result = $apiInstance->validateAddress($validate_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->validateAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **validate_address_request** | [**\OpenAPI\Client\Model\ValidateAddressRequest**](../Model/ValidateAddressRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ValidateAddress200Response**](../Model/ValidateAddress200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `withdraw()`

```php
withdraw($wallet_id, $withdraw_request): \OpenAPI\Client\Model\Withdraw200Response
```

Prepare withdrawal (semi-transaction; broadcast via non-custodial)

**Semi-transaction:** Builds and signs the withdrawal but does **not** broadcast. Returns `signedTx`, `chain`, and `fromAddress` so the client can broadcast via POST /api/wallet/non-custodial/broadcast. The wallet address must be registered for your organization before broadcasting. Supports all platform chains/currencies (EVM, UTXO, Tron, Solana, USDT on ETH/BSC/TRX/SOL/POLYGON). Use for testing the non-custodial flow: create custodial wallet, get private key, register address, then call withdraw to get signed tx and broadcast it manually.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WalletApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$wallet_id = 'wallet_id_example'; // string
$withdraw_request = {"toAddress":"bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh","amount":0.1}; // \OpenAPI\Client\Model\WithdrawRequest

try {
    $result = $apiInstance->withdraw($wallet_id, $withdraw_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WalletApi->withdraw: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **wallet_id** | **string**|  | |
| **withdraw_request** | [**\OpenAPI\Client\Model\WithdrawRequest**](../Model/WithdrawRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\Withdraw200Response**](../Model/Withdraw200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
