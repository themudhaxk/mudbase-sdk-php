# OpenAPI\Client\SearchApi

Full-text search capabilities

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getSearchAnalytics()**](SearchApi.md#getSearchAnalytics) | **GET** /api/search/projects/{projectId}/search/analytics | Get search analytics |
| [**getSearchSuggestions()**](SearchApi.md#getSearchSuggestions) | **GET** /api/search/projects/{projectId}/search/suggestions | Get search suggestions |
| [**searchData()**](SearchApi.md#searchData) | **GET** /api/search/projects/{projectId}/search | Full-text search |


## `getSearchAnalytics()`

```php
getSearchAnalytics($project_id, $timeframe): \OpenAPI\Client\Model\GetSearchAnalytics200Response
```

Get search analytics

Get search analytics including top queries, search volume, and performance metrics. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$timeframe = '7d'; // string

try {
    $result = $apiInstance->getSearchAnalytics($project_id, $timeframe);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->getSearchAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **timeframe** | **string**|  | [optional] [default to &#39;7d&#39;] |

### Return type

[**\OpenAPI\Client\Model\GetSearchAnalytics200Response**](../Model/GetSearchAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSearchSuggestions()`

```php
getSearchSuggestions($project_id, $q, $limit): \OpenAPI\Client\Model\GetSearchSuggestions200Response
```

Get search suggestions

Get search query suggestions based on partial input. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$q = 'q_example'; // string
$limit = 10; // int

try {
    $result = $apiInstance->getSearchSuggestions($project_id, $q, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->getSearchSuggestions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **q** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 10] |

### Return type

[**\OpenAPI\Client\Model\GetSearchSuggestions200Response**](../Model/GetSearchSuggestions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `searchData()`

```php
searchData($project_id, $q, $collections, $fields, $limit, $page): \OpenAPI\Client\Model\SearchResponse
```

Full-text search

Perform full-text search across collections in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\SearchApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$q = 'q_example'; // string
$collections = 'collections_example'; // string
$fields = 'fields_example'; // string
$limit = 20; // int
$page = 1; // int

try {
    $result = $apiInstance->searchData($project_id, $q, $collections, $fields, $limit, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SearchApi->searchData: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **q** | **string**|  | |
| **collections** | **string**|  | [optional] |
| **fields** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 20] |
| **page** | **int**|  | [optional] [default to 1] |

### Return type

[**\OpenAPI\Client\Model\SearchResponse**](../Model/SearchResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
