# OpenAPI\Client\StorageApi

Buckets and file storage (buckets, files, upload, signed URLs)

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**storageConfirmUpload()**](StorageApi.md#storageConfirmUpload) | **POST** /api/files/upload/confirm | Confirm direct upload (scan + finalize metadata) |
| [**storageCreateBucket()**](StorageApi.md#storageCreateBucket) | **POST** /api/bucket/projects/{projectId}/buckets | Create a new bucket |
| [**storageDeleteBucket()**](StorageApi.md#storageDeleteBucket) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId} | Delete bucket |
| [**storageDeleteFile()**](StorageApi.md#storageDeleteFile) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Delete file |
| [**storageDownloadBucketFile()**](StorageApi.md#storageDownloadBucketFile) | **GET** /api/bucket/files/{fileId}/download | Download file from bucket |
| [**storageDownloadFile()**](StorageApi.md#storageDownloadFile) | **GET** /api/files/{fileId}/download | Generate a presigned URL for downloading a file |
| [**storageGetBucket()**](StorageApi.md#storageGetBucket) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId} | Get bucket details |
| [**storageGetFile()**](StorageApi.md#storageGetFile) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Get file metadata |
| [**storageGetPresignedUpload()**](StorageApi.md#storageGetPresignedUpload) | **POST** /api/files/upload/presigned | Generate presigned POST data for direct browser upload |
| [**storageGetSignedUrl()**](StorageApi.md#storageGetSignedUrl) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId}/signed-url | Generate signed URL for file |
| [**storageListBuckets()**](StorageApi.md#storageListBuckets) | **GET** /api/bucket/projects/{projectId}/buckets | List buckets in a project |
| [**storageListFiles()**](StorageApi.md#storageListFiles) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | List files in bucket |
| [**storageUpdateBucket()**](StorageApi.md#storageUpdateBucket) | **PATCH** /api/bucket/projects/{projectId}/buckets/{bucketId} | Update bucket |
| [**storageUploadFiles()**](StorageApi.md#storageUploadFiles) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | Upload files to bucket |


## `storageConfirmUpload()`

```php
storageConfirmUpload($storage_confirm_upload_request): \OpenAPI\Client\Model\ConfirmUploadResponse
```

Confirm direct upload (scan + finalize metadata)

After a client uploads directly to S3 using the presigned POST, call this endpoint to have the server scan the object, create the File record, and optionally quarantine if infected.

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$storage_confirm_upload_request = {"key":"65a1b2c3d4e5f6789012345a/default/abcd-1234-invoice.pdf","projectId":"65a1b2c3d4e5f6789012345a","originalName":"invoice.pdf","contentType":"application/pdf","size":52312,"isPublic":false}; // \OpenAPI\Client\Model\StorageConfirmUploadRequest | S3 key from presigned response, projectId, and optional originalName, contentType, size, bucket, isPublic.

try {
    $result = $apiInstance->storageConfirmUpload($storage_confirm_upload_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageConfirmUpload: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **storage_confirm_upload_request** | [**\OpenAPI\Client\Model\StorageConfirmUploadRequest**](../Model/StorageConfirmUploadRequest.md)| S3 key from presigned response, projectId, and optional originalName, contentType, size, bucket, isPublic. | |

### Return type

[**\OpenAPI\Client\Model\ConfirmUploadResponse**](../Model/ConfirmUploadResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageCreateBucket()`

```php
storageCreateBucket($project_id, $create_bucket_request): \OpenAPI\Client\Model\BucketResponse
```

Create a new bucket

Create a new storage bucket in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$create_bucket_request = {"name":"my-bucket","isPublic":false,"settings":{}}; // \OpenAPI\Client\Model\CreateBucketRequest | Bucket name, isPublic flag, and optional settings.

try {
    $result = $apiInstance->storageCreateBucket($project_id, $create_bucket_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageCreateBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **create_bucket_request** | [**\OpenAPI\Client\Model\CreateBucketRequest**](../Model/CreateBucketRequest.md)| Bucket name, isPublic flag, and optional settings. | |

### Return type

[**\OpenAPI\Client\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageDeleteBucket()`

```php
storageDeleteBucket($project_id, $bucket_id): \OpenAPI\Client\Model\MessageResponse
```

Delete bucket

Delete a storage bucket permanently. This is a destructive operation that will also delete all files in the bucket. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.

try {
    $result = $apiInstance->storageDeleteBucket($project_id, $bucket_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageDeleteBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageDeleteFile()`

```php
storageDeleteFile($project_id, $bucket_id, $file_id): \OpenAPI\Client\Model\MessageResponse
```

Delete file

Delete a file from a bucket permanently. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$file_id = 'file_id_example'; // string | File ID.

try {
    $result = $apiInstance->storageDeleteFile($project_id, $bucket_id, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageDeleteFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **file_id** | **string**| File ID. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageDownloadBucketFile()`

```php
storageDownloadBucketFile($file_id, $token): \SplFileObject
```

Download file from bucket

Download a file from a bucket. For public files, no authentication is required. For private files, a download token (obtained via signed URL endpoint) is required in the query parameter. Accepts: Token-based authentication via query parameter (for private files), or no authentication (for public files).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_id = 685af8b85d73a104065b6a77; // string | File ID to download.
$token = 'token_example'; // string | Download token for private files (from signed URL endpoint).

try {
    $result = $apiInstance->storageDownloadBucketFile($file_id, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageDownloadBucketFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**| File ID to download. | |
| **token** | **string**| Download token for private files (from signed URL endpoint). | [optional] |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/octet-stream`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageDownloadFile()`

```php
storageDownloadFile($file_id, $token): \OpenAPI\Client\Model\SignedUrlResponse
```

Generate a presigned URL for downloading a file

Returns a time-limited provider-signed URL (S3) for direct download. Server enforces RBAC before issuing the URL.

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file_id = 'file_id_example'; // string | File ID.
$token = 'token_example'; // string | Optional one-time download token (if provided by upload flow).

try {
    $result = $apiInstance->storageDownloadFile($file_id, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageDownloadFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**| File ID. | |
| **token** | **string**| Optional one-time download token (if provided by upload flow). | [optional] |

### Return type

[**\OpenAPI\Client\Model\SignedUrlResponse**](../Model/SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageGetBucket()`

```php
storageGetBucket($project_id, $bucket_id): \OpenAPI\Client\Model\BucketResponse
```

Get bucket details

Retrieve metadata and configuration for a single storage bucket, including name, project, public/private status, and settings. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.

try {
    $result = $apiInstance->storageGetBucket($project_id, $bucket_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageGetBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |

### Return type

[**\OpenAPI\Client\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageGetFile()`

```php
storageGetFile($project_id, $bucket_id, $file_id): \OpenAPI\Client\Model\FileResponse
```

Get file metadata

Get metadata for a specific file in a bucket. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$file_id = 'file_id_example'; // string | File ID.

try {
    $result = $apiInstance->storageGetFile($project_id, $bucket_id, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageGetFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **file_id** | **string**| File ID. | |

### Return type

[**\OpenAPI\Client\Model\FileResponse**](../Model/FileResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageGetPresignedUpload()`

```php
storageGetPresignedUpload($storage_get_presigned_upload_request): \OpenAPI\Client\Model\PresignedPostResponse
```

Generate presigned POST data for direct browser upload

Issue a presigned POST (fields + url) for clients to upload directly to S3. The server stores the issued key with expiry and RBAC is enforced.

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$storage_get_presigned_upload_request = {"projectId":"65a1b2c3d4e5f6789012345a","bucket":"default","originalName":"invoice.pdf","contentType":"application/pdf","isPublic":false}; // \OpenAPI\Client\Model\StorageGetPresignedUploadRequest | projectId, originalName, optional bucket, contentType, isPublic.

try {
    $result = $apiInstance->storageGetPresignedUpload($storage_get_presigned_upload_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageGetPresignedUpload: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **storage_get_presigned_upload_request** | [**\OpenAPI\Client\Model\StorageGetPresignedUploadRequest**](../Model/StorageGetPresignedUploadRequest.md)| projectId, originalName, optional bucket, contentType, isPublic. | |

### Return type

[**\OpenAPI\Client\Model\PresignedPostResponse**](../Model/PresignedPostResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageGetSignedUrl()`

```php
storageGetSignedUrl($project_id, $bucket_id, $file_id, $storage_get_signed_url_request): \OpenAPI\Client\Model\SignedUrlResponse
```

Generate signed URL for file

Generate a time-limited signed URL for downloading a private file. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$file_id = 'file_id_example'; // string | File ID.
$storage_get_signed_url_request = {"expiresIn":3600}; // \OpenAPI\Client\Model\StorageGetSignedUrlRequest | Optional expiresIn (seconds) for the signed URL.

try {
    $result = $apiInstance->storageGetSignedUrl($project_id, $bucket_id, $file_id, $storage_get_signed_url_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageGetSignedUrl: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **file_id** | **string**| File ID. | |
| **storage_get_signed_url_request** | [**\OpenAPI\Client\Model\StorageGetSignedUrlRequest**](../Model/StorageGetSignedUrlRequest.md)| Optional expiresIn (seconds) for the signed URL. | [optional] |

### Return type

[**\OpenAPI\Client\Model\SignedUrlResponse**](../Model/SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageListBuckets()`

```php
storageListBuckets($project_id, $page, $limit, $search): \OpenAPI\Client\Model\BucketListResponse
```

List buckets in a project

List all storage buckets in a project with pagination and search. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$page = 1; // int | Page number (1-based).
$limit = 20; // int | Number of buckets per page.
$search = 'search_example'; // string | Search by bucket name.

try {
    $result = $apiInstance->storageListBuckets($project_id, $page, $limit, $search);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageListBuckets: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of buckets per page. | [optional] [default to 20] |
| **search** | **string**| Search by bucket name. | [optional] |

### Return type

[**\OpenAPI\Client\Model\BucketListResponse**](../Model/BucketListResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageListFiles()`

```php
storageListFiles($project_id, $bucket_id, $page, $limit, $search, $type): \OpenAPI\Client\Model\FileListResponse
```

List files in bucket

List files in a bucket with pagination, search, and optional type filter. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$page = 1; // int | Page number (1-based).
$limit = 20; // int | Number of files per page.
$search = 'search_example'; // string | Search by filename.
$type = 'type_example'; // string | Filter by MIME type or file type.

try {
    $result = $apiInstance->storageListFiles($project_id, $bucket_id, $page, $limit, $search, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageListFiles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of files per page. | [optional] [default to 20] |
| **search** | **string**| Search by filename. | [optional] |
| **type** | **string**| Filter by MIME type or file type. | [optional] |

### Return type

[**\OpenAPI\Client\Model\FileListResponse**](../Model/FileListResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageUpdateBucket()`

```php
storageUpdateBucket($project_id, $bucket_id, $update_bucket_request): \OpenAPI\Client\Model\BucketResponse
```

Update bucket

Update bucket configuration (name, public/private status, settings). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$update_bucket_request = {"name":"my-bucket-updated","isPublic":true,"settings":{}}; // \OpenAPI\Client\Model\UpdateBucketRequest | Fields to update (name, isPublic, settings).

try {
    $result = $apiInstance->storageUpdateBucket($project_id, $bucket_id, $update_bucket_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageUpdateBucket: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **update_bucket_request** | [**\OpenAPI\Client\Model\UpdateBucketRequest**](../Model/UpdateBucketRequest.md)| Fields to update (name, isPublic, settings). | |

### Return type

[**\OpenAPI\Client\Model\BucketResponse**](../Model/BucketResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `storageUploadFiles()`

```php
storageUploadFiles($project_id, $bucket_id, $upload_files_to_bucket_request): \OpenAPI\Client\Model\FileUploadResponse
```

Upload files to bucket

Upload one or more files to a storage bucket using multipart/form-data. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

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


$apiInstance = new OpenAPI\Client\Api\StorageApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$bucket_id = 'bucket_id_example'; // string | Bucket ID.
$upload_files_to_bucket_request = new \OpenAPI\Client\Model\UploadFilesToBucketRequest(); // \OpenAPI\Client\Model\UploadFilesToBucketRequest | Use multipart/form-data for file upload (files required; optional folder, tags). application/json uses the same schema for metadata-only or tooling that prefers JSON.

try {
    $result = $apiInstance->storageUploadFiles($project_id, $bucket_id, $upload_files_to_bucket_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling StorageApi->storageUploadFiles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **bucket_id** | **string**| Bucket ID. | |
| **upload_files_to_bucket_request** | [**\OpenAPI\Client\Model\UploadFilesToBucketRequest**](../Model/UploadFilesToBucketRequest.md)| Use multipart/form-data for file upload (files required; optional folder, tags). application/json uses the same schema for metadata-only or tooling that prefers JSON. | |

### Return type

[**\OpenAPI\Client\Model\FileUploadResponse**](../Model/FileUploadResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`, `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
