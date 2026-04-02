# OpenAPI\Client\RoleElevationApi

Configurable role elevation with admin approval support

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**roleElevationGetStatus()**](RoleElevationApi.md#roleElevationGetStatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**roleElevationRequest()**](RoleElevationApi.md#roleElevationRequest) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**roleElevationUploadDocuments()**](RoleElevationApi.md#roleElevationUploadDocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |


## `roleElevationGetStatus()`

```php
roleElevationGetStatus($project_id, $role_slug): \OpenAPI\Client\Model\RoleElevationGetStatus200Response
```

Get role elevation status

Get status of pending role elevation requests for current user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$role_slug = 'role_slug_example'; // string | Optional filter by role slug.

try {
    $result = $apiInstance->roleElevationGetStatus($project_id, $role_slug);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->roleElevationGetStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_slug** | **string**| Optional filter by role slug. | [optional] |

### Return type

[**\OpenAPI\Client\Model\RoleElevationGetStatus200Response**](../Model/RoleElevationGetStatus200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `roleElevationRequest()`

```php
roleElevationRequest($project_id, $role_elevation_request_request): \OpenAPI\Client\Model\RoleElevationRequest200Response
```

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$role_elevation_request_request = {"roleSlug":"seller"}; // \OpenAPI\Client\Model\RoleElevationRequestRequest | Role slug to request elevation to (e.g. a higher-privilege role you configured).

try {
    $result = $apiInstance->roleElevationRequest($project_id, $role_elevation_request_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->roleElevationRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_elevation_request_request** | [**\OpenAPI\Client\Model\RoleElevationRequestRequest**](../Model/RoleElevationRequestRequest.md)| Role slug to request elevation to (e.g. a higher-privilege role you configured). | |

### Return type

[**\OpenAPI\Client\Model\RoleElevationRequest200Response**](../Model/RoleElevationRequest200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `roleElevationUploadDocuments()`

```php
roleElevationUploadDocuments($project_id, $role_elevation_upload_documents_request)
```

Upload verification documents

Upload KYC/verification documents for role elevation

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$role_elevation_upload_documents_request = {"roleSlug":"seller","documents":[{"type":"id","url":"https://example.com/id.pdf"}]}; // \OpenAPI\Client\Model\RoleElevationUploadDocumentsRequest | Role slug and array of document objects (type, url).

try {
    $apiInstance->roleElevationUploadDocuments($project_id, $role_elevation_upload_documents_request);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->roleElevationUploadDocuments: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_elevation_upload_documents_request** | [**\OpenAPI\Client\Model\RoleElevationUploadDocumentsRequest**](../Model/RoleElevationUploadDocumentsRequest.md)| Role slug and array of document objects (type, url). | |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
