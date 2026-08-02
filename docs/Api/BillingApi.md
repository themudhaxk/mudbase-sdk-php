# OpenAPI\Client\BillingApi

Billing and subscription management. **Fiat only** on the live API: platform subscriptions + org payment processing (7% + $0.50 split). No crypto payment fields in billing responses. **Customer subscription payment flow (project-level plans):** 1. GET /api/billing/public/projects/{projectId}/plans — list plans (no auth). Response: { plans: [...] }. 2. POST /api/billing/public/projects/{projectId}/checkout — create checkout (no auth). Body: planId, billingCycle, customerInfo (email, name?), successUrl?, cancelUrl?. Response: { success, data: { checkoutUrl, authorizationUrl, accessCode?, reference, amount, currency } }. 3. After user pays, POST /api/billing/public/projects/{projectId}/verify-payment?reference&#x3D;{reference} — verify and create subscription (reference is mudbase_...). Response: { success, message, data: { subscription } }. **Org-level BaaS plan payment (Starter, Growth, Scale — paymentService.js PLANS):** 1. GET /api/billing/plans — list tiers (no auth). Response: { plans: [{ id, name, price, priceYearly, limits, overages }, ...] }. 2. POST /api/billing/org/checkout — create a payment link (auth required). Body: planName (starter|growth|scale), billingCycle (monthly|yearly), redirectUrl?. Response: { success, data: { link, txRef, amount, amountCents } }. 3. After user pays, POST /api/billing/org/verify-payment?tx_ref&#x3D;{txRef} — verify and update org plan. Response: { success, message, data: { plan, billingCycle, orgId } }. GET /api/billing/estimate returns current-month overage estimate and forecast; GET /api/usage/overage returns overage line items for the current period.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelSubscription()**](BillingApi.md#cancelSubscription) | **POST** /api/billing/subscriptions/{subscriptionId}/cancel | Cancel subscription |
| [**checkFeatureAccess()**](BillingApi.md#checkFeatureAccess) | **GET** /api/billing/public/projects/{projectId}/feature-access | Check feature access (public) |
| [**checkSubscription()**](BillingApi.md#checkSubscription) | **GET** /api/billing/public/projects/{projectId}/subscription | Check subscription status (public) |
| [**createCheckoutSession()**](BillingApi.md#createCheckoutSession) | **POST** /api/billing/public/projects/{projectId}/checkout | Create checkout session (fiat) |
| [**createPlan()**](BillingApi.md#createPlan) | **POST** /api/billing/projects/{projectId}/plans | Create billing plan |
| [**deletePlan()**](BillingApi.md#deletePlan) | **DELETE** /api/billing/projects/{projectId}/plans/{planId} | Delete billing plan |
| [**downloadInvoice()**](BillingApi.md#downloadInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId}/download | Download invoice PDF |
| [**enablePaymentProcessing()**](BillingApi.md#enablePaymentProcessing) | **POST** /api/orgs/{orgId}/payment-processing/enable | Enable payment processing for organization |
| [**exportInvoice()**](BillingApi.md#exportInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId}/export | Export invoice (e.g. PDF URL or file) |
| [**getBillingEstimate()**](BillingApi.md#getBillingEstimate) | **GET** /api/billing/estimate | Get billing estimate and forecast |
| [**getCheckoutPayment()**](BillingApi.md#getCheckoutPayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details (not used for fiat billing) |
| [**getDashboard()**](BillingApi.md#getDashboard) | **GET** /api/billing/projects/{projectId}/dashboard | Get billing dashboard data |
| [**getFeeBreakdown()**](BillingApi.md#getFeeBreakdown) | **GET** /api/orgs/{orgId}/payment-processing/fee-breakdown | Get fee breakdown for a given amount |
| [**getInvoice()**](BillingApi.md#getInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId} | Get single invoice |
| [**getInvoices()**](BillingApi.md#getInvoices) | **GET** /api/billing/projects/{projectId}/invoices | List project invoices |
| [**getPaymentRecords()**](BillingApi.md#getPaymentRecords) | **GET** /api/orgs/{orgId}/payment-processing/records | List fiat payment records for organization |
| [**getPlans()**](BillingApi.md#getPlans) | **GET** /api/billing/projects/{projectId}/plans | Get billing plans |
| [**getPublicPlans()**](BillingApi.md#getPublicPlans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**getSubscriptionTierById()**](BillingApi.md#getSubscriptionTierById) | **GET** /api/billing/plans/{planId} | Get one subscription tier by id |
| [**getSubscriptionTiers()**](BillingApi.md#getSubscriptionTiers) | **GET** /api/billing/plans | Get subscription tiers (org-level BaaS plans) |
| [**getSubscriptions()**](BillingApi.md#getSubscriptions) | **GET** /api/billing/projects/{projectId}/subscriptions | Get subscriptions |
| [**handleFlutterwaveWebhook()**](BillingApi.md#handleFlutterwaveWebhook) | **POST** /api/billing/webhooks/flutterwave | Payment gateway webhook |
| [**initializeOrgPlanCheckout()**](BillingApi.md#initializeOrgPlanCheckout) | **POST** /api/billing/org/checkout | Initialize org-level BaaS plan payment (Starter, Growth, Scale) |
| [**initializePayment()**](BillingApi.md#initializePayment) | **POST** /api/orgs/{orgId}/payment-processing/initialize-payment | Initialize fiat payment with split (org subaccount + platform fee) |
| [**initializePaymentForProject()**](BillingApi.md#initializePaymentForProject) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (project-scoped) |
| [**recordUsage()**](BillingApi.md#recordUsage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**updatePlan()**](BillingApi.md#updatePlan) | **PATCH** /api/billing/projects/{projectId}/plans/{planId} | Update billing plan |
| [**verifyOrgPlanPayment()**](BillingApi.md#verifyOrgPlanPayment) | **POST** /api/billing/org/verify-payment | Verify org-level plan payment |
| [**verifyPayment()**](BillingApi.md#verifyPayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |


## `cancelSubscription()`

```php
cancelSubscription($subscription_id, $cancel_subscription_request): \OpenAPI\Client\Model\DeleteRole200Response
```

Cancel subscription

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subscription_id = 'subscription_id_example'; // string
$cancel_subscription_request = {"cancelImmediately":false}; // \OpenAPI\Client\Model\CancelSubscriptionRequest

try {
    $result = $apiInstance->cancelSubscription($subscription_id, $cancel_subscription_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->cancelSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **subscription_id** | **string**|  | |
| **cancel_subscription_request** | [**\OpenAPI\Client\Model\CancelSubscriptionRequest**](../Model/CancelSubscriptionRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\DeleteRole200Response**](../Model/DeleteRole200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `checkFeatureAccess()`

```php
checkFeatureAccess($project_id, $email, $feature): \OpenAPI\Client\Model\CheckFeatureAccess200Response
```

Check feature access (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$email = 'email_example'; // string | Customer email
$feature = 'feature_example'; // string | Feature slug to check access for

try {
    $result = $apiInstance->checkFeatureAccess($project_id, $email, $feature);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->checkFeatureAccess: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **email** | **string**| Customer email | |
| **feature** | **string**| Feature slug to check access for | |

### Return type

[**\OpenAPI\Client\Model\CheckFeatureAccess200Response**](../Model/CheckFeatureAccess200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `checkSubscription()`

```php
checkSubscription($project_id, $email): \OpenAPI\Client\Model\CheckSubscription200Response
```

Check subscription status (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$email = 'email_example'; // string | Customer email to check subscription for

try {
    $result = $apiInstance->checkSubscription($project_id, $email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->checkSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **email** | **string**| Customer email to check subscription for | |

### Return type

[**\OpenAPI\Client\Model\CheckSubscription200Response**](../Model/CheckSubscription200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createCheckoutSession()`

```php
createCheckoutSession($project_id, $create_checkout_session_request): \OpenAPI\Client\Model\CreateCheckoutSession200Response
```

Create checkout session (fiat)

**Customer subscription flow — Step 2.** Creates a fiat checkout session. Request body must include planId (from GET public plans), billingCycle (monthly|yearly), and customerInfo.email. Redirect the user to **checkoutUrl** (same URL as authorizationUrl). After payment, call verify-payment with **reference** (mudbase_...). Response includes only fiat fields (no paymentAddress, paymentOptions, network, asset, or pmt_ references).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID
$create_checkout_session_request = {"planId":"65a1b2c3d4e5f6789012345d","billingCycle":"monthly","customerInfo":{"email":"customer@example.com","name":"John Doe"},"successUrl":"https://app.example.com/success","cancelUrl":"https://app.example.com/cancel"}; // \OpenAPI\Client\Model\CreateCheckoutSessionRequest

try {
    $result = $apiInstance->createCheckoutSession($project_id, $create_checkout_session_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->createCheckoutSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID | |
| **create_checkout_session_request** | [**\OpenAPI\Client\Model\CreateCheckoutSessionRequest**](../Model/CreateCheckoutSessionRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreateCheckoutSession200Response**](../Model/CreateCheckoutSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createPlan()`

```php
createPlan($project_id, $create_plan_request): \OpenAPI\Client\Model\CreatePlan201Response
```

Create billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_plan_request = {"name":"Pro Plan","description":"Professional plan with advanced features","price":29.99,"currency":"USD","interval":"month","features":["Unlimited API calls","Priority support","Advanced analytics"]}; // \OpenAPI\Client\Model\CreatePlanRequest

try {
    $result = $apiInstance->createPlan($project_id, $create_plan_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->createPlan: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **create_plan_request** | [**\OpenAPI\Client\Model\CreatePlanRequest**](../Model/CreatePlanRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreatePlan201Response**](../Model/CreatePlan201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deletePlan()`

```php
deletePlan($project_id, $plan_id): \OpenAPI\Client\Model\MessageResponse
```

Delete billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$plan_id = 'plan_id_example'; // string

try {
    $result = $apiInstance->deletePlan($project_id, $plan_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->deletePlan: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **plan_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `downloadInvoice()`

```php
downloadInvoice($project_id, $invoice_id): \SplFileObject
```

Download invoice PDF

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$invoice_id = 'invoice_id_example'; // string

try {
    $result = $apiInstance->downloadInvoice($project_id, $invoice_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->downloadInvoice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **invoice_id** | **string**|  | |

### Return type

**\SplFileObject**

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/pdf`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `enablePaymentProcessing()`

```php
enablePaymentProcessing($org_id, $enable_payment_processing_request): \OpenAPI\Client\Model\EnablePaymentProcessing200Response
```

Enable payment processing for organization

Creates a payment-collection subaccount for the org with the provided bank details. Use USD-capable bank (e.g. country US) for USD settlement. BVN only required when country is NG. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$enable_payment_processing_request = {"accountBank":"044","accountNumber":"0123456789","country":"US","businessName":"Acme Inc","businessMobile":"+1234567890"}; // \OpenAPI\Client\Model\EnablePaymentProcessingRequest

try {
    $result = $apiInstance->enablePaymentProcessing($org_id, $enable_payment_processing_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->enablePaymentProcessing: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **enable_payment_processing_request** | [**\OpenAPI\Client\Model\EnablePaymentProcessingRequest**](../Model/EnablePaymentProcessingRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\EnablePaymentProcessing200Response**](../Model/EnablePaymentProcessing200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportInvoice()`

```php
exportInvoice($project_id, $invoice_id): \OpenAPI\Client\Model\DownloadInvoice200Response
```

Export invoice (e.g. PDF URL or file)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$invoice_id = 'invoice_id_example'; // string

try {
    $result = $apiInstance->exportInvoice($project_id, $invoice_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->exportInvoice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **invoice_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\DownloadInvoice200Response**](../Model/DownloadInvoice200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getBillingEstimate()`

```php
getBillingEstimate(): \OpenAPI\Client\Model\GetBillingEstimate200Response
```

Get billing estimate and forecast

Returns current-month overage estimate and an optional end-of-month forecast for the authenticated organization. Includes spend limit settings (soft/hard) and whether usage is currently blocked. Requires org-level JWT.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getBillingEstimate();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getBillingEstimate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetBillingEstimate200Response**](../Model/GetBillingEstimate200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCheckoutPayment()`

```php
getCheckoutPayment($project_id, $payment_id)
```

Get checkout payment details (not used for fiat billing)

**Fiat-only billing:** checkout is completed on the payment gateway's hosted page; there is no server-side payment intent to poll. The live API returns **404** for this route. Reserved for compatibility; do not rely on a success body for project billing.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$payment_id = 'payment_id_example'; // string | Opaque id from checkout (fiat billing does not expose pollable payment state here)

try {
    $apiInstance->getCheckoutPayment($project_id, $payment_id);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getCheckoutPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **payment_id** | **string**| Opaque id from checkout (fiat billing does not expose pollable payment state here) | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDashboard()`

```php
getDashboard($project_id): \OpenAPI\Client\Model\GetDashboard200Response
```

Get billing dashboard data

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getDashboard($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getDashboard: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetDashboard200Response**](../Model/GetDashboard200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFeeBreakdown()`

```php
getFeeBreakdown($org_id, $amount, $currency): \OpenAPI\Client\Model\GetFeeBreakdown200Response
```

Get fee breakdown for a given amount

Returns orgReceives, platformPercent, platformFixed, processingFee for the given amount (7% + $0.50 platform fee; processing fee absorbed from platform share).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$amount = 3.4; // float
$currency = 'USD'; // string

try {
    $result = $apiInstance->getFeeBreakdown($org_id, $amount, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getFeeBreakdown: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **amount** | **float**|  | |
| **currency** | **string**|  | [optional] [default to &#39;USD&#39;] |

### Return type

[**\OpenAPI\Client\Model\GetFeeBreakdown200Response**](../Model/GetFeeBreakdown200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getInvoice()`

```php
getInvoice($project_id, $invoice_id): \OpenAPI\Client\Model\GetInvoice200Response
```

Get single invoice

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$invoice_id = 'invoice_id_example'; // string

try {
    $result = $apiInstance->getInvoice($project_id, $invoice_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getInvoice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **invoice_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetInvoice200Response**](../Model/GetInvoice200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getInvoices()`

```php
getInvoices($project_id): \OpenAPI\Client\Model\GetInvoices200Response
```

List project invoices

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getInvoices($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getInvoices: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetInvoices200Response**](../Model/GetInvoices200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPaymentRecords()`

```php
getPaymentRecords($org_id, $page, $limit, $status): \OpenAPI\Client\Model\GetPaymentRecords200Response
```

List fiat payment records for organization

Paginated list of FiatPaymentRecord for this org (txRef, amount, orgReceives, status, paidAt).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$page = 1; // int
$limit = 20; // int
$status = 'status_example'; // string

try {
    $result = $apiInstance->getPaymentRecords($org_id, $page, $limit, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPaymentRecords: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **status** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\GetPaymentRecords200Response**](../Model/GetPaymentRecords200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPlans()`

```php
getPlans($project_id): \OpenAPI\Client\Model\GetPlans200Response
```

Get billing plans

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getPlans($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPlans: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetPlans200Response**](../Model/GetPlans200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPublicPlans()`

```php
getPublicPlans($project_id): \OpenAPI\Client\Model\GetPublicPlans200Response
```

Get public plans (no auth required)

**Customer subscription flow — Step 1.** Returns all active plans for the project. Use a plan's _id as planId in the checkout request. No authentication required (for pricing/checkout pages).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getPublicPlans($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPublicPlans: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetPublicPlans200Response**](../Model/GetPublicPlans200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSubscriptionTierById()`

```php
getSubscriptionTierById($plan_id): \OpenAPI\Client\Model\GetSubscriptionTierById200Response
```

Get one subscription tier by id

Returns a single org-level BaaS plan (free, starter, growth, scale, enterprise). Public; no auth required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$plan_id = 'plan_id_example'; // string | Plan id (free, starter, growth, scale, enterprise)

try {
    $result = $apiInstance->getSubscriptionTierById($plan_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getSubscriptionTierById: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **plan_id** | **string**| Plan id (free, starter, growth, scale, enterprise) | |

### Return type

[**\OpenAPI\Client\Model\GetSubscriptionTierById200Response**](../Model/GetSubscriptionTierById200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSubscriptionTiers()`

```php
getSubscriptionTiers(): \OpenAPI\Client\Model\GetSubscriptionTiers200Response
```

Get subscription tiers (org-level BaaS plans)

**Org-level BaaS plan catalog** (source of truth in paymentService.js). Returns Free, Starter ($29), Growth ($69), Scale ($199), Enterprise. Use for pricing page and to get plan ids for POST /api/billing/org/checkout. Public; no auth required. Each plan includes id (free|starter|growth|scale|enterprise), name, description, price (cents), priceYearly (cents, 8% off), currency, limits, overages, enforcement.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getSubscriptionTiers();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getSubscriptionTiers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetSubscriptionTiers200Response**](../Model/GetSubscriptionTiers200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSubscriptions()`

```php
getSubscriptions($project_id): \OpenAPI\Client\Model\GetSubscriptions200Response
```

Get subscriptions

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getSubscriptions($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getSubscriptions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetSubscriptions200Response**](../Model/GetSubscriptions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `handleFlutterwaveWebhook()`

```php
handleFlutterwaveWebhook($handle_flutterwave_webhook_request): \OpenAPI\Client\Model\HandleFlutterwaveWebhook200Response
```

Payment gateway webhook

Receives payment gateway webhook events (charge.completed, payment.successful). No auth; verified by verif-hash header. - Subscription billing: meta without isPaymentProcessing triggers verifyPaymentAndCreateSubscription (mudbase_xxx refs). - Payment processing: meta.isPaymentProcessing === true triggers fiat payment record (mudbase_fiat_xxx refs); org share goes to org subaccount, platform fee to main or configured subaccounts.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$handle_flutterwave_webhook_request = {"event":"charge.completed","data":{"id":123456789,"tx_ref":"mudbase_fiat_org123_project456_1234567890_abc","amount":100,"currency":"USD","status":"successful","customer":{"email":"customer@example.com","name":"John Doe"},"meta":{"orgId":"65a1b2c3d4e5f6789012345a","projectId":"65a1b2c3d4e5f6789012345b","isPaymentProcessing":true}}}; // \OpenAPI\Client\Model\HandleFlutterwaveWebhookRequest

try {
    $result = $apiInstance->handleFlutterwaveWebhook($handle_flutterwave_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->handleFlutterwaveWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **handle_flutterwave_webhook_request** | [**\OpenAPI\Client\Model\HandleFlutterwaveWebhookRequest**](../Model/HandleFlutterwaveWebhookRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\HandleFlutterwaveWebhook200Response**](../Model/HandleFlutterwaveWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initializeOrgPlanCheckout()`

```php
initializeOrgPlanCheckout($initialize_org_plan_checkout_request): \OpenAPI\Client\Model\InitializeOrgPlanCheckout200Response
```

Initialize org-level BaaS plan payment (Starter, Growth, Scale)

**Org plan payment flow — Step 2.** Creates a payment link for the authenticated org to subscribe to a BaaS plan (starter, growth, scale). Enterprise has no price; use contact-sales flow. Redirect the user to the returned link; after payment, call POST /api/billing/org/verify-payment with the tx_ref from the redirect. Requires org-level JWT.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$initialize_org_plan_checkout_request = {"planName":"starter","billingCycle":"monthly"}; // \OpenAPI\Client\Model\InitializeOrgPlanCheckoutRequest

try {
    $result = $apiInstance->initializeOrgPlanCheckout($initialize_org_plan_checkout_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->initializeOrgPlanCheckout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **initialize_org_plan_checkout_request** | [**\OpenAPI\Client\Model\InitializeOrgPlanCheckoutRequest**](../Model/InitializeOrgPlanCheckoutRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\InitializeOrgPlanCheckout200Response**](../Model/InitializeOrgPlanCheckout200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initializePayment()`

```php
initializePayment($org_id, $initialize_payment_request): \OpenAPI\Client\Model\InitializePayment200Response
```

Initialize fiat payment with split (org subaccount + platform fee)

Creates a payment link. Customer pays; org receives (amount - 7% - $0.50) to their subaccount; platform fee (7% + $0.50, minus processing fee) stays on main account or goes to configured platform subaccounts. Requires payment processing enabled for org.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$initialize_payment_request = {"amount":100,"currency":"USD","customer":{"email":"buyer@example.com","name":"Buyer Name"},"metadata":{"title":"Order #123","description":"Payment for order"}}; // \OpenAPI\Client\Model\InitializePaymentRequest

try {
    $result = $apiInstance->initializePayment($org_id, $initialize_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->initializePayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **initialize_payment_request** | [**\OpenAPI\Client\Model\InitializePaymentRequest**](../Model/InitializePaymentRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\InitializePayment200Response**](../Model/InitializePayment200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initializePaymentForProject()`

```php
initializePaymentForProject($project_id, $initialize_payment_for_project_request)
```

Initialize fiat payment (project-scoped)

Same as org-level initialize-payment; projectId from path is used for scope and tx_ref. Resolves project to org and uses org's payment-processing subaccount.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$initialize_payment_for_project_request = {"amount":0.01,"customer":{"email":"email_example"}}; // \OpenAPI\Client\Model\InitializePaymentForProjectRequest

try {
    $apiInstance->initializePaymentForProject($project_id, $initialize_payment_for_project_request);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->initializePaymentForProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **initialize_payment_for_project_request** | [**\OpenAPI\Client\Model\InitializePaymentForProjectRequest**](../Model/InitializePaymentForProjectRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `recordUsage()`

```php
recordUsage($project_id, $record_usage_request): \OpenAPI\Client\Model\MessageResponse
```

Record usage (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$record_usage_request = {"email":"customer@example.com","metric":"api_calls","quantity":150}; // \OpenAPI\Client\Model\RecordUsageRequest

try {
    $result = $apiInstance->recordUsage($project_id, $record_usage_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->recordUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **record_usage_request** | [**\OpenAPI\Client\Model\RecordUsageRequest**](../Model/RecordUsageRequest.md)|  | |

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

## `updatePlan()`

```php
updatePlan($project_id, $plan_id, $update_plan_request): \OpenAPI\Client\Model\CreatePlan201Response
```

Update billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$plan_id = 'plan_id_example'; // string
$update_plan_request = {"name":"Pro Plan Updated","description":"Updated professional plan","price":39.99,"features":["Unlimited API calls","Priority support","Advanced analytics"]}; // \OpenAPI\Client\Model\UpdatePlanRequest

try {
    $result = $apiInstance->updatePlan($project_id, $plan_id, $update_plan_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->updatePlan: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **plan_id** | **string**|  | |
| **update_plan_request** | [**\OpenAPI\Client\Model\UpdatePlanRequest**](../Model/UpdatePlanRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreatePlan201Response**](../Model/CreatePlan201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyOrgPlanPayment()`

```php
verifyOrgPlanPayment($tx_ref, $reference): \OpenAPI\Client\Model\VerifyOrgPlanPayment200Response
```

Verify org-level plan payment

**Org plan payment flow — Step 3.** Call after the user completes payment (redirect or webhook). Pass tx_ref (or reference) from the payment redirect. Updates org plan and billing; idempotent. No auth required (redirect callback can call this).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$tx_ref = 'tx_ref_example'; // string | Payment reference (mudbase_org_...) from checkout redirect
$reference = 'reference_example'; // string | Alias for tx_ref

try {
    $result = $apiInstance->verifyOrgPlanPayment($tx_ref, $reference);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->verifyOrgPlanPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **tx_ref** | **string**| Payment reference (mudbase_org_...) from checkout redirect | [optional] |
| **reference** | **string**| Alias for tx_ref | [optional] |

### Return type

[**\OpenAPI\Client\Model\VerifyOrgPlanPayment200Response**](../Model/VerifyOrgPlanPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyPayment()`

```php
verifyPayment($project_id, $reference): \OpenAPI\Client\Model\VerifyPayment200Response
```

Verify payment and create subscription

**Customer subscription flow — Step 3.** Call after the user completes payment. Pass **reference** as query (?reference=mudbase_...). On success, a subscription is created. No auth required when using the platform gateway (mudbase_ refs). Org-level gateway verification may require JWT. References starting with pmt_ are rejected (crypto billing is not enabled on this API).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$reference = 'reference_example'; // string | Payment transaction reference (mudbase_...)

try {
    $result = $apiInstance->verifyPayment($project_id, $reference);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->verifyPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **reference** | **string**| Payment transaction reference (mudbase_...) | |

### Return type

[**\OpenAPI\Client\Model\VerifyPayment200Response**](../Model/VerifyPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
