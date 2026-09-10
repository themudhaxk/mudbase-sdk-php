# MudbaseSDK\RoleElevationApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**approveRoleElevation()**](RoleElevationApi.md#approveRoleElevation) | **POST** /api/orgs/{orgId}/role-elevation/{requestId}/approve | Approve/reject role elevation request (admin only) |
| [**getPendingRoleElevationRequests()**](RoleElevationApi.md#getPendingRoleElevationRequests) | **GET** /api/orgs/{orgId}/role-elevation/pending | Get pending role elevation requests (admin only) |
| [**getRoleElevationStatus()**](RoleElevationApi.md#getRoleElevationStatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**requestRoleElevation()**](RoleElevationApi.md#requestRoleElevation) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**uploadVerificationDocuments()**](RoleElevationApi.md#uploadVerificationDocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |


## `approveRoleElevation()`

```php
approveRoleElevation($org_id, $request_id, $approve_role_elevation_request): \MudbaseSDK\Model\ApproveRoleElevation200Response
```

Approve/reject role elevation request (admin only)

Admin approves or rejects a role elevation request

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$request_id = 'request_id_example'; // string
$approve_role_elevation_request = {"approved":true,"reason":"All requirements met"}; // \MudbaseSDK\Model\ApproveRoleElevationRequest

try {
    $result = $apiInstance->approveRoleElevation($org_id, $request_id, $approve_role_elevation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->approveRoleElevation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **request_id** | **string**|  | |
| **approve_role_elevation_request** | [**\MudbaseSDK\Model\ApproveRoleElevationRequest**](../Model/ApproveRoleElevationRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\ApproveRoleElevation200Response**](../Model/ApproveRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPendingRoleElevationRequests()`

```php
getPendingRoleElevationRequests($org_id, $status, $page, $limit): \MudbaseSDK\Model\GetPendingRoleElevationRequests200Response
```

Get pending role elevation requests (admin only)

Get all pending role elevation requests requiring admin approval

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$status = 'pending'; // string
$page = 1; // int
$limit = 50; // int

try {
    $result = $apiInstance->getPendingRoleElevationRequests($org_id, $status, $page, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->getPendingRoleElevationRequests: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **status** | **string**|  | [optional] [default to &#39;pending&#39;] |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\MudbaseSDK\Model\GetPendingRoleElevationRequests200Response**](../Model/GetPendingRoleElevationRequests200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getRoleElevationStatus()`

```php
getRoleElevationStatus($project_id, $role_slug): \MudbaseSDK\Model\GetRoleElevationStatus200Response
```

Get role elevation status

Get status of pending role elevation requests for current user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$role_slug = 'role_slug_example'; // string

try {
    $result = $apiInstance->getRoleElevationStatus($project_id, $role_slug);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->getRoleElevationStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **role_slug** | **string**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\GetRoleElevationStatus200Response**](../Model/GetRoleElevationStatus200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestRoleElevation()`

```php
requestRoleElevation($project_id, $request_role_elevation_request): \MudbaseSDK\Model\RequestRoleElevation200Response
```

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$request_role_elevation_request = {"roleSlug":"seller"}; // \MudbaseSDK\Model\RequestRoleElevationRequest

try {
    $result = $apiInstance->requestRoleElevation($project_id, $request_role_elevation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->requestRoleElevation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **request_role_elevation_request** | [**\MudbaseSDK\Model\RequestRoleElevationRequest**](../Model/RequestRoleElevationRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\RequestRoleElevation200Response**](../Model/RequestRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `uploadVerificationDocuments()`

```php
uploadVerificationDocuments($project_id, $upload_verification_documents_request)
```

Upload verification documents

Upload KYC/verification documents for role elevation

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\RoleElevationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$upload_verification_documents_request = {"roleSlug":"seller","documents":[{"type":"id","url":"https://example.com/id.pdf"}]}; // \MudbaseSDK\Model\UploadVerificationDocumentsRequest

try {
    $apiInstance->uploadVerificationDocuments($project_id, $upload_verification_documents_request);
} catch (Exception $e) {
    echo 'Exception when calling RoleElevationApi->uploadVerificationDocuments: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **upload_verification_documents_request** | [**\MudbaseSDK\Model\UploadVerificationDocumentsRequest**](../Model/UploadVerificationDocumentsRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
