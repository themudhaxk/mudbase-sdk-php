# OpenAPI\Client\UsageApi

Project-level usage and analytics. Use /api/usage/projects/{projectId} and /api/usage/trends. Org usage and overage are in the dashboard.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**usageGetProject()**](UsageApi.md#usageGetProject) | **GET** /api/usage/projects/{projectId} | Get project usage |
| [**usageGetTrends()**](UsageApi.md#usageGetTrends) | **GET** /api/usage/trends | Get usage trends |


## `usageGetProject()`

```php
usageGetProject($project_id, $period): \OpenAPI\Client\Model\ProjectUsageStatsResponse
```

Get project usage

Get usage statistics for a project (API calls, storage, bandwidth, database operations). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) to get usage for.
$period = 'month'; // string | Aggregation period for usage (day, week, or month).

try {
    $result = $apiInstance->usageGetProject($project_id, $period);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsageApi->usageGetProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to get usage for. | |
| **period** | **string**| Aggregation period for usage (day, week, or month). | [optional] [default to &#39;month&#39;] |

### Return type

[**\OpenAPI\Client\Model\ProjectUsageStatsResponse**](../Model/ProjectUsageStatsResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usageGetTrends()`

```php
usageGetTrends($days): \OpenAPI\Client\Model\UsageTrendsResponse
```

Get usage trends

Get usage trends over time for the authenticated organization or project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$days = 30; // int | Number of days of trend data to return (default 30).

try {
    $result = $apiInstance->usageGetTrends($days);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsageApi->usageGetTrends: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **days** | **int**| Number of days of trend data to return (default 30). | [optional] [default to 30] |

### Return type

[**\OpenAPI\Client\Model\UsageTrendsResponse**](../Model/UsageTrendsResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
