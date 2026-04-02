# OpenAPI\Client\UsersApi

User profile management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**usersChangePassword()**](UsersApi.md#usersChangePassword) | **PATCH** /api/users/password | Change password |
| [**usersDisable2fa()**](UsersApi.md#usersDisable2fa) | **POST** /api/users/2fa/disable | Disable 2FA |
| [**usersEraseData()**](UsersApi.md#usersEraseData) | **POST** /api/users/me/erase | Delete user data (GDPR Article 17) |
| [**usersExportData()**](UsersApi.md#usersExportData) | **GET** /api/users/me/export | Export user data (GDPR Article 15) |
| [**usersGet()**](UsersApi.md#usersGet) | **GET** /api/users/me | Get current user profile |
| [**usersLinkOAuthProvider()**](UsersApi.md#usersLinkOAuthProvider) | **GET** /api/users/me/oauth-providers/link/{provider} | Link OAuth provider to account |
| [**usersListOAuthProviders()**](UsersApi.md#usersListOAuthProviders) | **GET** /api/users/me/oauth-providers | List linked OAuth providers |
| [**usersResendVerification()**](UsersApi.md#usersResendVerification) | **POST** /api/users/resend-verification | Resend verification email |
| [**usersSetup2fa()**](UsersApi.md#usersSetup2fa) | **POST** /api/users/2fa/setup | Initiate two-factor authentication setup (secret, QR code, backup codes) |
| [**usersUnlinkOAuthProvider()**](UsersApi.md#usersUnlinkOAuthProvider) | **DELETE** /api/users/me/oauth-providers/{provider} | Unlink OAuth provider |
| [**usersUpdate()**](UsersApi.md#usersUpdate) | **PATCH** /api/users/update | Update user profile |
| [**usersVerify2fa()**](UsersApi.md#usersVerify2fa) | **POST** /api/users/2fa/verify | Verify and enable 2FA |
| [**usersVerifyEmail()**](UsersApi.md#usersVerifyEmail) | **POST** /api/users/verify-email | Verify email address (organization and project) |


## `usersChangePassword()`

```php
usersChangePassword($change_password_request): \OpenAPI\Client\Model\MessageResponse
```

Change password

Change the current user's password. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$change_password_request = {"currentPassword":"OldPassword123!","newPassword":"NewSecurePass123!"}; // \OpenAPI\Client\Model\ChangePasswordRequest | Current password and new password.

try {
    $result = $apiInstance->usersChangePassword($change_password_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersChangePassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **change_password_request** | [**\OpenAPI\Client\Model\ChangePasswordRequest**](../Model/ChangePasswordRequest.md)| Current password and new password. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersDisable2fa()`

```php
usersDisable2fa($users_disable2fa_request): \OpenAPI\Client\Model\MessageResponse
```

Disable 2FA

Disable two-factor authentication for the current user. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$users_disable2fa_request = {"password":"SecurePass123!","token":"123456"}; // \OpenAPI\Client\Model\UsersDisable2faRequest | Current password and one-time code to confirm disable.

try {
    $result = $apiInstance->usersDisable2fa($users_disable2fa_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersDisable2fa: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **users_disable2fa_request** | [**\OpenAPI\Client\Model\UsersDisable2faRequest**](../Model/UsersDisable2faRequest.md)| Current password and one-time code to confirm disable. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersEraseData()`

```php
usersEraseData($users_erase_data_request): \OpenAPI\Client\Model\UsersEraseData200Response
```

Delete user data (GDPR Article 17)

Request account erasure (right to be forgotten). Anonymizes PII and deactivates account with 7-day grace period. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$users_erase_data_request = {"confirmation":"DELETE_MY_ACCOUNT","reason":"No longer need the service"}; // \OpenAPI\Client\Model\UsersEraseDataRequest | Confirmation string (DELETE_MY_ACCOUNT) and optional reason for erasure.

try {
    $result = $apiInstance->usersEraseData($users_erase_data_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersEraseData: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **users_erase_data_request** | [**\OpenAPI\Client\Model\UsersEraseDataRequest**](../Model/UsersEraseDataRequest.md)| Confirmation string (DELETE_MY_ACCOUNT) and optional reason for erasure. | |

### Return type

[**\OpenAPI\Client\Model\UsersEraseData200Response**](../Model/UsersEraseData200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersExportData()`

```php
usersExportData(): \OpenAPI\Client\Model\UsersExportData200Response
```

Export user data (GDPR Article 15)

Export all user data in JSON format for GDPR data portability compliance. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->usersExportData();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersExportData: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\UsersExportData200Response**](../Model/UsersExportData200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersGet()`

```php
usersGet(): \OpenAPI\Client\Model\UsersGet200Response
```

Get current user profile

Get the current authenticated user's profile. Accepts JWT Bearer token (BearerToken).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->usersGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\UsersGet200Response**](../Model/UsersGet200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersLinkOAuthProvider()`

```php
usersLinkOAuthProvider($provider, $project_id): \OpenAPI\Client\Model\UsersLinkOAuthProvider200Response
```

Link OAuth provider to account

Initiate OAuth flow to link a new provider to the current account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$provider = google; // string | OAuth provider to link (e.g. google, github).
$project_id = 685ad30be129932fbb7a1047; // string | Project ID for the OAuth link context.

try {
    $result = $apiInstance->usersLinkOAuthProvider($provider, $project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersLinkOAuthProvider: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**| OAuth provider to link (e.g. google, github). | |
| **project_id** | **string**| Project ID for the OAuth link context. | [optional] |

### Return type

[**\OpenAPI\Client\Model\UsersLinkOAuthProvider200Response**](../Model/UsersLinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersListOAuthProviders()`

```php
usersListOAuthProviders(): \OpenAPI\Client\Model\UsersListOAuthProviders200Response
```

List linked OAuth providers

Get all OAuth providers linked to the current user's account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->usersListOAuthProviders();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersListOAuthProviders: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\UsersListOAuthProviders200Response**](../Model/UsersListOAuthProviders200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersResendVerification()`

```php
usersResendVerification(): \OpenAPI\Client\Model\MessageResponse
```

Resend verification email

Sends a new verification email to the authenticated user. Rate limited (e.g. 3 requests per 15 minutes per user). For app users the link includes project context.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->usersResendVerification();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersResendVerification: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `usersSetup2fa()`

```php
usersSetup2fa(): \OpenAPI\Client\Model\TwoFASetupResponse
```

Initiate two-factor authentication setup (secret, QR code, backup codes)

Initiates two-factor authentication setup for the current user. Returns a secret, QR code, and manual entry key for the user to add to an authenticator app. Requires JWT Bearer token (BearerToken). API keys are not supported.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->usersSetup2fa();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersSetup2fa: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\TwoFASetupResponse**](../Model/TwoFASetupResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersUnlinkOAuthProvider()`

```php
usersUnlinkOAuthProvider($provider): \OpenAPI\Client\Model\UsersUnlinkOAuthProvider200Response
```

Unlink OAuth provider

Remove an OAuth provider from the current account. Cannot unlink if it's the only authentication method. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$provider = github; // string | OAuth provider to unlink (e.g. google, github).

try {
    $result = $apiInstance->usersUnlinkOAuthProvider($provider);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersUnlinkOAuthProvider: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**| OAuth provider to unlink (e.g. google, github). | |

### Return type

[**\OpenAPI\Client\Model\UsersUnlinkOAuthProvider200Response**](../Model/UsersUnlinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersUpdate()`

```php
usersUpdate($update_user_request): \OpenAPI\Client\Model\UsersUpdate200Response
```

Update user profile

Update the current user's profile. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$update_user_request = {"firstName":"John","lastName":"Doe","avatar":"https://example.com/avatar.jpg"}; // \OpenAPI\Client\Model\UpdateUserRequest | Profile fields to update (firstName, lastName, avatar).

try {
    $result = $apiInstance->usersUpdate($update_user_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersUpdate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **update_user_request** | [**\OpenAPI\Client\Model\UpdateUserRequest**](../Model/UpdateUserRequest.md)| Profile fields to update (firstName, lastName, avatar). | |

### Return type

[**\OpenAPI\Client\Model\UsersUpdate200Response**](../Model/UsersUpdate200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersVerify2fa()`

```php
usersVerify2fa($users_verify2fa_request): \OpenAPI\Client\Model\MessageResponse
```

Verify and enable 2FA

Verify and enable two-factor authentication for the current user. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$users_verify2fa_request = {"token":"123456"}; // \OpenAPI\Client\Model\UsersVerify2faRequest | One-time code from the authenticator app.

try {
    $result = $apiInstance->usersVerify2fa($users_verify2fa_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersVerify2fa: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **users_verify2fa_request** | [**\OpenAPI\Client\Model\UsersVerify2faRequest**](../Model/UsersVerify2faRequest.md)| One-time code from the authenticator app. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `usersVerifyEmail()`

```php
usersVerifyEmail($auth_verify_email_request): \OpenAPI\Client\Model\MessageResponse
```

Verify email address (organization and project)

Verifies the user's email using the token from the link sent at signup. Works for both organization (platform) and app signups; the token is from the verification link (e.g. verify-email?token=... for org, or verify-email?token=...&project=... for project).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_verify_email_request = {"token":"a1b2c3d4..."}; // \OpenAPI\Client\Model\AuthVerifyEmailRequest | Verification token from the email link; optional projectId for project context.

try {
    $result = $apiInstance->usersVerifyEmail($auth_verify_email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->usersVerifyEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_verify_email_request** | [**\OpenAPI\Client\Model\AuthVerifyEmailRequest**](../Model/AuthVerifyEmailRequest.md)| Verification token from the email link; optional projectId for project context. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
