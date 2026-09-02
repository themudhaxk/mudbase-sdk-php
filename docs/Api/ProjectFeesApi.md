# OpenAPI\Client\ProjectFeesApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**confirmAddressVerification()**](ProjectFeesApi.md#confirmAddressVerification) | **POST** /api/projects/{projectId}/fee-settings/{currency}/confirm-verification | ~~Confirm address verification~~ (deprecated) |
| [**createOrUpdateFeeSettings()**](ProjectFeesApi.md#createOrUpdateFeeSettings) | **POST** /api/projects/{projectId}/fee-settings | ~~Create or update project fee settings~~ (deprecated) |
| [**getCurrencyFeeBalance()**](ProjectFeesApi.md#getCurrencyFeeBalance) | **GET** /api/projects/{projectId}/fee-balances/{currency} | ~~Get currency fee balance~~ (deprecated) |
| [**getFeeBalances()**](ProjectFeesApi.md#getFeeBalances) | **GET** /api/projects/{projectId}/fee-balances | ~~Get all fee balances~~ (deprecated) |
| [**getFeeSettings()**](ProjectFeesApi.md#getFeeSettings) | **GET** /api/projects/{projectId}/fee-settings | ~~Get project fee settings~~ (deprecated) |
| [**getPayoutHistory()**](ProjectFeesApi.md#getPayoutHistory) | **GET** /api/projects/{projectId}/payout-history | ~~Get payout history~~ (deprecated) |
| [**getProjectFeeDashboard()**](ProjectFeesApi.md#getProjectFeeDashboard) | **GET** /api/projects/{projectId}/fee-dashboard | ~~Get fee dashboard~~ (deprecated) |
| [**initiateAddressVerification()**](ProjectFeesApi.md#initiateAddressVerification) | **POST** /api/projects/{projectId}/fee-settings/{currency}/verify-address | ~~Initiate address verification~~ (deprecated) |
| [**requestManualPayout()**](ProjectFeesApi.md#requestManualPayout) | **POST** /api/projects/{projectId}/payouts/request-manual | ~~Request manual payout~~ (deprecated) |
| [**updateCurrencyFeeSettings()**](ProjectFeesApi.md#updateCurrencyFeeSettings) | **PATCH** /api/projects/{projectId}/fee-settings/{currency} | ~~Update currency fee settings~~ (deprecated) |


## `confirmAddressVerification()`

```php
confirmAddressVerification($project_id, $currency, $confirm_address_verification_request): \OpenAPI\Client\Model\ConfirmAddressVerification200Response
```

~~Confirm address verification~~ (deprecated)

Confirm address verification by providing the transaction hash of the test transaction sent to the payout address. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$currency = 'currency_example'; // string
$confirm_address_verification_request = {"txHash":"0x1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef"}; // \OpenAPI\Client\Model\ConfirmAddressVerificationRequest

try {
    $result = $apiInstance->confirmAddressVerification($project_id, $currency, $confirm_address_verification_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->confirmAddressVerification: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **currency** | **string**|  | |
| **confirm_address_verification_request** | [**\OpenAPI\Client\Model\ConfirmAddressVerificationRequest**](../Model/ConfirmAddressVerificationRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ConfirmAddressVerification200Response**](../Model/ConfirmAddressVerification200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createOrUpdateFeeSettings()`

```php
createOrUpdateFeeSettings($project_id, $create_or_update_fee_settings_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

~~Create or update project fee settings~~ (deprecated)

Create or update fee settings for a project. Configure transaction fees, payout addresses, and thresholds for supported cryptocurrencies. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_or_update_fee_settings_request = {"currency":"BTC","enabled":true,"feeAmount":5.0E-5,"payoutAddress":"bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh","payoutThreshold":0.001}; // \OpenAPI\Client\Model\CreateOrUpdateFeeSettingsRequest

try {
    $result = $apiInstance->createOrUpdateFeeSettings($project_id, $create_or_update_fee_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->createOrUpdateFeeSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **create_or_update_fee_settings_request** | [**\OpenAPI\Client\Model\CreateOrUpdateFeeSettingsRequest**](../Model/CreateOrUpdateFeeSettingsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCurrencyFeeBalance()`

```php
getCurrencyFeeBalance($project_id, $currency): \OpenAPI\Client\Model\GetCurrencyFeeBalance200Response
```

~~Get currency fee balance~~ (deprecated)

Get fee balance for a specific cryptocurrency in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$currency = 'currency_example'; // string

try {
    $result = $apiInstance->getCurrencyFeeBalance($project_id, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->getCurrencyFeeBalance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **currency** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetCurrencyFeeBalance200Response**](../Model/GetCurrencyFeeBalance200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFeeBalances()`

```php
getFeeBalances($project_id): \OpenAPI\Client\Model\GetFeeBalances200Response
```

~~Get all fee balances~~ (deprecated)

Get fee balances for all currencies in a project, including collected amounts, thresholds, and payout status. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getFeeBalances($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->getFeeBalances: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetFeeBalances200Response**](../Model/GetFeeBalances200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFeeSettings()`

```php
getFeeSettings($project_id): \OpenAPI\Client\Model\TestIntegration200Response
```

~~Get project fee settings~~ (deprecated)

Get all fee settings configured for a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getFeeSettings($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->getFeeSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\TestIntegration200Response**](../Model/TestIntegration200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPayoutHistory()`

```php
getPayoutHistory($project_id, $limit, $page, $currency, $status): \OpenAPI\Client\Model\GetPayoutHistory200Response
```

~~Get payout history~~ (deprecated)

Get historical payout records for a project with pagination. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$limit = 20; // int
$page = 1; // int
$currency = 'currency_example'; // string
$status = 'status_example'; // string

try {
    $result = $apiInstance->getPayoutHistory($project_id, $limit, $page, $currency, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->getPayoutHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 20] |
| **page** | **int**|  | [optional] [default to 1] |
| **currency** | **string**|  | [optional] |
| **status** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\GetPayoutHistory200Response**](../Model/GetPayoutHistory200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectFeeDashboard()`

```php
getProjectFeeDashboard($project_id): \OpenAPI\Client\Model\GetProjectFeeDashboard200Response
```

~~Get fee dashboard~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getProjectFeeDashboard($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->getProjectFeeDashboard: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetProjectFeeDashboard200Response**](../Model/GetProjectFeeDashboard200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initiateAddressVerification()`

```php
initiateAddressVerification($project_id, $currency): \OpenAPI\Client\Model\InitiateAddressVerification200Response
```

~~Initiate address verification~~ (deprecated)

Initiate verification process for a payout address. Requires sending a small test transaction to verify ownership. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$currency = 'currency_example'; // string

try {
    $result = $apiInstance->initiateAddressVerification($project_id, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->initiateAddressVerification: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **currency** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\InitiateAddressVerification200Response**](../Model/InitiateAddressVerification200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestManualPayout()`

```php
requestManualPayout($project_id, $request_manual_payout_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

~~Request manual payout~~ (deprecated)

Request a manual payout for collected fees. Requires sufficient balance above the threshold. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$request_manual_payout_request = {"currency":"BTC"}; // \OpenAPI\Client\Model\RequestManualPayoutRequest

try {
    $result = $apiInstance->requestManualPayout($project_id, $request_manual_payout_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->requestManualPayout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **request_manual_payout_request** | [**\OpenAPI\Client\Model\RequestManualPayoutRequest**](../Model/RequestManualPayoutRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCurrencyFeeSettings()`

```php
updateCurrencyFeeSettings($project_id, $currency, $update_currency_fee_settings_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

~~Update currency fee settings~~ (deprecated)

Update fee settings for a specific cryptocurrency in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectFeesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$currency = 'currency_example'; // string
$update_currency_fee_settings_request = {"enabled":true,"feeAmount":0.05,"payoutAddress":"bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh","payoutThreshold":0.1}; // \OpenAPI\Client\Model\UpdateCurrencyFeeSettingsRequest

try {
    $result = $apiInstance->updateCurrencyFeeSettings($project_id, $currency, $update_currency_fee_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectFeesApi->updateCurrencyFeeSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **currency** | **string**|  | |
| **update_currency_fee_settings_request** | [**\OpenAPI\Client\Model\UpdateCurrencyFeeSettingsRequest**](../Model/UpdateCurrencyFeeSettingsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
