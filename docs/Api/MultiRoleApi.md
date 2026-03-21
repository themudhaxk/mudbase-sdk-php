# OpenAPI\Client\MultiRoleApi

Project app roles (starter &#x60;customer&#x60; role) with per-collection CRUD; add roles via API and match signup paths to each role&#39;s &#x60;signupEndpoint&#x60;

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**authOauthSignupWithRole()**](MultiRoleApi.md#authOauthSignupWithRole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**authRegisterWithRole()**](MultiRoleApi.md#authRegisterWithRole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |


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
