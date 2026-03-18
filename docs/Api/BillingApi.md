# OpenAPI\Client\BillingApi

Billing and subscription management. Fiat via Flutterwave only (platform subscriptions + org payment processing with 7% + $0.50 split). Crypto checkout via multi-chain payment processor. Project checkout and subscription endpoints are documented here; org billing and overage are in the dashboard.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**billingCheckFeatureAccess()**](BillingApi.md#billingCheckFeatureAccess) | **GET** /api/billing/public/projects/{projectId}/feature-access | Check feature access (public) |
| [**billingCheckSubscription()**](BillingApi.md#billingCheckSubscription) | **GET** /api/billing/public/projects/{projectId}/subscription | Check subscription status (public) |
| [**billingCreateCheckoutSession()**](BillingApi.md#billingCreateCheckoutSession) | **POST** /api/billing/public/projects/{projectId}/checkout | Create checkout session (Flutterwave or crypto) |
| [**billingGetCheckoutPayment()**](BillingApi.md#billingGetCheckoutPayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details |
| [**billingGetPublicPlans()**](BillingApi.md#billingGetPublicPlans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**billingHandleCryptoWebhook()**](BillingApi.md#billingHandleCryptoWebhook) | **POST** /api/billing/webhooks/crypto | Crypto payment processor webhook |
| [**billingHandleFlutterwaveWebhook()**](BillingApi.md#billingHandleFlutterwaveWebhook) | **POST** /api/billing/webhooks/flutterwave | Flutterwave webhook |
| [**billingInitializePayment()**](BillingApi.md#billingInitializePayment) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (app-scoped) |
| [**billingRecordUsage()**](BillingApi.md#billingRecordUsage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**billingVerifyPayment()**](BillingApi.md#billingVerifyPayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |


## `billingCheckFeatureAccess()`

```php
billingCheckFeatureAccess($project_id, $email, $feature): \OpenAPI\Client\Model\BillingCheckFeatureAccess200Response
```

Check feature access (public)

Check whether a customer has access to a feature (by plan or entitlement). Public; no auth required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$email = 'email_example'; // string | Customer email
$feature = 'feature_example'; // string | Feature slug to check access for

try {
    $result = $apiInstance->billingCheckFeatureAccess($project_id, $email, $feature);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingCheckFeatureAccess: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **email** | **string**| Customer email | |
| **feature** | **string**| Feature slug to check access for | |

### Return type

[**\OpenAPI\Client\Model\BillingCheckFeatureAccess200Response**](../Model/BillingCheckFeatureAccess200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingCheckSubscription()`

```php
billingCheckSubscription($project_id, $email): \OpenAPI\Client\Model\BillingCheckSubscription200Response
```

Check subscription status (public)

Check whether a customer (by email) has an active subscription for the project. Public; no auth required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$email = 'email_example'; // string | Customer email to check subscription for

try {
    $result = $apiInstance->billingCheckSubscription($project_id, $email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingCheckSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **email** | **string**| Customer email to check subscription for | |

### Return type

[**\OpenAPI\Client\Model\BillingCheckSubscription200Response**](../Model/BillingCheckSubscription200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingCreateCheckoutSession()`

```php
billingCreateCheckoutSession($project_id, $billing_create_checkout_session_request): \OpenAPI\Client\Model\BillingCreateCheckoutSession200Response
```

Create checkout session (Flutterwave or crypto)

Creates a checkout session for subscription billing. When Flutterwave is configured (platform), returns authorizationUrl and accessCode for redirect. When using crypto payment processor, returns checkoutUrl, paymentOptions (multi-chain USDC/USDT/BTC Lightning), and reference.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$billing_create_checkout_session_request = {"planId":"65a1b2c3d4e5f6789012345d","billingCycle":"monthly","customerInfo":{"email":"customer@example.com","name":"John Doe"},"successUrl":"https://app.example.com/success","cancelUrl":"https://app.example.com/cancel"}; // \OpenAPI\Client\Model\BillingCreateCheckoutSessionRequest | Plan to subscribe to, billing cycle, customer email/name, and optional success/cancel redirect URLs.

try {
    $result = $apiInstance->billingCreateCheckoutSession($project_id, $billing_create_checkout_session_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingCreateCheckoutSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **billing_create_checkout_session_request** | [**\OpenAPI\Client\Model\BillingCreateCheckoutSessionRequest**](../Model/BillingCreateCheckoutSessionRequest.md)| Plan to subscribe to, billing cycle, customer email/name, and optional success/cancel redirect URLs. | |

### Return type

[**\OpenAPI\Client\Model\BillingCreateCheckoutSession200Response**](../Model/BillingCreateCheckoutSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingGetCheckoutPayment()`

```php
billingGetCheckoutPayment($project_id, $payment_id): \OpenAPI\Client\Model\BillingGetCheckoutPayment200Response
```

Get checkout payment details

Returns payment intent/checkout status (for refresh or deep link). No auth required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$payment_id = 'payment_id_example'; // string | Payment ID or reference from checkout session

try {
    $result = $apiInstance->billingGetCheckoutPayment($project_id, $payment_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingGetCheckoutPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **payment_id** | **string**| Payment ID or reference from checkout session | |

### Return type

[**\OpenAPI\Client\Model\BillingGetCheckoutPayment200Response**](../Model/BillingGetCheckoutPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingGetPublicPlans()`

```php
billingGetPublicPlans($project_id): \OpenAPI\Client\Model\BillingGetPublicPlans200Response
```

Get public plans (no auth required)

Returns subscription plans available for the project. Public; no authentication required. Use for pricing pages and checkout flow.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) to list plans for.

try {
    $result = $apiInstance->billingGetPublicPlans($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingGetPublicPlans: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to list plans for. | |

### Return type

[**\OpenAPI\Client\Model\BillingGetPublicPlans200Response**](../Model/BillingGetPublicPlans200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingHandleCryptoWebhook()`

```php
billingHandleCryptoWebhook($billing_handle_crypto_webhook_request): \OpenAPI\Client\Model\BillingHandleCryptoWebhook200Response
```

Crypto payment processor webhook

Receives crypto payment events (payment.completed, etc.) for platform billing. No auth; verified by provider signature.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$billing_handle_crypto_webhook_request = {"event":"payment.completed","data":{"paymentId":"pmt_abc123xyz789","reference":"pmt_abc123xyz789","amount":29.99,"currency":"USD","network":"polygon","status":"completed","metadata":{"isPlatformBilling":true,"planId":"65a1b2c3d4e5f6789012345d","billingCycle":"monthly","customerEmail":"customer@example.com"}}}; // \OpenAPI\Client\Model\BillingHandleCryptoWebhookRequest | Crypto payment webhook payload (event type and data with paymentId, reference, amount, currency, network, status, metadata).

try {
    $result = $apiInstance->billingHandleCryptoWebhook($billing_handle_crypto_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingHandleCryptoWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **billing_handle_crypto_webhook_request** | [**\OpenAPI\Client\Model\BillingHandleCryptoWebhookRequest**](../Model/BillingHandleCryptoWebhookRequest.md)| Crypto payment webhook payload (event type and data with paymentId, reference, amount, currency, network, status, metadata). | |

### Return type

[**\OpenAPI\Client\Model\BillingHandleCryptoWebhook200Response**](../Model/BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingHandleFlutterwaveWebhook()`

```php
billingHandleFlutterwaveWebhook($billing_handle_flutterwave_webhook_request): \OpenAPI\Client\Model\BillingHandleCryptoWebhook200Response
```

Flutterwave webhook

Receives Flutterwave webhook events (charge.completed, payment.successful). No auth; verified by verif-hash header. - Subscription billing: meta without isPaymentProcessing triggers verifyPaymentAndCreateSubscription (mudbase_xxx refs). - Payment processing: meta.isPaymentProcessing === true triggers fiat payment record (mudbase_fiat_xxx refs); org share goes to org subaccount, platform fee to main or configured subaccounts.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$billing_handle_flutterwave_webhook_request = {"event":"charge.completed","data":{"id":123456789,"tx_ref":"mudbase_fiat_org123_project456_1234567890_abc","amount":100,"currency":"USD","status":"successful","customer":{"email":"customer@example.com","name":"John Doe"},"meta":{"orgId":"65a1b2c3d4e5f6789012345a","projectId":"65a1b2c3d4e5f6789012345b","isPaymentProcessing":true}}}; // \OpenAPI\Client\Model\BillingHandleFlutterwaveWebhookRequest | Flutterwave webhook payload (event and data with id, tx_ref, amount, currency, status, customer, meta for subscription or payment-processing).

try {
    $result = $apiInstance->billingHandleFlutterwaveWebhook($billing_handle_flutterwave_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingHandleFlutterwaveWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **billing_handle_flutterwave_webhook_request** | [**\OpenAPI\Client\Model\BillingHandleFlutterwaveWebhookRequest**](../Model/BillingHandleFlutterwaveWebhookRequest.md)| Flutterwave webhook payload (event and data with id, tx_ref, amount, currency, status, customer, meta for subscription or payment-processing). | |

### Return type

[**\OpenAPI\Client\Model\BillingHandleCryptoWebhook200Response**](../Model/BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingInitializePayment()`

```php
billingInitializePayment($project_id, $billing_initialize_payment_request)
```

Initialize fiat payment (app-scoped)

Same as org-level initialize-payment; projectId from path is used for scope and tx_ref. Resolves project to org and uses org's Flutterwave subaccount.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID for payment scope and tx_ref.
$billing_initialize_payment_request = new \OpenAPI\Client\Model\BillingInitializePaymentRequest(); // \OpenAPI\Client\Model\BillingInitializePaymentRequest | Payment amount, currency, customer (email, name), and optional metadata.

try {
    $apiInstance->billingInitializePayment($project_id, $billing_initialize_payment_request);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingInitializePayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID for payment scope and tx_ref. | |
| **billing_initialize_payment_request** | [**\OpenAPI\Client\Model\BillingInitializePaymentRequest**](../Model/BillingInitializePaymentRequest.md)| Payment amount, currency, customer (email, name), and optional metadata. | |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingRecordUsage()`

```php
billingRecordUsage($project_id, $billing_record_usage_request): \OpenAPI\Client\Model\MessageResponse
```

Record usage (public)

Record metered usage for a customer (e.g. api_calls, storage_mb). Used for usage-based billing. Public endpoint; optionally secured by webhook or API key in production.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$billing_record_usage_request = {"email":"customer@example.com","metric":"api_calls","quantity":150}; // \OpenAPI\Client\Model\BillingRecordUsageRequest | Customer email, metric name (e.g. api_calls, storage_mb), and quantity to record.

try {
    $result = $apiInstance->billingRecordUsage($project_id, $billing_record_usage_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingRecordUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **billing_record_usage_request** | [**\OpenAPI\Client\Model\BillingRecordUsageRequest**](../Model/BillingRecordUsageRequest.md)| Customer email, metric name (e.g. api_calls, storage_mb), and quantity to record. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `billingVerifyPayment()`

```php
billingVerifyPayment($project_id, $reference): \OpenAPI\Client\Model\BillingVerifyPayment200Response
```

Verify payment and create subscription

Verifies payment by reference (Flutterwave mudbase_xxx or crypto pmt_xxx) and creates or updates the subscription. Call after redirect from payment provider; pass reference as query (e.g. ?reference=mudbase_abc123). Idempotent for same reference.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the billing project.
$reference = 'reference_example'; // string | Payment reference (e.g. mudbase_abc123 or pmt_abc123)

try {
    $result = $apiInstance->billingVerifyPayment($project_id, $reference);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->billingVerifyPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the billing project. | |
| **reference** | **string**| Payment reference (e.g. mudbase_abc123 or pmt_abc123) | |

### Return type

[**\OpenAPI\Client\Model\BillingVerifyPayment200Response**](../Model/BillingVerifyPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
