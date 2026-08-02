# OpenAPI\Client\KYCApi

Identity verification — platform KYC sessions, status, and white-label webhook config

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**apiKycEventsGet()**](KYCApi.md#apiKycEventsGet) | **GET** /api/kyc/events | List recent compliance webhook deliveries |
| [**apiKycSessionsPost()**](KYCApi.md#apiKycSessionsPost) | **POST** /api/kyc/sessions | Start a platform KYC session |
| [**apiKycStatusGet()**](KYCApi.md#apiKycStatusGet) | **GET** /api/kyc/status | Get the organization&#39;s platform KYC status |
| [**apiKycVerificationsIdGet()**](KYCApi.md#apiKycVerificationsIdGet) | **GET** /api/kyc/verifications/{id} | Get a single KYC verification record |
| [**apiKycWebhookConfigGet()**](KYCApi.md#apiKycWebhookConfigGet) | **GET** /api/kyc/webhook-config | Get white-label KYC webhook config |
| [**apiKycWebhookConfigPut()**](KYCApi.md#apiKycWebhookConfigPut) | **PUT** /api/kyc/webhook-config | Set white-label KYC webhook config |
| [**apiKycWebhookConfigTestPost()**](KYCApi.md#apiKycWebhookConfigTestPost) | **POST** /api/kyc/webhook-config/test | Send a signed test event to the configured webhook endpoint |
| [**apiKycWorkflowsGet()**](KYCApi.md#apiKycWorkflowsGet) | **GET** /api/kyc/workflows | List available verification workflows |
| [**apiProjectsProjectIdKybSessionsPost()**](KYCApi.md#apiProjectsProjectIdKybSessionsPost) | **POST** /api/projects/{projectId}/kyb/sessions | Start a business verification (KYB) session for one of your business customers |


## `apiKycEventsGet()`

```php
apiKycEventsGet($limit)
```

List recent compliance webhook deliveries

Audit trail of compliance webhook events received for this organization and whether Mudbase forwarded each one to the organization's own endpoint. Owner, admin, and developer roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$limit = 25; // int | Maximum number of events to return.

try {
    $apiInstance->apiKycEventsGet($limit);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycEventsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**| Maximum number of events to return. | [optional] [default to 25] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycSessionsPost()`

```php
apiKycSessionsPost($api_kyc_sessions_post_request)
```

Start a platform KYC session

Creates a verification session for the caller's organization. Owner/admin only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$api_kyc_sessions_post_request = new \OpenAPI\Client\Model\ApiKycSessionsPostRequest(); // \OpenAPI\Client\Model\ApiKycSessionsPostRequest

try {
    $apiInstance->apiKycSessionsPost($api_kyc_sessions_post_request);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycSessionsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **api_kyc_sessions_post_request** | [**\OpenAPI\Client\Model\ApiKycSessionsPostRequest**](../Model/ApiKycSessionsPostRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycStatusGet()`

```php
apiKycStatusGet()
```

Get the organization's platform KYC status

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->apiKycStatusGet();
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycStatusGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycVerificationsIdGet()`

```php
apiKycVerificationsIdGet($id)
```

Get a single KYC verification record

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | Verification record id.

try {
    $apiInstance->apiKycVerificationsIdGet($id);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycVerificationsIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| Verification record id. | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycWebhookConfigGet()`

```php
apiKycWebhookConfigGet(): \OpenAPI\Client\Model\ApiKycWebhookConfigGet200Response
```

Get white-label KYC webhook config

Returns the destination URL where the organization's own system receives KYC results and whether a signing secret is set. The secret value itself is never returned. Owner/admin only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->apiKycWebhookConfigGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycWebhookConfigGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\ApiKycWebhookConfigGet200Response**](../Model/ApiKycWebhookConfigGet200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycWebhookConfigPut()`

```php
apiKycWebhookConfigPut($api_kyc_webhook_config_put_request): \OpenAPI\Client\Model\ApiKycWebhookConfigPut200Response
```

Set white-label KYC webhook config

Updates the destination URL and/or signing secret used to deliver KYC results to the organization's own system. The outbound URL is SSRF-validated. When generateSecret is true a new secret is created and returned once. Owner/admin only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$api_kyc_webhook_config_put_request = new \OpenAPI\Client\Model\ApiKycWebhookConfigPutRequest(); // \OpenAPI\Client\Model\ApiKycWebhookConfigPutRequest

try {
    $result = $apiInstance->apiKycWebhookConfigPut($api_kyc_webhook_config_put_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycWebhookConfigPut: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **api_kyc_webhook_config_put_request** | [**\OpenAPI\Client\Model\ApiKycWebhookConfigPutRequest**](../Model/ApiKycWebhookConfigPutRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\ApiKycWebhookConfigPut200Response**](../Model/ApiKycWebhookConfigPut200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycWebhookConfigTestPost()`

```php
apiKycWebhookConfigTestPost(): \OpenAPI\Client\Model\ApiKycWebhookConfigTestPost200Response
```

Send a signed test event to the configured webhook endpoint

Delivers a sample `kyc.test` payload, signed exactly like a real event, so you can confirm your receiver and signature verification work. Ignores your event subscription. Owner/admin only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->apiKycWebhookConfigTestPost();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycWebhookConfigTestPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\ApiKycWebhookConfigTestPost200Response**](../Model/ApiKycWebhookConfigTestPost200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiKycWorkflowsGet()`

```php
apiKycWorkflowsGet(): \OpenAPI\Client\Model\ApiKycWorkflowsGet200Response
```

List available verification workflows

Returns the verification workflows configured on this Mudbase account, split into kyc (individual identity) and kyb (business verification). Used to choose a default workflow in the console instead of pasting a workflow UUID. Owner/admin only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->apiKycWorkflowsGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiKycWorkflowsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\ApiKycWorkflowsGet200Response**](../Model/ApiKycWorkflowsGet200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiProjectsProjectIdKybSessionsPost()`

```php
apiProjectsProjectIdKybSessionsPost($project_id, $api_projects_project_id_kyb_sessions_post_request)
```

Start a business verification (KYB) session for one of your business customers

Creates a KYB session scoped to your project. The workflow is resolved from the request, then the organization's configured default KYB workflow, then the platform default. Results arrive at your configured KYC webhook as `kyb.completed`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\KYCApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$api_projects_project_id_kyb_sessions_post_request = new \OpenAPI\Client\Model\ApiProjectsProjectIdKybSessionsPostRequest(); // \OpenAPI\Client\Model\ApiProjectsProjectIdKybSessionsPostRequest

try {
    $apiInstance->apiProjectsProjectIdKybSessionsPost($project_id, $api_projects_project_id_kyb_sessions_post_request);
} catch (Exception $e) {
    echo 'Exception when calling KYCApi->apiProjectsProjectIdKybSessionsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **api_projects_project_id_kyb_sessions_post_request** | [**\OpenAPI\Client\Model\ApiProjectsProjectIdKybSessionsPostRequest**](../Model/ApiProjectsProjectIdKybSessionsPostRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
