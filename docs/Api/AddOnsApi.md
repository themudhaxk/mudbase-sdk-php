# OpenAPI\Client\AddOnsApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**apiAddonsGet()**](AddOnsApi.md#apiAddonsGet) | **GET** /api/addons | List the add-on catalog |
| [**apiProjectsProjectIdAddonsAddonInvokePost()**](AddOnsApi.md#apiProjectsProjectIdAddonsAddonInvokePost) | **POST** /api/projects/{projectId}/addons/{addon}/invoke | Invoke an add-on for a project |
| [**apiProjectsProjectIdAddonsJobsIdGet()**](AddOnsApi.md#apiProjectsProjectIdAddonsJobsIdGet) | **GET** /api/projects/{projectId}/addons/jobs/{id} | Get an add-on job status |


## `apiAddonsGet()`

```php
apiAddonsGet(): \OpenAPI\Client\Model\ApiAddonsGet200Response
```

List the add-on catalog

Returns the available add-ons (key, metadata, pricing) the caller can invoke.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AddOnsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->apiAddonsGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddOnsApi->apiAddonsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\ApiAddonsGet200Response**](../Model/ApiAddonsGet200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiProjectsProjectIdAddonsAddonInvokePost()`

```php
apiProjectsProjectIdAddonsAddonInvokePost($project_id, $addon, $body): \OpenAPI\Client\Model\ApiProjectsProjectIdAddonsAddonInvokePost200Response
```

Invoke an add-on for a project

Runs the named add-on against the project. Returns the job synchronously (200) when it completes immediately, or 202 with a pending job when processing continues in the background.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AddOnsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$addon = 'addon_example'; // string | Add-on key from the catalog.
$body = array('key' => new \stdClass); // object

try {
    $result = $apiInstance->apiProjectsProjectIdAddonsAddonInvokePost($project_id, $addon, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddOnsApi->apiProjectsProjectIdAddonsAddonInvokePost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **addon** | **string**| Add-on key from the catalog. | |
| **body** | **object**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\ApiProjectsProjectIdAddonsAddonInvokePost200Response**](../Model/ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiProjectsProjectIdAddonsJobsIdGet()`

```php
apiProjectsProjectIdAddonsJobsIdGet($project_id, $id): \OpenAPI\Client\Model\ApiProjectsProjectIdAddonsAddonInvokePost200Response
```

Get an add-on job status

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AddOnsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$id = 'id_example'; // string | Add-on job id.

try {
    $result = $apiInstance->apiProjectsProjectIdAddonsJobsIdGet($project_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddOnsApi->apiProjectsProjectIdAddonsJobsIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **id** | **string**| Add-on job id. | |

### Return type

[**\OpenAPI\Client\Model\ApiProjectsProjectIdAddonsAddonInvokePost200Response**](../Model/ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
