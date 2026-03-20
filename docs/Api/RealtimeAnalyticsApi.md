# OpenAPI\Client\RealtimeAnalyticsApi

Real-time analytics and monitoring endpoints

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**realtimeAnalyticsCheckUserPresence()**](RealtimeAnalyticsApi.md#realtimeAnalyticsCheckUserPresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**realtimeAnalyticsGetActiveUsers()**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetActiveUsers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**realtimeAnalyticsGetEventThroughput()**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetEventThroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**realtimeAnalyticsGetHistoricalAnalytics()**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetHistoricalAnalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**realtimeAnalyticsGetProject()**](RealtimeAnalyticsApi.md#realtimeAnalyticsGetProject) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |


## `realtimeAnalyticsCheckUserPresence()`

```php
realtimeAnalyticsCheckUserPresence($project_id, $realtime_analytics_check_user_presence_request): \OpenAPI\Client\Model\RealtimeAnalyticsCheckUserPresence200Response
```

Check presence status for users

Returns online status for specified user IDs

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RealtimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$realtime_analytics_check_user_presence_request = {"userIds":["685acbe0e129932fbb7a0fc2","685acbe0e129932fbb7a0fc3"]}; // \OpenAPI\Client\Model\RealtimeAnalyticsCheckUserPresenceRequest | Array of user IDs to check presence for.

try {
    $result = $apiInstance->realtimeAnalyticsCheckUserPresence($project_id, $realtime_analytics_check_user_presence_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealtimeAnalyticsApi->realtimeAnalyticsCheckUserPresence: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **realtime_analytics_check_user_presence_request** | [**\OpenAPI\Client\Model\RealtimeAnalyticsCheckUserPresenceRequest**](../Model/RealtimeAnalyticsCheckUserPresenceRequest.md)| Array of user IDs to check presence for. | |

### Return type

[**\OpenAPI\Client\Model\RealtimeAnalyticsCheckUserPresence200Response**](../Model/RealtimeAnalyticsCheckUserPresence200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `realtimeAnalyticsGetActiveUsers()`

```php
realtimeAnalyticsGetActiveUsers($project_id): \OpenAPI\Client\Model\RealtimeAnalyticsGetActiveUsers200Response
```

Get active users for a project

Returns list of currently connected users

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RealtimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.

try {
    $result = $apiInstance->realtimeAnalyticsGetActiveUsers($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealtimeAnalyticsApi->realtimeAnalyticsGetActiveUsers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |

### Return type

[**\OpenAPI\Client\Model\RealtimeAnalyticsGetActiveUsers200Response**](../Model/RealtimeAnalyticsGetActiveUsers200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `realtimeAnalyticsGetEventThroughput()`

```php
realtimeAnalyticsGetEventThroughput($project_id, $window): \OpenAPI\Client\Model\RealtimeAnalyticsGetEventThroughput200Response
```

Get event throughput metrics

Returns event throughput for a project

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RealtimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$window = 60000; // int | Time window in milliseconds

try {
    $result = $apiInstance->realtimeAnalyticsGetEventThroughput($project_id, $window);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealtimeAnalyticsApi->realtimeAnalyticsGetEventThroughput: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **window** | **int**| Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**\OpenAPI\Client\Model\RealtimeAnalyticsGetEventThroughput200Response**](../Model/RealtimeAnalyticsGetEventThroughput200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `realtimeAnalyticsGetHistoricalAnalytics()`

```php
realtimeAnalyticsGetHistoricalAnalytics($project_id, $period): \OpenAPI\Client\Model\RealtimeAnalyticsGetHistoricalAnalytics200Response
```

Get historical analytics

Returns historical analytics for charting

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RealtimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$period = 'hour'; // string | Time period for historical data

try {
    $result = $apiInstance->realtimeAnalyticsGetHistoricalAnalytics($project_id, $period);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealtimeAnalyticsApi->realtimeAnalyticsGetHistoricalAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **period** | **string**| Time period for historical data | [optional] [default to &#39;hour&#39;] |

### Return type

[**\OpenAPI\Client\Model\RealtimeAnalyticsGetHistoricalAnalytics200Response**](../Model/RealtimeAnalyticsGetHistoricalAnalytics200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `realtimeAnalyticsGetProject()`

```php
realtimeAnalyticsGetProject($project_id): \OpenAPI\Client\Model\RealtimeAnalyticsGetProject200Response
```

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RealtimeAnalyticsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID (MongoDB ObjectId) to get real-time analytics for.

try {
    $result = $apiInstance->realtimeAnalyticsGetProject($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RealtimeAnalyticsApi->realtimeAnalyticsGetProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to get real-time analytics for. | |

### Return type

[**\OpenAPI\Client\Model\RealtimeAnalyticsGetProject200Response**](../Model/RealtimeAnalyticsGetProject200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
