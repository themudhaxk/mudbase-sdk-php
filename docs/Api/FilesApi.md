# OpenAPI\Client\FilesApi

File storage and management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**apiFilesDownloadFileIdGet()**](FilesApi.md#apiFilesDownloadFileIdGet) | **GET** /api/files/download/{fileId} | Get a download URL for a file |
| [**apiFilesLogoRedirectGet()**](FilesApi.md#apiFilesLogoRedirectGet) | **GET** /api/files/logo-redirect | Redirect to an org/project logo&#39;s content |
| [**apiFilesPublicFileIdGet()**](FilesApi.md#apiFilesPublicFileIdGet) | **GET** /api/files/public/{fileId} | Redirect to a public file&#39;s content |
| [**confirmDirectUpload()**](FilesApi.md#confirmDirectUpload) | **POST** /api/files/upload/confirm | Confirm direct upload (scan + finalize metadata) |
| [**deleteFile()**](FilesApi.md#deleteFile) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Delete file |
| [**downloadBucketFile()**](FilesApi.md#downloadBucketFile) | **GET** /api/bucket/files/{fileId}/download | Download file from bucket |
| [**downloadFile()**](FilesApi.md#downloadFile) | **GET** /api/files/{fileId}/download | Generate a presigned URL for downloading a file |
| [**generatePresignedUpload()**](FilesApi.md#generatePresignedUpload) | **POST** /api/files/upload/presigned | Generate a presigned PUT URL for direct browser upload |
| [**generateSignedUrl()**](FilesApi.md#generateSignedUrl) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId}/signed-url | Generate signed URL for file |
| [**getFile()**](FilesApi.md#getFile) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Get file metadata |
| [**listFiles()**](FilesApi.md#listFiles) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | List files in bucket |
| [**uploadFiles()**](FilesApi.md#uploadFiles) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | Upload files to bucket |


## `apiFilesDownloadFileIdGet()`

```php
apiFilesDownloadFileIdGet($file_id, $expires_in): \OpenAPI\Client\Model\ApiFilesDownloadFileIdGet200Response
```

Get a download URL for a file

Returns a URL to download the file. For private files a short-lived signed URL is generated; the lifetime can be tuned per request via the optional expiresIn query parameter (seconds, clamped to a safe server-configured range). For public (public-read) files the permanent world-readable URL is returned with isPublic true and a warning, since signing a public object provides no protection. Accepts a JWT (Bearer) or a project API key.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file_id = 'file_id_example'; // string
$expires_in = 56; // int | Signed-URL lifetime in seconds for private files. Clamped to the server's min/max range; ignored for public files. Defaults to the server's configured expiry.

try {
    $result = $apiInstance->apiFilesDownloadFileIdGet($file_id, $expires_in);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->apiFilesDownloadFileIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**|  | |
| **expires_in** | **int**| Signed-URL lifetime in seconds for private files. Clamped to the server&#39;s min/max range; ignored for public files. Defaults to the server&#39;s configured expiry. | [optional] |

### Return type

[**\OpenAPI\Client\Model\ApiFilesDownloadFileIdGet200Response**](../Model/ApiFilesDownloadFileIdGet200Response.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiFilesLogoRedirectGet()`

```php
apiFilesLogoRedirectGet($key)
```

Redirect to an org/project logo's content

Unauthenticated. Logos are always meant to be public branding assets, but the object storage backend has no per-object ACL, so this route (not the bucket) is what actually serves them - the `key` query param is validated against the exact shape logoStorageService.uploadLogo() produces before signing, so this can never be used to fetch an arbitrary storage key. 302-redirects to a short-lived signed GET url.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$key = 'key_example'; // string

try {
    $apiInstance->apiFilesLogoRedirectGet($key);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->apiFilesLogoRedirectGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key** | **string**|  | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiFilesPublicFileIdGet()`

```php
apiFilesPublicFileIdGet($file_id)
```

Redirect to a public file's content

Unauthenticated. Only serves files with isPublic=true whose upload has been confirmed and whose virus scan came back clean - the object storage backend has no per-object ACL, so this route (not the storage bucket) is what actually decides whether a \"public\" file's bytes are reachable. 302-redirects to a fresh, short-lived (60s) signed GET url so the actual bytes are still served straight off the storage edge.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_id = 'file_id_example'; // string

try {
    $apiInstance->apiFilesPublicFileIdGet($file_id);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->apiFilesPublicFileIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `confirmDirectUpload()`

```php
confirmDirectUpload($confirm_direct_upload_request): \OpenAPI\Client\Model\ConfirmUploadResponse
```

Confirm direct upload (scan + finalize metadata)

After a client uploads directly to object storage using the presigned PUT URL, call this endpoint to have the server scan the object, create the File record, and optionally quarantine if infected.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$confirm_direct_upload_request = {"key":"65a1b2c3d4e5f6789012345a/default/abcd-1234-invoice.pdf","projectId":"65a1b2c3d4e5f6789012345a","originalName":"invoice.pdf","contentType":"application/pdf","size":52312,"isPublic":false}; // \OpenAPI\Client\Model\ConfirmDirectUploadRequest

try {
    $result = $apiInstance->confirmDirectUpload($confirm_direct_upload_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->confirmDirectUpload: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **confirm_direct_upload_request** | [**\OpenAPI\Client\Model\ConfirmDirectUploadRequest**](../Model/ConfirmDirectUploadRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ConfirmUploadResponse**](../Model/ConfirmUploadResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteFile()`

```php
deleteFile($project_id, $bucket_id, $file_id): \OpenAPI\Client\Model\MessageResponse
```

Delete file

Delete a file from a bucket permanently. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$file_id = 'file_id_example'; // string

try {
    $result = $apiInstance->deleteFile($project_id, $bucket_id, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->deleteFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **file_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `downloadBucketFile()`

```php
downloadBucketFile($file_id, $token): \SplFileObject
```

Download file from bucket

Download a file from a bucket. For public files, no authentication is required. For private files, a download token (obtained via signed URL endpoint) is required in the query parameter. Accepts: Token-based authentication via query parameter (for private files), or no authentication (for public files).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$file_id = 685af8b85d73a104065b6a77; // string
$token = 'token_example'; // string

try {
    $result = $apiInstance->downloadBucketFile($file_id, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->downloadBucketFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**|  | |
| **token** | **string**|  | [optional] |

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

## `downloadFile()`

```php
downloadFile($file_id, $token): \OpenAPI\Client\Model\SignedUrlResponse
```

Generate a presigned URL for downloading a file

Returns a time-limited provider-signed URL for direct download. Server enforces RBAC before issuing the URL.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file_id = 'file_id_example'; // string
$token = 'token_example'; // string

try {
    $result = $apiInstance->downloadFile($file_id, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->downloadFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file_id** | **string**|  | |
| **token** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\SignedUrlResponse**](../Model/SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generatePresignedUpload()`

```php
generatePresignedUpload($generate_presigned_upload_request): \OpenAPI\Client\Model\PresignedPostResponse
```

Generate a presigned PUT URL for direct browser upload

Issue a presigned PUT URL for clients to upload directly to object storage. The server stores the issued key with expiry and RBAC is enforced. PUT (not POST) is used because the object storage backend does not implement a POST-based upload API. The client must PUT the file body to `url` with the exact `headers` returned (a Content-Type mismatch fails with SignatureDoesNotMatch). `maxFileUploadBytes` is enforced server-side by `/api/files/upload/confirm` after the upload, not by the presigned URL itself.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$generate_presigned_upload_request = {"projectId":"65a1b2c3d4e5f6789012345a","bucket":"default","originalName":"invoice.pdf","contentType":"application/pdf","isPublic":false}; // \OpenAPI\Client\Model\GeneratePresignedUploadRequest

try {
    $result = $apiInstance->generatePresignedUpload($generate_presigned_upload_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->generatePresignedUpload: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **generate_presigned_upload_request** | [**\OpenAPI\Client\Model\GeneratePresignedUploadRequest**](../Model/GeneratePresignedUploadRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\PresignedPostResponse**](../Model/PresignedPostResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generateSignedUrl()`

```php
generateSignedUrl($project_id, $bucket_id, $file_id, $generate_signed_url_request): \OpenAPI\Client\Model\SignedUrlResponse
```

Generate signed URL for file

Generate a time-limited signed URL for downloading a private file. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$file_id = 'file_id_example'; // string
$generate_signed_url_request = {"expiresIn":3600}; // \OpenAPI\Client\Model\GenerateSignedUrlRequest

try {
    $result = $apiInstance->generateSignedUrl($project_id, $bucket_id, $file_id, $generate_signed_url_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->generateSignedUrl: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **file_id** | **string**|  | |
| **generate_signed_url_request** | [**\OpenAPI\Client\Model\GenerateSignedUrlRequest**](../Model/GenerateSignedUrlRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\SignedUrlResponse**](../Model/SignedUrlResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getFile()`

```php
getFile($project_id, $bucket_id, $file_id): \OpenAPI\Client\Model\FileResponse
```

Get file metadata

Get metadata for a specific file in a bucket. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$file_id = 'file_id_example'; // string

try {
    $result = $apiInstance->getFile($project_id, $bucket_id, $file_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->getFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **file_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\FileResponse**](../Model/FileResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listFiles()`

```php
listFiles($project_id, $bucket_id, $page, $limit, $search, $type): \OpenAPI\Client\Model\FileListResponse
```

List files in bucket

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$page = 1; // int
$limit = 20; // int
$search = 'search_example'; // string
$type = 'type_example'; // string

try {
    $result = $apiInstance->listFiles($project_id, $bucket_id, $page, $limit, $search, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->listFiles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **search** | **string**|  | [optional] |
| **type** | **string**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\FileListResponse**](../Model/FileListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `uploadFiles()`

```php
uploadFiles($project_id, $bucket_id, $files): \OpenAPI\Client\Model\FileUploadResponse
```

Upload files to bucket

Upload one or more files to a storage bucket using multipart/form-data. Per-file size is limited by the org plan (`maxFileUploadBytes`) and bucket `maxFileSize`, whichever is stricter. Exceeding the limit returns **413**. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\FilesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$bucket_id = 'bucket_id_example'; // string
$files = array('/path/to/file.txt'); // \SplFileObject[]

try {
    $result = $apiInstance->uploadFiles($project_id, $bucket_id, $files);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FilesApi->uploadFiles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **bucket_id** | **string**|  | |
| **files** | **\SplFileObject[]**|  | |

### Return type

[**\OpenAPI\Client\Model\FileUploadResponse**](../Model/FileUploadResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
