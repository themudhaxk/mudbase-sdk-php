# OpenAPI\Client\IntegrationsApi

Third-party service integrations

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**integrationsExecute()**](IntegrationsApi.md#integrationsExecute) | **POST** /api/integrations/projects/{projectId}/integrations/{integrationId}/execute | Execute integration |
| [**integrationsList()**](IntegrationsApi.md#integrationsList) | **GET** /api/integrations/projects/{projectId}/integrations | Get project integrations |


## `integrationsExecute()`

```php
integrationsExecute($project_id, $integration_id, $integrations_execute_request): \OpenAPI\Client\Model\MultiRoleGetPermissionsMatrix200Response
```

Execute integration

Execute an integration action (API call) with specified endpoint and parameters. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$integration_id = 'integration_id_example'; // string | Integration ID to execute.
$integrations_execute_request = {"endpoint":"/api/v1/users","method":"GET","params":{},"body":{}}; // \OpenAPI\Client\Model\IntegrationsExecuteRequest | Endpoint path, HTTP method, optional params and body for the integration call.

try {
    $result = $apiInstance->integrationsExecute($project_id, $integration_id, $integrations_execute_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->integrationsExecute: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **integration_id** | **string**| Integration ID to execute. | |
| **integrations_execute_request** | [**\OpenAPI\Client\Model\IntegrationsExecuteRequest**](../Model/IntegrationsExecuteRequest.md)| Endpoint path, HTTP method, optional params and body for the integration call. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleGetPermissionsMatrix200Response**](../Model/MultiRoleGetPermissionsMatrix200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `integrationsList()`

```php
integrationsList($project_id): \OpenAPI\Client\Model\IntegrationsList200Response
```

Get project integrations

List all integrations configured for a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.

try {
    $result = $apiInstance->integrationsList($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->integrationsList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |

### Return type

[**\OpenAPI\Client\Model\IntegrationsList200Response**](../Model/IntegrationsList200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
