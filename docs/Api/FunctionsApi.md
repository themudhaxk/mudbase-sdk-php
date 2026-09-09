# MudbaseSDK\FunctionsApi

Serverless function management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**activateFunction()**](FunctionsApi.md#activateFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**createFunction()**](FunctionsApi.md#createFunction) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**deactivateFunction()**](FunctionsApi.md#deactivateFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**deleteFunction()**](FunctionsApi.md#deleteFunction) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**executeFunction()**](FunctionsApi.md#executeFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**getFunction()**](FunctionsApi.md#getFunction) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**getFunctionExecution()**](FunctionsApi.md#getFunctionExecution) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId} | Get execution status |
| [**getFunctionLogs()**](FunctionsApi.md#getFunctionLogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**getFunctionVersions()**](FunctionsApi.md#getFunctionVersions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**listFunctions()**](FunctionsApi.md#listFunctions) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**retryFunctionExecution()**](FunctionsApi.md#retryFunctionExecution) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**rollbackFunction()**](FunctionsApi.md#rollbackFunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**simulateFunctionTrigger()**](FunctionsApi.md#simulateFunctionTrigger) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**triggerFunctionWebhook()**](FunctionsApi.md#triggerFunctionWebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**updateFunction()**](FunctionsApi.md#updateFunction) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |


## `activateFunction()`

```php
activateFunction($project_id, $function_id): \MudbaseSDK\Model\FunctionResponse
```

Activate function

Activate a deactivated function. Active functions can be triggered.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string

try {
    $result = $apiInstance->activateFunction($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->activateFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createFunction()`

```php
createFunction($project_id, $create_function_request): \MudbaseSDK\Model\FunctionResponse
```

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, cron, messaging. Sandbox globals available today: `payload`, `context`, `env`, `console`. Function code runs in an isolated worker with no ambient network or database access — it can only read its trigger payload, the `env` vars you configure, and return a JSON-serializable result; it cannot yet call back into your project's database, storage, or messaging APIs from inside the function body. If you need to read or write project data from a function, call the regular REST API (with your own API key) from your own backend in response to the function's returned result, rather than from within the function's own code.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_function_request = {"name":"OnUserCreate","description":"Process new users","code":"// payload.document holds the created/updated document for this trigger\nconst created = payload.document?.data || {};\nconsole.log('New user document:', created.email);\nreturn { email: created.email || null, receivedAt: new Date().toISOString() };\n","trigger":{"type":"document","event":"create","collectionId":"685ada8fd9416ac02f171abf"},"environment":{"DEBUG":"true"}}; // \MudbaseSDK\Model\CreateFunctionRequest

try {
    $result = $apiInstance->createFunction($project_id, $create_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->createFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **create_function_request** | [**\MudbaseSDK\Model\CreateFunctionRequest**](../Model/CreateFunctionRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deactivateFunction()`

```php
deactivateFunction($project_id, $function_id): \MudbaseSDK\Model\FunctionResponse
```

Deactivate function

Deactivate a function. Deactivated functions will not be triggered.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string

try {
    $result = $apiInstance->deactivateFunction($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->deactivateFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteFunction()`

```php
deleteFunction($project_id, $function_id): \MudbaseSDK\Model\DeleteFunction200Response
```

Delete function

Delete a function permanently. This is a destructive operation.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string

try {
    $result = $apiInstance->deleteFunction($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->deleteFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\DeleteFunction200Response**](../Model/DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `executeFunction()`

```php
executeFunction($project_id, $function_id, $execute_function_request): \MudbaseSDK\Model\FunctionExecutionResponse
```

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour.  This endpoint is asynchronous: it returns 202 immediately with an `executionId`, before the function has necessarily finished running. Poll `GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}` until `status` leaves `queued`/`running` to get the real result, error, and duration.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$execute_function_request = {"payload":{"userId":"685acbe0e129932fbb7a0fc2","action":"process"}}; // \MudbaseSDK\Model\ExecuteFunctionRequest

try {
    $result = $apiInstance->executeFunction($project_id, $function_id, $execute_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->executeFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **execute_function_request** | [**\MudbaseSDK\Model\ExecuteFunctionRequest**](../Model/ExecuteFunctionRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFunction()`

```php
getFunction($project_id, $function_id): \MudbaseSDK\Model\FunctionResponse
```

Get function

Get function details by ID including createdBy/updatedBy.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string

try {
    $result = $apiInstance->getFunction($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->getFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFunctionExecution()`

```php
getFunctionExecution($project_id, $function_id, $execution_id): \MudbaseSDK\Model\FunctionExecutionStatusResponse
```

Get execution status

Poll this after Execute function or Simulate trigger to get the real outcome — both of those endpoints return 202 immediately and do not carry the result themselves. `status` is one of `queued`, `provisioning`, `running`, `success`, `failed`, `timeout`; `result`/`error`/`durationMs`/`logs` are only populated once `status` leaves `queued`/`running`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$execution_id = 'execution_id_example'; // string

try {
    $result = $apiInstance->getFunctionExecution($project_id, $function_id, $execution_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->getFunctionExecution: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **execution_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\FunctionExecutionStatusResponse**](../Model/FunctionExecutionStatusResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFunctionLogs()`

```php
getFunctionLogs($project_id, $function_id, $limit, $offset): \MudbaseSDK\Model\FunctionLogsResponse
```

Get function execution logs

Get execution logs with pagination. Includes stats (totalExecutions, successful, failed, successRate, avgExecutionTime, lastRun).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$limit = 50; // int
$offset = 0; // int

try {
    $result = $apiInstance->getFunctionLogs($project_id, $function_id, $limit, $offset);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->getFunctionLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 50] |
| **offset** | **int**|  | [optional] [default to 0] |

### Return type

[**\MudbaseSDK\Model\FunctionLogsResponse**](../Model/FunctionLogsResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFunctionVersions()`

```php
getFunctionVersions($project_id, $function_id): \MudbaseSDK\Model\GetFunctionVersions200Response
```

Get function versions

List all code versions for a function. Used for rollback.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string

try {
    $result = $apiInstance->getFunctionVersions($project_id, $function_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->getFunctionVersions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetFunctionVersions200Response**](../Model/GetFunctionVersions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listFunctions()`

```php
listFunctions($project_id, $page, $limit, $search, $trigger_type, $is_active): \MudbaseSDK\Model\FunctionListResponse
```

List functions

List serverless functions in a project with optional search and filters. Supports trigger types: http, event, document, file, webhook, cron, messaging.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$page = 1; // int
$limit = 20; // int
$search = 'search_example'; // string | Search by name or description
$trigger_type = 'trigger_type_example'; // string | Filter by trigger type
$is_active = True; // bool | Filter by active status (true/false)

try {
    $result = $apiInstance->listFunctions($project_id, $page, $limit, $search, $trigger_type, $is_active);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->listFunctions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **search** | **string**| Search by name or description | [optional] |
| **trigger_type** | **string**| Filter by trigger type | [optional] |
| **is_active** | **bool**| Filter by active status (true/false) | [optional] |

### Return type

[**\MudbaseSDK\Model\FunctionListResponse**](../Model/FunctionListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `retryFunctionExecution()`

```php
retryFunctionExecution($project_id, $function_id, $execution_index): \MudbaseSDK\Model\FunctionExecutionResponse
```

Retry failed execution

Retry a failed execution by its index (0-based) in the logs. Cannot retry successful executions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$execution_index = 56; // int | 0-based index of the execution in logs

try {
    $result = $apiInstance->retryFunctionExecution($project_id, $function_id, $execution_index);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->retryFunctionExecution: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **execution_index** | **int**| 0-based index of the execution in logs | |

### Return type

[**\MudbaseSDK\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `rollbackFunction()`

```php
rollbackFunction($project_id, $function_id, $rollback_function_request): \MudbaseSDK\Model\FunctionResponse
```

Rollback to previous version

Rollback function code to a previous version. Version number is required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$rollback_function_request = {"version":2}; // \MudbaseSDK\Model\RollbackFunctionRequest

try {
    $result = $apiInstance->rollbackFunction($project_id, $function_id, $rollback_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->rollbackFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **rollback_function_request** | [**\MudbaseSDK\Model\RollbackFunctionRequest**](../Model/RollbackFunctionRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `simulateFunctionTrigger()`

```php
simulateFunctionTrigger($project_id, $function_id, $simulate_function_trigger_request): \MudbaseSDK\Model\FunctionExecutionResponse
```

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, or cron payloads. Executes the function with the provided eventContext merged into the payload.  Asynchronous, same pattern as Execute function: returns 202 immediately with an `executionId`. Poll `GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}` for the real result.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$simulate_function_trigger_request = {"trigger":{"type":"document","event":"create"},"eventContext":{"document":{"_id":"685ae1210136e73fa1dcaf36","collectionId":"685ada8fd9416ac02f171abf","data":{"name":"John","email":"john@example.com"}}}}; // \MudbaseSDK\Model\SimulateFunctionTriggerRequest

try {
    $result = $apiInstance->simulateFunctionTrigger($project_id, $function_id, $simulate_function_trigger_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->simulateFunctionTrigger: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **simulate_function_trigger_request** | [**\MudbaseSDK\Model\SimulateFunctionTriggerRequest**](../Model/SimulateFunctionTriggerRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\FunctionExecutionResponse**](../Model/FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `triggerFunctionWebhook()`

```php
triggerFunctionWebhook($project_id, $x_webhook_secret, $body): \MudbaseSDK\Model\TriggerFunctionWebhook200Response
```

Trigger webhook functions

Public endpoint for external services to trigger functions with `trigger.type: webhook`. No authentication required. Optionally verify using `X-Webhook-Secret` header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 120 requests per 15 minutes per IP (per-org adjustable).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$project_id = 'project_id_example'; // string
$x_webhook_secret = 'x_webhook_secret_example'; // string | Optional webhook secret for verification
$body = {"event":"user.created","userId":"507f1f77bcf86cd799439011","timestamp":"2026-04-03T12:00:00.000Z"}; // object

try {
    $result = $apiInstance->triggerFunctionWebhook($project_id, $x_webhook_secret, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->triggerFunctionWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **x_webhook_secret** | **string**| Optional webhook secret for verification | [optional] |
| **body** | **object**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\TriggerFunctionWebhook200Response**](../Model/TriggerFunctionWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`, `application/x-www-form-urlencoded`, `text/plain`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateFunction()`

```php
updateFunction($project_id, $function_id, $update_function_request): \MudbaseSDK\Model\FunctionResponse
```

Update function

Update function configuration. Code changes are versioned automatically.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\FunctionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$function_id = 'function_id_example'; // string
$update_function_request = {"name":"OnUserCreate v2","code":"return { version: 2 };\n","versionComment":"Add version tracking"}; // \MudbaseSDK\Model\UpdateFunctionRequest

try {
    $result = $apiInstance->updateFunction($project_id, $function_id, $update_function_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FunctionsApi->updateFunction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **function_id** | **string**|  | |
| **update_function_request** | [**\MudbaseSDK\Model\UpdateFunctionRequest**](../Model/UpdateFunctionRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\FunctionResponse**](../Model/FunctionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
