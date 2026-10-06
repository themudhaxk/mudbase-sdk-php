# MudbaseSDK\BillingApi

Billing and subscription management. **Fiat only** on the live API: platform subscriptions + org payment processing. Per-transaction processing fees are computed per payout rail and returned by GET /api/orgs/{orgId}/payment-processing/fee-breakdown. No crypto payment fields in billing responses. **Customer subscription payment flow (project-level plans):** 1. GET /api/billing/public/projects/{projectId}/plans — list plans (no auth). Response: { plans: [...] }. 2. POST /api/billing/public/projects/{projectId}/checkout — create checkout (no auth). Body: planId, billingCycle, customerInfo (email, name?), successUrl?, cancelUrl?. Response: { success, data: { checkoutUrl, authorizationUrl, accessCode?, reference, amount, currency } }. 3. After user pays, POST /api/billing/public/projects/{projectId}/verify-payment?reference&#x3D;{reference} — verify and create subscription (reference is mudbase_...). Response: { success, message, data: { subscription } }. **Org-level BaaS plan payment (Starter, Growth, Scale — paymentService.js PLANS):** 1. GET /api/billing/plans — list tiers (no auth). Response: { plans: [{ id, name, price, priceYearly, limits, overages }, ...] }. 2. POST /api/billing/org/checkout — create a payment link (auth required). Body: planName (basic|starter|growth|scale), billingCycle (monthly|yearly), redirectUrl?. Response: { success, data: { link, txRef, amount, amountCents } }. 3. After user pays, POST /api/billing/org/verify-payment?tx_ref&#x3D;{txRef} — verify and update org plan. Response: { success, message, data: { plan, billingCycle, orgId } }. GET /api/billing/estimate returns current-month overage estimate and forecast; GET /api/usage/overage returns overage line items for the current period.

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
| [**enablePaymentProcessing()**](BillingApi.md#enablePaymentProcessing) | **POST** /api/orgs/{orgId}/payment-processing/enable | Submit payout onboarding for organization |
| [**exportInvoice()**](BillingApi.md#exportInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId}/export | Export invoice (e.g. PDF URL or file) |
| [**getBillingEstimate()**](BillingApi.md#getBillingEstimate) | **GET** /api/billing/estimate | Get billing estimate and forecast |
| [**getCheckoutPayment()**](BillingApi.md#getCheckoutPayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details (not used for fiat billing) |
| [**getDashboard()**](BillingApi.md#getDashboard) | **GET** /api/billing/projects/{projectId}/dashboard | Get billing dashboard data |
| [**getFeeBreakdown()**](BillingApi.md#getFeeBreakdown) | **GET** /api/orgs/{orgId}/payment-processing/fee-breakdown | Preview the fee for a given amount |
| [**getInvoice()**](BillingApi.md#getInvoice) | **GET** /api/billing/projects/{projectId}/invoices/{invoiceId} | Get single invoice |
| [**getInvoices()**](BillingApi.md#getInvoices) | **GET** /api/billing/projects/{projectId}/invoices | List project invoices |
| [**getPaymentProcessingStatus()**](BillingApi.md#getPaymentProcessingStatus) | **GET** /api/orgs/{orgId}/payment-processing/status | Get payout-onboarding status for organization |
| [**getPaymentRecords()**](BillingApi.md#getPaymentRecords) | **GET** /api/orgs/{orgId}/payment-processing/records | List fiat payment records for organization |
| [**getPayoutBanks()**](BillingApi.md#getPayoutBanks) | **GET** /api/orgs/{orgId}/payment-processing/banks | List settlement banks for a payout country |
| [**getPayoutCountries()**](BillingApi.md#getPayoutCountries) | **GET** /api/orgs/{orgId}/payment-processing/countries | List supported payout countries |
| [**getPlans()**](BillingApi.md#getPlans) | **GET** /api/billing/projects/{projectId}/plans | Get billing plans |
| [**getPublicPlans()**](BillingApi.md#getPublicPlans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**getSubscriptionTierById()**](BillingApi.md#getSubscriptionTierById) | **GET** /api/billing/plans/{planId} | Get one subscription tier by id |
| [**getSubscriptionTiers()**](BillingApi.md#getSubscriptionTiers) | **GET** /api/billing/plans | Get subscription tiers (org-level BaaS plans) |
| [**getSubscriptions()**](BillingApi.md#getSubscriptions) | **GET** /api/billing/projects/{projectId}/subscriptions | Get subscriptions |
| [**initializeOrgPlanCheckout()**](BillingApi.md#initializeOrgPlanCheckout) | **POST** /api/billing/org/checkout | Initialize org-level BaaS plan payment (Basic, Starter, Growth, Scale) |
| [**initializePayment()**](BillingApi.md#initializePayment) | **POST** /api/orgs/{orgId}/payment-processing/initialize-payment | Initialize fiat payment |
| [**initializePaymentForProject()**](BillingApi.md#initializePaymentForProject) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (project-scoped) |
| [**recordUsage()**](BillingApi.md#recordUsage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**updatePlan()**](BillingApi.md#updatePlan) | **PATCH** /api/billing/projects/{projectId}/plans/{planId} | Update billing plan |
| [**verifyOrgPlanPayment()**](BillingApi.md#verifyOrgPlanPayment) | **POST** /api/billing/org/verify-payment | Verify org-level plan payment |
| [**verifyPayment()**](BillingApi.md#verifyPayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |


## `cancelSubscription()`

```php
cancelSubscription($subscription_id, $cancel_subscription_request): \MudbaseSDK\Model\DeleteRole200Response
```

Cancel subscription

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subscription_id = 'subscription_id_example'; // string
$cancel_subscription_request = {"cancelImmediately":false}; // \MudbaseSDK\Model\CancelSubscriptionRequest

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
| **cancel_subscription_request** | [**\MudbaseSDK\Model\CancelSubscriptionRequest**](../Model/CancelSubscriptionRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\DeleteRole200Response**](../Model/DeleteRole200Response.md)

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
checkFeatureAccess($project_id, $email, $feature): \MudbaseSDK\Model\CheckFeatureAccess200Response
```

Check feature access (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\CheckFeatureAccess200Response**](../Model/CheckFeatureAccess200Response.md)

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
checkSubscription($project_id, $email): \MudbaseSDK\Model\CheckSubscription200Response
```

Check subscription status (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\CheckSubscription200Response**](../Model/CheckSubscription200Response.md)

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
createCheckoutSession($project_id, $create_checkout_session_request): \MudbaseSDK\Model\CreateCheckoutSession200Response
```

Create checkout session (fiat)

**Customer subscription flow — Step 2.** Creates a fiat checkout session. Request body must include planId (from GET public plans), billingCycle (monthly|yearly), and customerInfo.email. Redirect the user to **checkoutUrl** (same URL as authorizationUrl). After payment, call verify-payment with **reference** (mudbase_...). Response includes only fiat fields (no paymentAddress, paymentOptions, network, asset, or pmt_ references).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID
$create_checkout_session_request = {"planId":"65a1b2c3d4e5f6789012345d","billingCycle":"monthly","customerInfo":{"email":"customer@example.com","name":"John Doe"},"successUrl":"https://app.example.com/success","cancelUrl":"https://app.example.com/cancel"}; // \MudbaseSDK\Model\CreateCheckoutSessionRequest

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
| **create_checkout_session_request** | [**\MudbaseSDK\Model\CreateCheckoutSessionRequest**](../Model/CreateCheckoutSessionRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\CreateCheckoutSession200Response**](../Model/CreateCheckoutSession200Response.md)

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
createPlan($project_id, $create_plan_request): \MudbaseSDK\Model\CreatePlan201Response
```

Create billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_plan_request = {"name":"Pro Plan","description":"Professional plan with advanced features","price":29.99,"currency":"USD","interval":"month","features":["Unlimited API calls","Priority support","Advanced analytics"]}; // \MudbaseSDK\Model\CreatePlanRequest

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
| **create_plan_request** | [**\MudbaseSDK\Model\CreatePlanRequest**](../Model/CreatePlanRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\CreatePlan201Response**](../Model/CreatePlan201Response.md)

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
deletePlan($project_id, $plan_id): \MudbaseSDK\Model\MessageResponse
```

Delete billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

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
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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
enablePaymentProcessing($org_id, $enable_payment_processing_request): \MudbaseSDK\Model\EnablePaymentProcessing200Response
```

Submit payout onboarding for organization

Validates and stores the org's payout account details, then queues the org for platform-admin review. This does not activate payments by itself; initialize-payment only starts succeeding once the org is approved. The required fields depend on the chosen country: call GET /payment-processing/countries first and collect exactly the fields that country's schema returns (bank code + account number for most African markets, plus a BVN for Nigeria, or routing number/sort code + account type + account holder name for the US/UK). Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$enable_payment_processing_request = {"country":"NG","businessName":"Acme Inc","accountBank":"044","accountNumber":"0123456789","bvn":"12345678901"}; // \MudbaseSDK\Model\EnablePaymentProcessingRequest

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
| **enable_payment_processing_request** | [**\MudbaseSDK\Model\EnablePaymentProcessingRequest**](../Model/EnablePaymentProcessingRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\EnablePaymentProcessing200Response**](../Model/EnablePaymentProcessing200Response.md)

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
exportInvoice($project_id, $invoice_id): \MudbaseSDK\Model\DownloadInvoice200Response
```

Export invoice (e.g. PDF URL or file)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\DownloadInvoice200Response**](../Model/DownloadInvoice200Response.md)

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
getBillingEstimate(): \MudbaseSDK\Model\GetBillingEstimate200Response
```

Get billing estimate and forecast

Returns current-month overage estimate and an optional end-of-month forecast for the authenticated organization. Includes spend limit settings (soft/hard) and whether usage is currently blocked. Requires org-level JWT.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetBillingEstimate200Response**](../Model/GetBillingEstimate200Response.md)

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



$apiInstance = new MudbaseSDK\Api\BillingApi(
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
getDashboard($project_id): \MudbaseSDK\Model\GetDashboard200Response
```

Get billing dashboard data

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetDashboard200Response**](../Model/GetDashboard200Response.md)

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
getFeeBreakdown($org_id, $amount, $currency, $country, $method, $international): \MudbaseSDK\Model\GetFeeBreakdown200Response
```

Preview the fee for a given amount

Returns the single all-in Mudbase fee, its effective rate, and what the org would net for the given amount, without creating a payment. Pass country/method/international to price a specific rail; omitting them uses a generic local-rail estimate. Never returns the underlying rail's own cost or any internal margin split.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$amount = 3.4; // float
$currency = 'USD'; // string
$country = 'country_example'; // string | ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries.
$method = 'card'; // string
$international = false; // bool | Set true for a cross-border/international card, Apple Pay, or Google Pay.

try {
    $result = $apiInstance->getFeeBreakdown($org_id, $amount, $currency, $country, $method, $international);
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
| **country** | **string**| ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries. | [optional] |
| **method** | **string**|  | [optional] [default to &#39;card&#39;] |
| **international** | **bool**| Set true for a cross-border/international card, Apple Pay, or Google Pay. | [optional] [default to false] |

### Return type

[**\MudbaseSDK\Model\GetFeeBreakdown200Response**](../Model/GetFeeBreakdown200Response.md)

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
getInvoice($project_id, $invoice_id): \MudbaseSDK\Model\GetInvoice200Response
```

Get single invoice

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetInvoice200Response**](../Model/GetInvoice200Response.md)

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
getInvoices($project_id): \MudbaseSDK\Model\GetInvoices200Response
```

List project invoices

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetInvoices200Response**](../Model/GetInvoices200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPaymentProcessingStatus()`

```php
getPaymentProcessingStatus($org_id): \MudbaseSDK\Model\GetPaymentProcessingStatus200Response
```

Get payout-onboarding status for organization

Returns the current onboarding/approval state for the org's payout account. Poll this after calling enable, or before calling initialize-payment, to confirm the org is actually approved rather than assuming a 200 from enable means payments are live. Never returns the raw payout-account id, only whether one exists.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string

try {
    $result = $apiInstance->getPaymentProcessingStatus($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPaymentProcessingStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetPaymentProcessingStatus200Response**](../Model/GetPaymentProcessingStatus200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPaymentRecords()`

```php
getPaymentRecords($org_id, $page, $limit, $status): \MudbaseSDK\Model\GetPaymentRecords200Response
```

List fiat payment records for organization

Paginated list of FiatPaymentRecord for this org (txRef, amount, orgReceives, status, paidAt).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetPaymentRecords200Response**](../Model/GetPaymentRecords200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPayoutBanks()`

```php
getPayoutBanks($org_id, $country): \MudbaseSDK\Model\GetPayoutBanks200Response
```

List settlement banks for a payout country

Read-only lookup of the settlement-bank list for a country, only meaningful when that country's entry from GET /payment-processing/countries has banksListSupported: true. For a country where it is false, this returns an empty list and your onboarding form should fall back to the free-text bank/code field the countries response already describes for that country, rather than calling this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$country = 'country_example'; // string | ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries.

try {
    $result = $apiInstance->getPayoutBanks($org_id, $country);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPayoutBanks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **country** | **string**| ISO-3166 alpha-2 payout country code, one of the codes from GET /payment-processing/countries. | |

### Return type

[**\MudbaseSDK\Model\GetPayoutBanks200Response**](../Model/GetPayoutBanks200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPayoutCountries()`

```php
getPayoutCountries($org_id): \MudbaseSDK\Model\GetPayoutCountries200Response
```

List supported payout countries

Returns the full supported payout-country set and each country's payout-account field schema. Drives a dynamic onboarding form: which fields to collect (bank code/routing number/sort code/IBAN, whether a BVN is required, whether a bank list or mobile-money network applies) comes straight from this response, so build your onboarding UI to render from it rather than hardcoding a country list.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string

try {
    $result = $apiInstance->getPayoutCountries($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getPayoutCountries: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetPayoutCountries200Response**](../Model/GetPayoutCountries200Response.md)

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
getPlans($project_id): \MudbaseSDK\Model\GetPlans200Response
```

Get billing plans

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetPlans200Response**](../Model/GetPlans200Response.md)

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
getPublicPlans($project_id): \MudbaseSDK\Model\GetPublicPlans200Response
```

Get public plans (no auth required)

**Customer subscription flow — Step 1.** Returns all active plans for the project. Use a plan's _id as planId in the checkout request. No authentication required (for pricing/checkout pages).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetPublicPlans200Response**](../Model/GetPublicPlans200Response.md)

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
getSubscriptionTierById($plan_id): \MudbaseSDK\Model\GetSubscriptionTierById200Response
```

Get one subscription tier by id

Returns a single org-level BaaS plan (free, basic, starter, growth, scale, enterprise). Public; no auth required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$plan_id = 'plan_id_example'; // string | Plan id (free, basic, starter, growth, scale, enterprise)

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
| **plan_id** | **string**| Plan id (free, basic, starter, growth, scale, enterprise) | |

### Return type

[**\MudbaseSDK\Model\GetSubscriptionTierById200Response**](../Model/GetSubscriptionTierById200Response.md)

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
getSubscriptionTiers(): \MudbaseSDK\Model\GetSubscriptionTiers200Response
```

Get subscription tiers (org-level BaaS plans)

**Org-level BaaS plan catalog** (source of truth in paymentService.js). Returns Free, Basic ($12), Starter ($29), Growth ($69), Scale ($199), Enterprise. Use for pricing page and to get plan ids for POST /api/billing/org/checkout. Public; no auth required. Each plan includes id (free|basic|starter|growth|scale|enterprise), name, description, price (cents), priceYearly (cents, 2 months free), currency, limits, overages, enforcement.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetSubscriptionTiers200Response**](../Model/GetSubscriptionTiers200Response.md)

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
getSubscriptions($project_id): \MudbaseSDK\Model\GetSubscriptions200Response
```

Get subscriptions

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\GetSubscriptions200Response**](../Model/GetSubscriptions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initializeOrgPlanCheckout()`

```php
initializeOrgPlanCheckout($initialize_org_plan_checkout_request): \MudbaseSDK\Model\InitializeOrgPlanCheckout200Response
```

Initialize org-level BaaS plan payment (Basic, Starter, Growth, Scale)

**Org plan payment flow — Step 2.** Creates a payment link for the authenticated org to subscribe to a BaaS plan (basic, starter, growth, scale). Enterprise has no price; use contact-sales flow. Redirect the user to the returned link; after payment, call POST /api/billing/org/verify-payment with the tx_ref from the redirect. Requires org-level JWT.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$initialize_org_plan_checkout_request = {"planName":"starter","billingCycle":"monthly"}; // \MudbaseSDK\Model\InitializeOrgPlanCheckoutRequest

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
| **initialize_org_plan_checkout_request** | [**\MudbaseSDK\Model\InitializeOrgPlanCheckoutRequest**](../Model/InitializeOrgPlanCheckoutRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\InitializeOrgPlanCheckout200Response**](../Model/InitializeOrgPlanCheckout200Response.md)

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
initializePayment($org_id, $initialize_payment_request): \MudbaseSDK\Model\InitializePayment200Response
```

Initialize fiat payment

Creates a payment link. The customer pays; Mudbase charges a single all-in, cost-plus fee (see GET /payment-processing/fee-breakdown for the exact rate for a given country/method) and the org receives the remainder. Requires payment processing enabled and approved for the org.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$initialize_payment_request = {"amount":100,"currency":"USD","customer":{"email":"buyer@example.com","name":"Buyer Name"},"metadata":{"title":"Order #123","description":"Payment for order"}}; // \MudbaseSDK\Model\InitializePaymentRequest

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
| **initialize_payment_request** | [**\MudbaseSDK\Model\InitializePaymentRequest**](../Model/InitializePaymentRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\InitializePayment200Response**](../Model/InitializePayment200Response.md)

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
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$initialize_payment_for_project_request = {"amount":0.01,"customer":{"email":"email_example"}}; // \MudbaseSDK\Model\InitializePaymentForProjectRequest

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
| **initialize_payment_for_project_request** | [**\MudbaseSDK\Model\InitializePaymentForProjectRequest**](../Model/InitializePaymentForProjectRequest.md)|  | |

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
recordUsage($project_id, $record_usage_request): \MudbaseSDK\Model\MessageResponse
```

Record usage (public)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$record_usage_request = {"email":"customer@example.com","metric":"api_calls","quantity":150}; // \MudbaseSDK\Model\RecordUsageRequest

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
| **record_usage_request** | [**\MudbaseSDK\Model\RecordUsageRequest**](../Model/RecordUsageRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

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
updatePlan($project_id, $plan_id, $update_plan_request): \MudbaseSDK\Model\CreatePlan201Response
```

Update billing plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$plan_id = 'plan_id_example'; // string
$update_plan_request = {"name":"Pro Plan Updated","description":"Updated professional plan","price":39.99,"features":["Unlimited API calls","Priority support","Advanced analytics"]}; // \MudbaseSDK\Model\UpdatePlanRequest

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
| **update_plan_request** | [**\MudbaseSDK\Model\UpdatePlanRequest**](../Model/UpdatePlanRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\CreatePlan201Response**](../Model/CreatePlan201Response.md)

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
verifyOrgPlanPayment($tx_ref, $reference): \MudbaseSDK\Model\VerifyOrgPlanPayment200Response
```

Verify org-level plan payment

**Org plan payment flow — Step 3.** Call after the user completes payment (redirect or webhook). Pass tx_ref (or reference) from the payment redirect. Updates org plan and billing; idempotent. No auth required (redirect callback can call this).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\VerifyOrgPlanPayment200Response**](../Model/VerifyOrgPlanPayment200Response.md)

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
verifyPayment($project_id, $reference): \MudbaseSDK\Model\VerifyPayment200Response
```

Verify payment and create subscription

**Customer subscription flow — Step 3.** Call after the user completes payment. Pass **reference** as query (?reference=mudbase_...). On success, a subscription is created. No auth required when using the platform gateway (mudbase_ refs). Org-level gateway verification may require JWT. References starting with pmt_ are rejected (crypto billing is not enabled on this API).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\BillingApi(
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

[**\MudbaseSDK\Model\VerifyPayment200Response**](../Model/VerifyPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
