# OpenAPI\Client\WebhooksApi

Webhook configuration and logs

All URIs are relative to https://cloud.dev.mudbase, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**webhooksGetStats()**](WebhooksApi.md#webhooksGetStats) | **GET** /api/webhooks/stats | Get webhook statistics |


## `webhooksGetStats()`

```php
webhooksGetStats($project_id, $days): \OpenAPI\Client\Model\WebhookStatsResponse
```

Get webhook statistics

Get webhook delivery statistics including success rate, total deliveries, and breakdown by status. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID to filter stats (optional).
$days = 7; // int | Number of days to include in the stats window.

try {
    $result = $apiInstance->webhooksGetStats($project_id, $days);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->webhooksGetStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID to filter stats (optional). | [optional] |
| **days** | **int**| Number of days to include in the stats window. | [optional] [default to 7] |

### Return type

[**\OpenAPI\Client\Model\WebhookStatsResponse**](../Model/WebhookStatsResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
