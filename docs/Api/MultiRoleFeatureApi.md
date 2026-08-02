# OpenAPI\Client\MultiRoleFeatureApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addCustomRole()**](MultiRoleFeatureApi.md#addCustomRole) | **POST** /api/projects/{projectId}/multi-role/roles | Add custom role |
| [**applyRoleFeaturePreset()**](MultiRoleFeatureApi.md#applyRoleFeaturePreset) | **POST** /api/projects/{projectId}/multi-role/roles/{roleSlug}/apply-preset | Apply Admin / User / Viewer feature permission preset |
| [**getAvailableRoles()**](MultiRoleFeatureApi.md#getAvailableRoles) | **GET** /api/projects/{projectId}/multi-role/roles/available | Get available roles for signup |
| [**getMultiRoleConfig()**](MultiRoleFeatureApi.md#getMultiRoleConfig) | **GET** /api/projects/{projectId}/multi-role | Get multi-role feature configuration |
| [**getPermissionsMatrix()**](MultiRoleFeatureApi.md#getPermissionsMatrix) | **GET** /api/projects/{projectId}/permissions-matrix | Get permissions matrix (collections + featurePermissions) |
| [**oauthSignupWithRole()**](MultiRoleFeatureApi.md#oauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**registerWithRole()**](MultiRoleFeatureApi.md#registerWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |
| [**simulateAppPermissions()**](MultiRoleFeatureApi.md#simulateAppPermissions) | **POST** /api/projects/{projectId}/multi-role/simulate-permissions | Simulate app-role feature permission for a path |
| [**toggleRole()**](MultiRoleFeatureApi.md#toggleRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/toggle | Toggle role on/off |
| [**updateCollectionPermissions()**](MultiRoleFeatureApi.md#updateCollectionPermissions) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/collections/{collectionId}/permissions | Update collection permissions for a role |
| [**updateMultiRoleSettings()**](MultiRoleFeatureApi.md#updateMultiRoleSettings) | **PATCH** /api/projects/{projectId}/multi-role/settings | Update multi-role feature settings |
| [**updateProjectRole()**](MultiRoleFeatureApi.md#updateProjectRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug} | Update role configuration |


## `addCustomRole()`

```php
addCustomRole($project_id, $add_custom_role_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Add custom role

Add a custom role to a project with specific permissions and signup endpoint. Optional **`featurePermissions`** must align with app JWT gates — see `components/schemas/AppRoleFeaturePermissions` and `services/appRoleFeatureMap.js`. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$add_custom_role_request = {"slug":"seller","name":"Seller","description":"Seller role with CRUD on seller-owned collections","signupEndpoint":"seller","requiresApproval":false,"requiresPayment":false,"requiresKYC":false,"metadata":{"notes":"Example role for API integration tests"},"defaultPermissions":[{"resource":"project","actions":["read"]},{"resource":"data","actions":["read","create"]}],"collectionPermissions":{"listings":["create","read","update","delete"],"orders":{"actions":["create","read"],"conditions":{"status":"active"}}},"featurePermissions":{"messaging":{"email":true,"sms":true,"push":true,"history":true,"stats":true},"integration":{"read":true,"create":true,"update":true,"delete":false,"execute":true,"test":true,"export":true,"read_usage":true},"functions":{"create":true,"read":true,"update":true,"delete":false,"execute":true,"simulate":true},"data":{"create":true,"read":true,"update":true,"delete":false},"search":{"query":true,"suggestions":true,"read_analytics":true},"usage":{"read":true},"storage":{"read":true,"create":true,"update":true,"delete":false,"upload":true},"chat":{"read":true,"create":true,"update":true,"delete":false},"realtime":{"read_analytics":true,"read_active_users":true,"presence":true,"read_throughput":true,"read_history":true},"roleElevation":{"request":true,"status":true,"documents":true},"webhooks":{"config_read":true,"config_update":true,"test_transformation":true}}}; // \OpenAPI\Client\Model\AddCustomRoleRequest

try {
    $result = $apiInstance->addCustomRole($project_id, $add_custom_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->addCustomRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **add_custom_role_request** | [**\OpenAPI\Client\Model\AddCustomRoleRequest**](../Model/AddCustomRoleRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `applyRoleFeaturePreset()`

```php
applyRoleFeaturePreset($project_id, $role_slug, $apply_role_feature_preset_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Apply Admin / User / Viewer feature permission preset

Sets `featurePermissions` on the role from a bundled preset (`admin`, `user`, `viewer`). Does not change collection CRUD or `dataScope`; use collection permission APIs for those.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$role_slug = 'role_slug_example'; // string
$apply_role_feature_preset_request = {"preset":"admin"}; // \OpenAPI\Client\Model\ApplyRoleFeaturePresetRequest

try {
    $result = $apiInstance->applyRoleFeaturePreset($project_id, $role_slug, $apply_role_feature_preset_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->applyRoleFeaturePreset: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **role_slug** | **string**|  | |
| **apply_role_feature_preset_request** | [**\OpenAPI\Client\Model\ApplyRoleFeaturePresetRequest**](../Model/ApplyRoleFeaturePresetRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getAvailableRoles()`

```php
getAvailableRoles($project_id): \OpenAPI\Client\Model\GetAvailableRoles200Response
```

Get available roles for signup

Get all available roles for user signup in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getAvailableRoles($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->getAvailableRoles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetAvailableRoles200Response**](../Model/GetAvailableRoles200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMultiRoleConfig()`

```php
getMultiRoleConfig($project_id): \OpenAPI\Client\Model\GetMultiRoleConfig200Response
```

Get multi-role feature configuration

Returns project app roles (default one editable `customer` starter until you add more) and settings

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getMultiRoleConfig($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->getMultiRoleConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetMultiRoleConfig200Response**](../Model/GetMultiRoleConfig200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPermissionsMatrix()`

```php
getPermissionsMatrix($project_id): \OpenAPI\Client\Model\GetPermissionsMatrix200Response
```

Get permissions matrix (collections + featurePermissions)

Dashboard helper: per-collection permission rows (role actions, `dataScope`, conditions) and a per-role `featurePermissions` snapshot used by app-role feature gates (messaging, integrations, storage, etc.).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getPermissionsMatrix($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->getPermissionsMatrix: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetPermissionsMatrix200Response**](../Model/GetPermissionsMatrix200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `oauthSignupWithRole()`

```php
oauthSignupWithRole($role, $provider, $project_id, $redirect_url)
```

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project's multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$role = customer; // string | Path segment must match the role's `signupEndpoint` (default `customer`; use each role's configured endpoint).
$provider = google; // string
$project_id = 685ad30be129932fbb7a1047; // string
$redirect_url = https://client.app/auth/callback; // string | The URL to redirect to after authentication

try {
    $apiInstance->oauthSignupWithRole($role, $provider, $project_id, $redirect_url);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->oauthSignupWithRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **role** | **string**| Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). | |
| **provider** | **string**|  | |
| **project_id** | **string**|  | |
| **redirect_url** | **string**| The URL to redirect to after authentication | [optional] |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `registerWithRole()`

```php
registerWithRole($role, $register_with_role_request): \OpenAPI\Client\Model\RegisterWithRole201Response
```

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The path segment must match a role's `signupEndpoint` (default starter is `customer`; add more roles via multi-role API). No authentication required - this is a public signup endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$role = customer; // string | Must match the role's `signupEndpoint` (default `customer`; other values for roles you add).
$register_with_role_request = {"email":"customer@example.com","password":"SecurePass123!","firstName":"Jane","lastName":"Doe","projectId":"685ad30be129932fbb7a1047","agreedToTerms":true}; // \OpenAPI\Client\Model\RegisterWithRoleRequest

try {
    $result = $apiInstance->registerWithRole($role, $register_with_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->registerWithRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **role** | **string**| Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). | |
| **register_with_role_request** | [**\OpenAPI\Client\Model\RegisterWithRoleRequest**](../Model/RegisterWithRoleRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\RegisterWithRole201Response**](../Model/RegisterWithRole201Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `simulateAppPermissions()`

```php
simulateAppPermissions($project_id, $simulate_app_permissions_request): \OpenAPI\Client\Model\SimulateAppPermissions200Response
```

Simulate app-role feature permission for a path

Dashboard-only. Given an app role slug and either an OpenAPI `operationId` **or** HTTP method + pathname, returns whether the role's `featurePermissions` would allow the operation for paths that have a feature gate. Unmapped paths or unknown operation IDs return `allowed: true` with reason `no_feature_gate_for_path` or `no_feature_gate_for_operation_id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$simulate_app_permissions_request = {"role":"customer","method":"POST","pathname":"/api/messaging/projects/685ad30be129932fbb7a1047/messaging/email"}; // \OpenAPI\Client\Model\SimulateAppPermissionsRequest

try {
    $result = $apiInstance->simulateAppPermissions($project_id, $simulate_app_permissions_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->simulateAppPermissions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **simulate_app_permissions_request** | [**\OpenAPI\Client\Model\SimulateAppPermissionsRequest**](../Model/SimulateAppPermissionsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\SimulateAppPermissions200Response**](../Model/SimulateAppPermissions200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `toggleRole()`

```php
toggleRole($project_id, $role_slug, $toggle_role_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Toggle role on/off

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$role_slug = customer; // string | Role slug to toggle (e.g. starter `customer` or a role you added).
$toggle_role_request = {"isEnabled":true}; // \OpenAPI\Client\Model\ToggleRoleRequest

try {
    $result = $apiInstance->toggleRole($project_id, $role_slug, $toggle_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->toggleRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **role_slug** | **string**| Role slug to toggle (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **toggle_role_request** | [**\OpenAPI\Client\Model\ToggleRoleRequest**](../Model/ToggleRoleRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCollectionPermissions()`

```php
updateCollectionPermissions($project_id, $role_slug, $collection_id, $update_collection_permissions_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Update collection permissions for a role

Update collection-specific permissions for a role in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$role_slug = customer; // string | Role slug (e.g. starter `customer` or a role you added).
$collection_id = 696ba6e4f4a9422ac4be4f74; // string
$update_collection_permissions_request = {"actions":["create","read","update","delete"],"conditions":{"status":"active"},"dataScope":"own"}; // \OpenAPI\Client\Model\UpdateCollectionPermissionsRequest

try {
    $result = $apiInstance->updateCollectionPermissions($project_id, $role_slug, $collection_id, $update_collection_permissions_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->updateCollectionPermissions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **role_slug** | **string**| Role slug (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **collection_id** | **string**|  | |
| **update_collection_permissions_request** | [**\OpenAPI\Client\Model\UpdateCollectionPermissionsRequest**](../Model/UpdateCollectionPermissionsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMultiRoleSettings()`

```php
updateMultiRoleSettings($project_id, $update_multi_role_settings_request): \OpenAPI\Client\Model\UpdateMultiRoleSettings200Response
```

Update multi-role feature settings

Update multi-role feature settings for a project: enable/disable the feature, set which app role is the default at signup, and tune `settings` (`allowMultipleRoles`, `requireRoleSelection`, `autoAssignDefault`). This endpoint does **not** edit role definitions or permissions — use `POST/PATCH .../multi-role/roles` for that (same shape as **Add custom role**). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$update_multi_role_settings_request = {"isEnabled":true,"defaultRole":"customer","settings":{"allowMultipleRoles":false,"requireRoleSelection":false,"autoAssignDefault":true,"dataOwnerField":"createdBy"}}; // \OpenAPI\Client\Model\UpdateMultiRoleSettingsRequest

try {
    $result = $apiInstance->updateMultiRoleSettings($project_id, $update_multi_role_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->updateMultiRoleSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **update_multi_role_settings_request** | [**\OpenAPI\Client\Model\UpdateMultiRoleSettingsRequest**](../Model/UpdateMultiRoleSettingsRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateMultiRoleSettings200Response**](../Model/UpdateMultiRoleSettings200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateProjectRole()`

```php
updateProjectRole($project_id, $role_slug, $update_project_role_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Update role configuration

Partial update of an app role. **`featurePermissions`** keys must match the app-role gate map (`services/appRoleFeatureMap.js`); schema: `components/schemas/AppRoleFeaturePermissions`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleFeatureApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$role_slug = customer; // string | Role slug to update (e.g. starter `customer` or a role you added).
$update_project_role_request = {"name":"App user","description":"End users of the app","signupEndpoint":"customer","requiresApproval":false,"requiresPayment":false,"requiresKYC":false,"collectionPermissions":{"posts":["create","read","update","delete"]},"featurePermissions":{"messaging":{"email":true,"sms":false,"push":false},"integration":{"read":true,"execute":true}}}; // \OpenAPI\Client\Model\UpdateProjectRoleRequest | Same fields as **Add custom role** — send only fields you want to change. `defaultPermissions` / `collectionPermissions` are normalized the same way as on create. **`featurePermissions`:** `components/schemas/AppRoleFeaturePermissions` (aligned with `services/appRoleFeatureMap.js`).

try {
    $result = $apiInstance->updateProjectRole($project_id, $role_slug, $update_project_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleFeatureApi->updateProjectRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **role_slug** | **string**| Role slug to update (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **update_project_role_request** | [**\OpenAPI\Client\Model\UpdateProjectRoleRequest**](../Model/UpdateProjectRoleRequest.md)| Same fields as **Add custom role** — send only fields you want to change. &#x60;defaultPermissions&#x60; / &#x60;collectionPermissions&#x60; are normalized the same way as on create. **&#x60;featurePermissions&#x60;:** &#x60;components/schemas/AppRoleFeaturePermissions&#x60; (aligned with &#x60;services/appRoleFeatureMap.js&#x60;). | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
