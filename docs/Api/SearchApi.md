# OpenAPI\Client\SearchApi

Full-text search capabilities

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**searchGetAnalytics()**](SearchApi.md#searchGetAnalytics) | **GET** /api/search/projects/{projectId}/search/analytics | Get search analytics |
| [**searchGetSuggestions()**](SearchApi.md#searchGetSuggestions) | **GET** /api/search/projects/{projectId}/search/suggestions | Get search suggestions |
| [**searchSearch()**](SearchApi.md#searchSearch) | **GET** /api/search/projects/{projectId}/search | Full-text search |


## `searchGetAnalytics()`

```php
searchGetAnalytics($project_id, $timeframe): \OpenAPI\Client\Model\SearchGetAnalytics200Response
```

Get search analytics

Get search analytics including top queries, search volume, and performance metrics. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID (MongoDB ObjectId) to get analytics for.
$timeframe = '7d'; // string | Timeframe for analytics (1d, 7d, or 30d).

try {
    $result = $apiInstance->searchGetAnalytics($project_id, $timeframe);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->searchGetAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to get analytics for. | |
| **timeframe** | **string**| Timeframe for analytics (1d, 7d, or 30d). | [optional] [default to &#39;7d&#39;] |

### Return type

[**\OpenAPI\Client\Model\SearchGetAnalytics200Response**](../Model/SearchGetAnalytics200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `searchGetSuggestions()`

```php
searchGetSuggestions($project_id, $q, $limit): \OpenAPI\Client\Model\SearchGetSuggestions200Response
```

Get search suggestions

Get search query suggestions based on partial input. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID (MongoDB ObjectId) to get suggestions for.
$q = 'q_example'; // string | Partial search query (min 2 characters, max 50); suggestions are based on past queries and indexed content.
$limit = 10; // int | Maximum number of suggestions to return (1–20).

try {
    $result = $apiInstance->searchGetSuggestions($project_id, $q, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->searchGetSuggestions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to get suggestions for. | |
| **q** | **string**| Partial search query (min 2 characters, max 50); suggestions are based on past queries and indexed content. | |
| **limit** | **int**| Maximum number of suggestions to return (1–20). | [optional] [default to 10] |

### Return type

[**\OpenAPI\Client\Model\SearchGetSuggestions200Response**](../Model/SearchGetSuggestions200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `searchSearch()`

```php
searchSearch($project_id, $q, $collections, $fields, $limit, $page): \OpenAPI\Client\Model\SearchResponse
```

Full-text search

Perform full-text search across collections in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) to search within.
$q = 'q_example'; // string | Full-text search query string.
$collections = 'collections_example'; // string | Comma-separated collection slugs or IDs to limit search scope.
$fields = 'fields_example'; // string | Comma-separated field names to search or return in highlights.
$limit = 20; // int | Maximum number of results to return per page.
$page = 1; // int | Page number for pagination (1-based).

try {
    $result = $apiInstance->searchSearch($project_id, $q, $collections, $fields, $limit, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->searchSearch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) to search within. | |
| **q** | **string**| Full-text search query string. | |
| **collections** | **string**| Comma-separated collection slugs or IDs to limit search scope. | [optional] |
| **fields** | **string**| Comma-separated field names to search or return in highlights. | [optional] |
| **limit** | **int**| Maximum number of results to return per page. | [optional] [default to 20] |
| **page** | **int**| Page number for pagination (1-based). | [optional] [default to 1] |

### Return type

[**\OpenAPI\Client\Model\SearchResponse**](../Model/SearchResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
