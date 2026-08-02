# OpenAPI\Client\WebhooksApi

**Outbound webhooks (Mudbase → your URL):** Configure a single callback URL per project with &#x60;PUT /api/webhooks/projects/{projectId}/config&#x60;. When events fire, Mudbase creates **delivery log** rows (&#x60;WebhookLog&#x60; in the database) and HTTP POSTs to your URL.  **What is &#x60;webhookId&#x60; in the API?** - In **&#x60;POST /api/webhooks/trigger&#x60;** and **&#x60;POST /api/webhooks/retry/{webhookId}&#x60;**, the id is the **MongoDB &#x60;_id&#x60; of a webhook delivery log** document—not a separate “subscription id” from the config endpoint. - After **&#x60;POST /api/webhooks/trigger&#x60;**, the JSON field **&#x60;webhookId&#x60;** in the response is that log’s **&#x60;_id&#x60;**. Use the same value in the retry path to re-queue delivery. - List logs with **&#x60;GET /api/webhooks&#x60;** (org-wide) or **&#x60;GET /api/webhooks/projects/{projectId}&#x60;** (project-scoped); each row’s **&#x60;_id&#x60;** is what you pass to retry. - Each log also has an internal string field **&#x60;webhookId&#x60;** (e.g. &#x60;manual-173…&#x60;) used for correlation; you normally use the document **&#x60;_id&#x60;** for retry.  **Wallet non-custodial webhooks** (&#x60;/api/wallet/non-custodial/webhooks/...&#x60;) are a **different** feature (on-chain notification subscriptions) with their own ids—see the Wallet tag.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**configureWebhook()**](WebhooksApi.md#configureWebhook) | **PUT** /api/webhooks/projects/{projectId}/config | Create or update project webhook |
| [**getWebhookConfig()**](WebhooksApi.md#getWebhookConfig) | **GET** /api/webhooks/projects/{projectId}/config | Get project webhook configuration |
| [**getWebhookStats()**](WebhooksApi.md#getWebhookStats) | **GET** /api/webhooks/stats | Get webhook delivery statistics |
| [**listProjectWebhookLogs()**](WebhooksApi.md#listProjectWebhookLogs) | **GET** /api/webhooks/projects/{projectId} | List webhook delivery logs (project) |
| [**listWebhooks()**](WebhooksApi.md#listWebhooks) | **GET** /api/webhooks | List webhook delivery logs (organization) |
| [**retryWebhook()**](WebhooksApi.md#retryWebhook) | **POST** /api/webhooks/retry/{webhookId} | Retry a failed webhook delivery |
| [**testWebhookTransformation()**](WebhooksApi.md#testWebhookTransformation) | **POST** /api/webhooks/projects/{projectId}/test-transformation | Test webhook transformation |
| [**triggerWebhook()**](WebhooksApi.md#triggerWebhook) | **POST** /api/webhooks/trigger | Manually trigger an outbound webhook |


## `configureWebhook()`

```php
configureWebhook($project_id, $configure_webhook_request): \OpenAPI\Client\Model\ConfigureWebhook200Response
```

Create or update project webhook

Set or update the project webhook URL and options. This is how you **add** or **create** a webhook for a project: provide **webhookUrl** to enable delivery; omit or set to null to disable. Optionally set **webhookSecret**, **webhookEvents**, **webhookVersion**, and **transformations**. Plan limits (webhooks per project) apply when adding a new URL. Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project update access.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$configure_webhook_request = {"webhookUrl":"https://your-app.com/webhooks/mudbase","webhookSecret":"your-secret","webhookEvents":["collection.insert","collection.update","collection.delete"],"webhookVersion":"1.0","transformations":[]}; // \OpenAPI\Client\Model\ConfigureWebhookRequest

try {
    $result = $apiInstance->configureWebhook($project_id, $configure_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->configureWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **configure_webhook_request** | [**\OpenAPI\Client\Model\ConfigureWebhookRequest**](../Model/ConfigureWebhookRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\ConfigureWebhook200Response**](../Model/ConfigureWebhook200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getWebhookConfig()`

```php
getWebhookConfig($project_id): \OpenAPI\Client\Model\GetWebhookConfig200Response
```

Get project webhook configuration

Get the current webhook URL, events, version, and transformations for a project. This is **where Mudbase POSTs event payloads**; it does **not** return a `webhookId`. Delivery ids (`WebhookLog._id`) come from **`POST /api/webhooks/trigger`** or automatic deliveries, and from **list logs** endpoints.  Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project read access.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getWebhookConfig($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->getWebhookConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetWebhookConfig200Response**](../Model/GetWebhookConfig200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getWebhookStats()`

```php
getWebhookStats($project_id, $days): \OpenAPI\Client\Model\WebhookStatsResponse
```

Get webhook delivery statistics

Aggregates **`WebhookLog`** rows for your organization over the last **`days`** (default 7). Optional **`projectId`** filters to a project in your org.  Returns **`statusStats`** (counts and average duration per delivery **status**) and **`eventStats`** (counts and success rate per **event** name).  **Auth:** Organization JWT only (`authRequired`).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Optional; limit stats to this project.
$days = 7; // int

try {
    $result = $apiInstance->getWebhookStats($project_id, $days);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->getWebhookStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Optional; limit stats to this project. | [optional] |
| **days** | **int**|  | [optional] [default to 7] |

### Return type

[**\OpenAPI\Client\Model\WebhookStatsResponse**](../Model/WebhookStatsResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listProjectWebhookLogs()`

```php
listProjectWebhookLogs($project_id, $page, $limit, $status, $event): \OpenAPI\Client\Model\WebhookListResponse
```

List webhook delivery logs (project)

Same **`WebhookLog`** documents as **`GET /api/webhooks`**, scoped to **`projectId`** in the path. Accepts **org JWT**, **project JWT**, or **project API key** with project read access.  Each item’s **`_id`** is the id returned as **`webhookId`** from **`POST /api/webhooks/trigger`** and used in **`POST /api/webhooks/retry/{webhookId}`**.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$page = 1; // int
$limit = 20; // int
$status = 'status_example'; // string
$event = 'event_example'; // string

try {
    $result = $apiInstance->listProjectWebhookLogs($project_id, $page, $limit, $status, $event);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->listProjectWebhookLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **status** | **string**|  | [optional] |
| **event** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\WebhookListResponse**](../Model/WebhookListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listWebhooks()`

```php
listWebhooks($page, $limit, $status, $event, $project_id): \OpenAPI\Client\Model\WebhookListResponse
```

List webhook delivery logs (organization)

Paginated **webhook delivery logs** for your organization (each row is one outbound HTTP attempt). Optional **`projectId`** query filters to a project that belongs to your org.  Use each log document’s **`_id`** (MongoDB ObjectId) as **`webhookId`** when calling **`POST /api/webhooks/retry/{webhookId}`** after a failed delivery. Organization **JWT only** (`OrgBearerAuth`); project API keys are not accepted on this route.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 1; // int
$limit = 20; // int
$status = 'status_example'; // string
$event = 'event_example'; // string
$project_id = 'project_id_example'; // string | Optional; restrict logs to this project (must belong to your org).

try {
    $result = $apiInstance->listWebhooks($page, $limit, $status, $event, $project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->listWebhooks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **status** | **string**|  | [optional] |
| **event** | **string**|  | [optional] |
| **project_id** | **string**| Optional; restrict logs to this project (must belong to your org). | [optional] |

### Return type

[**\OpenAPI\Client\Model\WebhookListResponse**](../Model/WebhookListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `retryWebhook()`

```php
retryWebhook($webhook_id): \OpenAPI\Client\Model\RetryWebhookResponse
```

Retry a failed webhook delivery

**`webhookId`** (path) = **`WebhookLog._id`** (MongoDB ObjectId)—the same value returned as **`webhookId`** from **`POST /api/webhooks/trigger`** and as **`_id`** on **`GET /api/webhooks`** / **`GET /api/webhooks/projects/{projectId}`**.  **Not** the string **`webhookId`** field stored on the log document (e.g. `manual-173…`); use the document **`_id`** for this path.  Resets a non-success log to **pending** and re-delivers. **400** if status is already **`success`**.  **Auth:** Organization JWT only; project API keys are not accepted.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$webhook_id = 'webhook_id_example'; // string | WebhookLog document `_id` (delivery log id).

try {
    $result = $apiInstance->retryWebhook($webhook_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->retryWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_id** | **string**| WebhookLog document &#x60;_id&#x60; (delivery log id). | |

### Return type

[**\OpenAPI\Client\Model\RetryWebhookResponse**](../Model/RetryWebhookResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `testWebhookTransformation()`

```php
testWebhookTransformation($project_id, $test_webhook_transformation_request): \OpenAPI\Client\Model\TestWebhookTransformation200Response
```

Test webhook transformation

Apply transformation rules to a sample payload and return original and transformed payloads. Requires ProjectBearerAuth (JWT) or ApiKeyAuth (X-API-Key) with project update access.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$test_webhook_transformation_request = {"payload":{"event":"collection.insert","data":{"name":"Test"}},"transformations":[]}; // \OpenAPI\Client\Model\TestWebhookTransformationRequest

try {
    $result = $apiInstance->testWebhookTransformation($project_id, $test_webhook_transformation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->testWebhookTransformation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **test_webhook_transformation_request** | [**\OpenAPI\Client\Model\TestWebhookTransformationRequest**](../Model/TestWebhookTransformationRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\TestWebhookTransformation200Response**](../Model/TestWebhookTransformation200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `triggerWebhook()`

```php
triggerWebhook($trigger_webhook_request): \OpenAPI\Client\Model\TriggerWebhookResponse
```

Manually trigger an outbound webhook

Queues an HTTP delivery to **`url`** for **`projectId`** (must belong to your org). Creates a **`WebhookLog`** row, runs delivery, and returns the new log’s **`_id`**.  **Response field `webhookId`:** This is the **MongoDB `_id` of the delivery log** (same as the log’s **`_id`** in list endpoints). It is **not** part of the request body and is **not** the project `webhookSecret` from **`PUT .../config`**.  **Auth:** Org JWT, project JWT, or project API key with **project `update`** permission.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$trigger_webhook_request = {"projectId":"65a1b2c3d4e5f6789012345b","url":"https://your-app.com/webhooks/mudbase","event":"manual.test","payload":{"message":"Hello from Mudbase"}}; // \OpenAPI\Client\Model\TriggerWebhookRequest

try {
    $result = $apiInstance->triggerWebhook($trigger_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->triggerWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **trigger_webhook_request** | [**\OpenAPI\Client\Model\TriggerWebhookRequest**](../Model/TriggerWebhookRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\TriggerWebhookResponse**](../Model/TriggerWebhookResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
