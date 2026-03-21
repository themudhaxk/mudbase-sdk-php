# OpenAPI\Client\MultiRoleApi

Project app roles (starter &#x60;customer&#x60; role) with per-collection CRUD; add roles via API and match signup paths to each role&#39;s &#x60;signupEndpoint&#x60;

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**authOauthSignupWithRole()**](MultiRoleApi.md#authOauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**authRegisterWithRole()**](MultiRoleApi.md#authRegisterWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |
| [**multiRoleAddRole()**](MultiRoleApi.md#multiRoleAddRole) | **POST** /api/projects/{projectId}/multi-role/roles | Add custom role |
| [**multiRoleGetAvailableRoles()**](MultiRoleApi.md#multiRoleGetAvailableRoles) | **GET** /api/projects/{projectId}/multi-role/roles/available | Get available roles for signup |
| [**multiRoleGetConfig()**](MultiRoleApi.md#multiRoleGetConfig) | **GET** /api/projects/{projectId}/multi-role | Get multi-role feature configuration |
| [**multiRoleToggleRole()**](MultiRoleApi.md#multiRoleToggleRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/toggle | Toggle role on/off |
| [**multiRoleUpdateCollectionPermissions()**](MultiRoleApi.md#multiRoleUpdateCollectionPermissions) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/collections/{collectionId}/permissions | Update collection permissions for a role |
| [**multiRoleUpdateRole()**](MultiRoleApi.md#multiRoleUpdateRole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug} | Update role configuration |
| [**multiRoleUpdateSettings()**](MultiRoleApi.md#multiRoleUpdateSettings) | **PATCH** /api/projects/{projectId}/multi-role/settings | Update multi-role feature settings |


## `authOauthSignupWithRole()`

```php
authOauthSignupWithRole($role, $provider, $project_id, $redirect_url): \OpenAPI\Client\Model\UsersLinkOAuthProvider200Response
```

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project's multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$role = customer; // string | Path segment must match the role's `signupEndpoint` (default `customer`; use each role's configured endpoint).
$provider = google; // string | OAuth provider (e.g. google, github).
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$redirect_url = https://client.app/auth/callback; // string | The URL to redirect to after authentication

try {
    $result = $apiInstance->authOauthSignupWithRole($role, $provider, $project_id, $redirect_url);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->authOauthSignupWithRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **role** | **string**| Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). | |
| **provider** | **string**| OAuth provider (e.g. google, github). | |
| **project_id** | **string**| Project ID. | |
| **redirect_url** | **string**| The URL to redirect to after authentication | [optional] |

### Return type

[**\OpenAPI\Client\Model\UsersLinkOAuthProvider200Response**](../Model/UsersLinkOAuthProvider200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authRegisterWithRole()`

```php
authRegisterWithRole($role, $auth_register_with_role_request)
```

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The path segment must match a role's `signupEndpoint` (default starter is `customer`; add more roles via multi-role API). No authentication required - this is a public signup endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$role = customer; // string | Must match the role's `signupEndpoint` (default `customer`; other values for roles you add).
$auth_register_with_role_request = {"email":"customer@example.com","password":"SecurePass123!","firstName":"Jane","lastName":"Doe","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\AuthRegisterWithRoleRequest | Registration payload (email, password, firstName, lastName, projectId).

try {
    $apiInstance->authRegisterWithRole($role, $auth_register_with_role_request);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->authRegisterWithRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **role** | **string**| Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). | |
| **auth_register_with_role_request** | [**\OpenAPI\Client\Model\AuthRegisterWithRoleRequest**](../Model/AuthRegisterWithRoleRequest.md)| Registration payload (email, password, firstName, lastName, projectId). | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleAddRole()`

```php
multiRoleAddRole($project_id, $multi_role_add_role_request): \OpenAPI\Client\Model\MultiRoleToggleRole200Response
```

Add custom role

Add a custom role to a project with specific permissions and signup endpoint. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$multi_role_add_role_request = {"slug":"seller","name":"Seller","description":"Seller role with CRUD on seller-owned collections","signupEndpoint":"seller","collectionPermissions":{"listings":["create","read","update","delete"],"orders":{"actions":["create","read"],"conditions":{"status":"active"}}}}; // \OpenAPI\Client\Model\MultiRoleAddRoleRequest | Custom role definition. Use `collectionPermissions` to apply CRUD per collection slug (e.g. users/products/orders). `defaultPermissions` is optional for global/base permissions.

try {
    $result = $apiInstance->multiRoleAddRole($project_id, $multi_role_add_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleAddRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **multi_role_add_role_request** | [**\OpenAPI\Client\Model\MultiRoleAddRoleRequest**](../Model/MultiRoleAddRoleRequest.md)| Custom role definition. Use &#x60;collectionPermissions&#x60; to apply CRUD per collection slug (e.g. users/products/orders). &#x60;defaultPermissions&#x60; is optional for global/base permissions. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleToggleRole200Response**](../Model/MultiRoleToggleRole200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleGetAvailableRoles()`

```php
multiRoleGetAvailableRoles($project_id): \OpenAPI\Client\Model\MultiRoleGetAvailableRoles200Response
```

Get available roles for signup

Get all available roles for user signup in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.

try {
    $result = $apiInstance->multiRoleGetAvailableRoles($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleGetAvailableRoles: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleGetAvailableRoles200Response**](../Model/MultiRoleGetAvailableRoles200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleGetConfig()`

```php
multiRoleGetConfig($project_id): \OpenAPI\Client\Model\MultiRoleGetConfig200Response
```

Get multi-role feature configuration

Returns project app roles (default one editable `customer` starter until you add more) and settings.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.

try {
    $result = $apiInstance->multiRoleGetConfig($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleGetConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleGetConfig200Response**](../Model/MultiRoleGetConfig200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleToggleRole()`

```php
multiRoleToggleRole($project_id, $role_slug, $multi_role_toggle_role_request): \OpenAPI\Client\Model\MultiRoleToggleRole200Response
```

Toggle role on/off

Enable or disable a role for the project. When disabled, the role is no longer available for signup or assignment.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$role_slug = customer; // string | Role slug to toggle (e.g. starter `customer` or a role you added).
$multi_role_toggle_role_request = {"isEnabled":true}; // \OpenAPI\Client\Model\MultiRoleToggleRoleRequest | Whether the role is enabled (true) or disabled (false).

try {
    $result = $apiInstance->multiRoleToggleRole($project_id, $role_slug, $multi_role_toggle_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleToggleRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_slug** | **string**| Role slug to toggle (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **multi_role_toggle_role_request** | [**\OpenAPI\Client\Model\MultiRoleToggleRoleRequest**](../Model/MultiRoleToggleRoleRequest.md)| Whether the role is enabled (true) or disabled (false). | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleToggleRole200Response**](../Model/MultiRoleToggleRole200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleUpdateCollectionPermissions()`

```php
multiRoleUpdateCollectionPermissions($project_id, $role_slug, $collection_id, $multi_role_update_collection_permissions_request): \OpenAPI\Client\Model\MultiRoleToggleRole200Response
```

Update collection permissions for a role

Update collection-specific permissions for a role in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$role_slug = customer; // string | Role slug (e.g. starter `customer` or a role you added).
$collection_id = 696ba6e4f4a9422ac4be4f74; // string | Collection ID to set permissions for.
$multi_role_update_collection_permissions_request = {"actions":["create","read","update","delete"],"conditions":{"status":"active"}}; // \OpenAPI\Client\Model\MultiRoleUpdateCollectionPermissionsRequest | Allowed actions and optional conditions for the role on this collection.

try {
    $result = $apiInstance->multiRoleUpdateCollectionPermissions($project_id, $role_slug, $collection_id, $multi_role_update_collection_permissions_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleUpdateCollectionPermissions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_slug** | **string**| Role slug (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **collection_id** | **string**| Collection ID to set permissions for. | |
| **multi_role_update_collection_permissions_request** | [**\OpenAPI\Client\Model\MultiRoleUpdateCollectionPermissionsRequest**](../Model/MultiRoleUpdateCollectionPermissionsRequest.md)| Allowed actions and optional conditions for the role on this collection. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleToggleRole200Response**](../Model/MultiRoleToggleRole200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleUpdateRole()`

```php
multiRoleUpdateRole($project_id, $role_slug, $multi_role_update_role_request): \OpenAPI\Client\Model\MultiRoleToggleRole200Response
```

Update role configuration

Update an app role — same fields as **Add custom role** (partial). `defaultPermissions` / `collectionPermissions` use the same normalization as on create.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$role_slug = customer; // string | Role slug to update (e.g. starter `customer` or a role you added).
$multi_role_update_role_request = {"name":"App user","description":"End users of the app","signupEndpoint":"customer","requiresApproval":false,"requiresPayment":false,"requiresKYC":false,"collectionPermissions":{"posts":["create","read","update","delete"]}}; // \OpenAPI\Client\Model\MultiRoleUpdateRoleRequest | Same fields as **Add custom role** — send only fields you want to change. `defaultPermissions` / `collectionPermissions` are normalized the same way as on create.

try {
    $result = $apiInstance->multiRoleUpdateRole($project_id, $role_slug, $multi_role_update_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleUpdateRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **role_slug** | **string**| Role slug to update (e.g. starter &#x60;customer&#x60; or a role you added). | |
| **multi_role_update_role_request** | [**\OpenAPI\Client\Model\MultiRoleUpdateRoleRequest**](../Model/MultiRoleUpdateRoleRequest.md)| Same fields as **Add custom role** — send only fields you want to change. &#x60;defaultPermissions&#x60; / &#x60;collectionPermissions&#x60; are normalized the same way as on create. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleToggleRole200Response**](../Model/MultiRoleToggleRole200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `multiRoleUpdateSettings()`

```php
multiRoleUpdateSettings($project_id, $multi_role_update_settings_request): \OpenAPI\Client\Model\MultiRoleUpdateSettings200Response
```

Update multi-role feature settings

Update multi-role feature settings: enable/disable the feature, `defaultRole`, and `settings` (`allowMultipleRoles`, `requireRoleSelection`, `autoAssignDefault`). Does not edit role definitions — use `POST/PATCH .../multi-role/roles` (same body shape as add role). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MultiRoleApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string | Project ID.
$multi_role_update_settings_request = {"isEnabled":true,"defaultRole":"customer","settings":{"allowMultipleRoles":false,"requireRoleSelection":false,"autoAssignDefault":true}}; // \OpenAPI\Client\Model\MultiRoleUpdateSettingsRequest | Feature flags only — not per-role approval. Use `settings.allowMultipleRoles`, `requireRoleSelection`, `autoAssignDefault`.

try {
    $result = $apiInstance->multiRoleUpdateSettings($project_id, $multi_role_update_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MultiRoleApi->multiRoleUpdateSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **multi_role_update_settings_request** | [**\OpenAPI\Client\Model\MultiRoleUpdateSettingsRequest**](../Model/MultiRoleUpdateSettingsRequest.md)| Feature flags only — not per-role approval. Use &#x60;settings.allowMultipleRoles&#x60;, &#x60;requireRoleSelection&#x60;, &#x60;autoAssignDefault&#x60;. | |

### Return type

[**\OpenAPI\Client\Model\MultiRoleUpdateSettings200Response**](../Model/MultiRoleUpdateSettings200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
