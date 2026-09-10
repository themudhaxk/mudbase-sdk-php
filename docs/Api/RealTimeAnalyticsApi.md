# MudbaseSDK\RealTimeAnalyticsApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**checkUserPresence()**](RealTimeAnalyticsApi.md#checkUserPresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**getActiveUsers()**](RealTimeAnalyticsApi.md#getActiveUsers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**getEventThroughput()**](RealTimeAnalyticsApi.md#getEventThroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**getGlobalAnalytics()**](RealTimeAnalyticsApi.md#getGlobalAnalytics) | **GET** /api/realtime/analytics | Get global real-time analytics |
| [**getHistoricalAnalytics()**](RealTimeAnalyticsApi.md#getHistoricalAnalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**getProjectAnalytics()**](RealTimeAnalyticsApi.md#getProjectAnalytics) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |


## `checkUserPresence()`

```php
checkUserPresence($project_id, $check_user_presence_request): \MudbaseSDK\Model\CheckUserPresence200Response
```

Check presence status for users

Returns online status for specified user IDs

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$check_user_presence_request = {"userIds":["685acbe0e129932fbb7a0fc2","685acbe0e129932fbb7a0fc3"]}; // \MudbaseSDK\Model\CheckUserPresenceRequest

try {
    $result = $apiInstance->checkUserPresence($project_id, $check_user_presence_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->checkUserPresence: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **check_user_presence_request** | [**\MudbaseSDK\Model\CheckUserPresenceRequest**](../Model/CheckUserPresenceRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\CheckUserPresence200Response**](../Model/CheckUserPresence200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getActiveUsers()`

```php
getActiveUsers($project_id): \MudbaseSDK\Model\GetActiveUsers200Response
```

Get active users for a project

Returns list of currently connected users

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getActiveUsers($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->getActiveUsers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetActiveUsers200Response**](../Model/GetActiveUsers200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getEventThroughput()`

```php
getEventThroughput($project_id, $window): \MudbaseSDK\Model\GetEventThroughput200Response
```

Get event throughput metrics

Returns event throughput for a project

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$window = 60000; // int | Time window in milliseconds

try {
    $result = $apiInstance->getEventThroughput($project_id, $window);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->getEventThroughput: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **window** | **int**| Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**\MudbaseSDK\Model\GetEventThroughput200Response**](../Model/GetEventThroughput200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getGlobalAnalytics()`

```php
getGlobalAnalytics(): \MudbaseSDK\Model\GetGlobalAnalytics200Response
```

Get global real-time analytics

Returns system-wide real-time metrics (admin only)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getGlobalAnalytics();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->getGlobalAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\MudbaseSDK\Model\GetGlobalAnalytics200Response**](../Model/GetGlobalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getHistoricalAnalytics()`

```php
getHistoricalAnalytics($project_id, $period): \MudbaseSDK\Model\GetHistoricalAnalytics200Response
```

Get historical analytics

Returns historical analytics for charting

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$period = 'hour'; // string | Time period for historical data

try {
    $result = $apiInstance->getHistoricalAnalytics($project_id, $period);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->getHistoricalAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **period** | **string**| Time period for historical data | [optional] [default to &#39;hour&#39;] |

### Return type

[**\MudbaseSDK\Model\GetHistoricalAnalytics200Response**](../Model/GetHistoricalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectAnalytics()`

```php
getProjectAnalytics($project_id): \MudbaseSDK\Model\GetProjectAnalytics200Response
```

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RealTimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getProjectAnalytics($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealTimeAnalyticsApi->getProjectAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetProjectAnalytics200Response**](../Model/GetProjectAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
