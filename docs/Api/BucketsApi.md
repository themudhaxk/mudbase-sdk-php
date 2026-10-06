# MudbaseSDK\BucketsApi

Bucket management operations

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createBucket()**](BucketsApi.md#createBucket) | **POST** /api/bucket/projects/{projectId}/buckets | Create a new bucket |
| [**deleteBucket()**](BucketsApi.md#deleteBucket) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId} | Delete bucket |
| [**getBucket()**](BucketsApi.md#getBucket) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId} | Get bucket details |
| [**listBuckets()**](BucketsApi.md#listBuckets) | **GET** /api/bucket/projects/{projectId}/buckets | List buckets in a project |
| [**updateBucket()**](BucketsApi.md#updateBucket) | **PATCH** /api/bucket/projects/{projectId}/buckets/{bucketId} | Update bucket |


## `createBucket()`

```php
createBucket($project_id, $create_bucket_request): \MudbaseSDK\Model\BucketResponse
```

Create a new bucket

Create a new storage bucket in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

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


$apiInstance = new MudbaseSDK\Api\BucketsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_bucket_request = {"name":"my-bucket","isPublic":false,"settings":{}}; // \MudbaseSDK\Model\CreateBucketRequest

try {
    $result = $apiInstance->createBucket($project_id, $create_bucket_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BucketsApi->createBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **create_bucket_request** | [**\MudbaseSDK\Model\CreateBucketRequest**](../Model/CreateBucketRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteBucket()`

```php
deleteBucket($project_id, $bucket_id): \MudbaseSDK\Model\MessageResponse
```

Delete bucket

Delete a storage bucket permanently. This is a destructive operation that will also delete all files in the bucket. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BucketsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string

try {
    $result = $apiInstance->deleteBucket($project_id, $bucket_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BucketsApi->deleteBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getBucket()`

```php
getBucket($project_id, $bucket_id): \MudbaseSDK\Model\BucketResponse
```

Get bucket details

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


$apiInstance = new MudbaseSDK\Api\BucketsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string

try {
    $result = $apiInstance->getBucket($project_id, $bucket_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BucketsApi->getBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listBuckets()`

```php
listBuckets($project_id, $page, $limit, $search): \MudbaseSDK\Model\BucketListResponse
```

List buckets in a project

List all storage buckets in a project with pagination and search. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BucketsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$page = 1; // int
$limit = 20; // int
$search = 'search_example'; // string

try {
    $result = $apiInstance->listBuckets($project_id, $page, $limit, $search);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BucketsApi->listBuckets: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **search** | **string**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\BucketListResponse**](../Model/BucketListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateBucket()`

```php
updateBucket($project_id, $bucket_id, $update_bucket_request): \MudbaseSDK\Model\BucketResponse
```

Update bucket

Update bucket configuration (name, public/private status, settings). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\BucketsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$update_bucket_request = {"name":"my-bucket-updated","isPublic":true,"settings":{}}; // \MudbaseSDK\Model\UpdateBucketRequest

try {
    $result = $apiInstance->updateBucket($project_id, $bucket_id, $update_bucket_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BucketsApi->updateBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **update_bucket_request** | [**\MudbaseSDK\Model\UpdateBucketRequest**](../Model/UpdateBucketRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
