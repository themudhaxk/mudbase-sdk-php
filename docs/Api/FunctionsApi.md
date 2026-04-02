# OpenAPI\Client\FunctionsApi

Serverless function management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**functionsActivate()**](FunctionsApi.md#functionsActivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**functionsCreate()**](FunctionsApi.md#functionsCreate) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**functionsDeactivate()**](FunctionsApi.md#functionsDeactivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**functionsDelete()**](FunctionsApi.md#functionsDelete) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**functionsExecute()**](FunctionsApi.md#functionsExecute) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**functionsGet()**](FunctionsApi.md#functionsGet) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**functionsGetLogs()**](FunctionsApi.md#functionsGetLogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**functionsGetVersions()**](FunctionsApi.md#functionsGetVersions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**functionsList()**](FunctionsApi.md#functionsList) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**functionsRetry()**](FunctionsApi.md#functionsRetry) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**functionsRollback()**](FunctionsApi.md#functionsRollback) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**functionsSimulate()**](FunctionsApi.md#functionsSimulate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**functionsTriggerWebhook()**](FunctionsApi.md#functionsTriggerWebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**functionsUpdate()**](FunctionsApi.md#functionsUpdate) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |


## `functionsActivate()`

```php
functionsActivate($project_id, $function_id): \OpenAPI\Client\Model\FunctionResponse
```

Activate function

Activate a deactivated function. Active functions can be triggered.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to activate.

try {
    $result = $apiInstance->functionsActivate($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsActivate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to activate. | |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsCreate()`

```php
functionsCreate($project_id, $create_function_request): \OpenAPI\Client\Model\FunctionResponse
```

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, wallet, cron, messaging. Sandbox utilities available: db, files, messaging, wallet, utils, env, console.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$create_function_request = {"name":"OnUserCreate","description":"Process new users","code":"const count = await db.find('users', payload.document?.data ? { email: payload.document.data.email } : {});\nreturn { found: count.length };\n","trigger":{"type":"document","event":"create","collectionId":"685ada8fd9416ac02f171abf"},"environment":{"DEBUG":"true"}}; // \OpenAPI\Client\Model\CreateFunctionRequest | Function name, description, code, trigger config, and optional environment.

try {
    $result = $apiInstance->functionsCreate($project_id, $create_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsCreate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **create_function_request** | [**\OpenAPI\Client\Model\CreateFunctionRequest**](../Model/CreateFunctionRequest.md)| Function name, description, code, trigger config, and optional environment. | |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsDeactivate()`

```php
functionsDeactivate($project_id, $function_id): \OpenAPI\Client\Model\FunctionResponse
```

Deactivate function

Deactivate a function. Deactivated functions will not be triggered.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to deactivate.

try {
    $result = $apiInstance->functionsDeactivate($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsDeactivate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to deactivate. | |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsDelete()`

```php
functionsDelete($project_id, $function_id): \OpenAPI\Client\Model\FunctionsDelete200Response
```

Delete function

Delete a function permanently. This is a destructive operation.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$function_id = 'function_id_example'; // string | Function ID to delete.

try {
    $result = $apiInstance->functionsDelete($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **function_id** | **string**| Function ID to delete. | |

### Return type

[**\OpenAPI\Client\Model\FunctionsDelete200Response**](../Model/FunctionsDelete200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsExecute()`

```php
functionsExecute($project_id, $function_id, $functions_execute_request): \OpenAPI\Client\Model\FunctionExecutionResponse
```

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to execute.
$functions_execute_request = {"payload":{"userId":"685acbe0e129932fbb7a0fc2","action":"process"}}; // \OpenAPI\Client\Model\FunctionsExecuteRequest | Optional JSON payload merged with trigger context (e.g. document, file, webhook body). Omit for no custom input.

try {
    $result = $apiInstance->functionsExecute($project_id, $function_id, $functions_execute_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsExecute: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to execute. | |
| **functions_execute_request** | [**\OpenAPI\Client\Model\FunctionsExecuteRequest**](../Model/FunctionsExecuteRequest.md)| Optional JSON payload merged with trigger context (e.g. document, file, webhook body). Omit for no custom input. | [optional] |

### Return type

[**\OpenAPI\Client\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsGet()`

```php
functionsGet($project_id, $function_id): \OpenAPI\Client\Model\FunctionResponse
```

Get function

Get function details by ID including createdBy/updatedBy.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$function_id = 'function_id_example'; // string | Function ID.

try {
    $result = $apiInstance->functionsGet($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **function_id** | **string**| Function ID. | |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsGetLogs()`

```php
functionsGetLogs($project_id, $function_id, $limit, $offset): \OpenAPI\Client\Model\FunctionLogsResponse
```

Get function execution logs

Get execution logs with pagination. Includes stats (totalExecutions, successful, failed, successRate, avgExecutionTime, lastRun).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to get logs for.
$limit = 50; // int | Maximum number of log entries to return.
$offset = 0; // int | Number of log entries to skip for pagination.

try {
    $result = $apiInstance->functionsGetLogs($project_id, $function_id, $limit, $offset);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsGetLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to get logs for. | |
| **limit** | **int**| Maximum number of log entries to return. | [optional] [default to 50] |
| **offset** | **int**| Number of log entries to skip for pagination. | [optional] [default to 0] |

### Return type

[**\OpenAPI\Client\Model\FunctionLogsResponse**](../Model/FunctionLogsResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsGetVersions()`

```php
functionsGetVersions($project_id, $function_id): \OpenAPI\Client\Model\FunctionsGetVersions200Response
```

Get function versions

List all code versions for a function. Used for rollback.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to list versions for.

try {
    $result = $apiInstance->functionsGetVersions($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsGetVersions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to list versions for. | |

### Return type

[**\OpenAPI\Client\Model\FunctionsGetVersions200Response**](../Model/FunctionsGetVersions200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsList()`

```php
functionsList($project_id, $page, $limit, $search, $trigger_type, $is_active): \OpenAPI\Client\Model\FunctionListResponse
```

List functions

List serverless functions in a project with optional search and filters. Supports trigger types: http, event, document, file, webhook, wallet, cron, messaging.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$page = 1; // int | Page number (1-based).
$limit = 20; // int | Number of functions per page.
$search = 'search_example'; // string | Search by name or description
$trigger_type = 'trigger_type_example'; // string | Filter by trigger type
$is_active = True; // bool | Filter by active status (true/false)

try {
    $result = $apiInstance->functionsList($project_id, $page, $limit, $search, $trigger_type, $is_active);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of functions per page. | [optional] [default to 20] |
| **search** | **string**| Search by name or description | [optional] |
| **trigger_type** | **string**| Filter by trigger type | [optional] |
| **is_active** | **bool**| Filter by active status (true/false) | [optional] |

### Return type

[**\OpenAPI\Client\Model\FunctionListResponse**](../Model/FunctionListResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsRetry()`

```php
functionsRetry($project_id, $function_id, $execution_index): \OpenAPI\Client\Model\FunctionExecutionResponse
```

Retry failed execution

Retry a failed execution by its index (0-based) in the logs. Cannot retry successful executions.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to retry execution for.
$execution_index = 56; // int | 0-based index of the execution in logs

try {
    $result = $apiInstance->functionsRetry($project_id, $function_id, $execution_index);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsRetry: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to retry execution for. | |
| **execution_index** | **int**| 0-based index of the execution in logs | |

### Return type

[**\OpenAPI\Client\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsRollback()`

```php
functionsRollback($project_id, $function_id, $functions_rollback_request): \OpenAPI\Client\Model\FunctionResponse
```

Rollback to previous version

Rollback function code to a previous version. Version number is required.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to rollback.
$functions_rollback_request = {"version":2}; // \OpenAPI\Client\Model\FunctionsRollbackRequest | Version number (integer) to rollback to; use GET .../versions to list available versions.

try {
    $result = $apiInstance->functionsRollback($project_id, $function_id, $functions_rollback_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsRollback: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to rollback. | |
| **functions_rollback_request** | [**\OpenAPI\Client\Model\FunctionsRollbackRequest**](../Model/FunctionsRollbackRequest.md)| Version number (integer) to rollback to; use GET .../versions to list available versions. | |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsSimulate()`

```php
functionsSimulate($project_id, $function_id, $functions_simulate_request): \OpenAPI\Client\Model\FunctionExecutionResponse
```

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, wallet, or cron payloads. Executes the function with the provided eventContext merged into the payload.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) that owns the function.
$function_id = 'function_id_example'; // string | Function ID (MongoDB ObjectId) to simulate.
$functions_simulate_request = {"trigger":{"type":"document","event":"create"},"eventContext":{"document":{"_id":"685ae1210136e73fa1dcaf36","collectionId":"685ada8fd9416ac02f171abf","data":{"name":"John","email":"john@example.com"}}}}; // \OpenAPI\Client\Model\FunctionsSimulateRequest | Simulated trigger (type, event) and eventContext (document, file, webhook, wallet, message, or cron). Merged into the function payload for testing.

try {
    $result = $apiInstance->functionsSimulate($project_id, $function_id, $functions_simulate_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsSimulate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) that owns the function. | |
| **function_id** | **string**| Function ID (MongoDB ObjectId) to simulate. | |
| **functions_simulate_request** | [**\OpenAPI\Client\Model\FunctionsSimulateRequest**](../Model/FunctionsSimulateRequest.md)| Simulated trigger (type, event) and eventContext (document, file, webhook, wallet, message, or cron). Merged into the function payload for testing. | [optional] |

### Return type

[**\OpenAPI\Client\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsTriggerWebhook()`

```php
functionsTriggerWebhook($project_id, $x_webhook_secret, $body): \OpenAPI\Client\Model\FunctionsTriggerWebhook200Response
```

Trigger webhook functions

Public endpoint for external services to trigger functions with `trigger.type: webhook`. No authentication required. Optionally verify using `X-Webhook-Secret` header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 30 requests per 15 minutes per IP.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string | Project ID.
$x_webhook_secret = 'x_webhook_secret_example'; // string | Optional webhook secret for verification
$body = array('key' => new \stdClass); // object | Payload sent to the triggered function(s).

try {
    $result = $apiInstance->functionsTriggerWebhook($project_id, $x_webhook_secret, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsTriggerWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **x_webhook_secret** | **string**| Optional webhook secret for verification | [optional] |
| **body** | **object**| Payload sent to the triggered function(s). | [optional] |

### Return type

[**\OpenAPI\Client\Model\FunctionsTriggerWebhook200Response**](../Model/FunctionsTriggerWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`, `application/x-www-form-urlencoded`, `text/plain`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `functionsUpdate()`

```php
functionsUpdate($project_id, $function_id, $update_function_request): \OpenAPI\Client\Model\FunctionResponse
```

Update function

Update function configuration. Code changes are versioned automatically.

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


$apiInstance = new OpenAPI\Client\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$function_id = 'function_id_example'; // string | Function ID.
$update_function_request = {"name":"OnUserCreate v2","code":"return { version: 2 };\n","versionComment":"Add version tracking"}; // \OpenAPI\Client\Model\UpdateFunctionRequest | Fields to update (name, description, code, trigger, environment, isActive, limits, retryPolicy).

try {
    $result = $apiInstance->functionsUpdate($project_id, $function_id, $update_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->functionsUpdate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **function_id** | **string**| Function ID. | |
| **update_function_request** | [**\OpenAPI\Client\Model\UpdateFunctionRequest**](../Model/UpdateFunctionRequest.md)| Fields to update (name, description, code, trigger, environment, isActive, limits, retryPolicy). | [optional] |

### Return type

[**\OpenAPI\Client\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
