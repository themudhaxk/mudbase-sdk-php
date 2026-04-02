# OpenAPI\Client\AuthApi

User authentication and authorization

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**authConfirmPasswordReset()**](AuthApi.md#authConfirmPasswordReset) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP |
| [**authConvertAnonymous()**](AuthApi.md#authConvertAnonymous) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**authCreateAnonymous()**](AuthApi.md#authCreateAnonymous) | **POST** /api/auth/anonymous | Create anonymous session |
| [**authGetOAuthProviders()**](AuthApi.md#authGetOAuthProviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**authGetSession()**](AuthApi.md#authGetSession) | **GET** /api/auth/local/session | Get current session |
| [**authLogin()**](AuthApi.md#authLogin) | **POST** /api/auth/local/login | Login user |
| [**authLogout()**](AuthApi.md#authLogout) | **POST** /api/auth/local/logout | Logout user |
| [**authOauthCallback()**](AuthApi.md#authOauthCallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler |
| [**authOauthInitiate()**](AuthApi.md#authOauthInitiate) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**authRefresh()**](AuthApi.md#authRefresh) | **POST** /api/auth/refresh | Refresh access token (dashboard and project) |
| [**authRegister()**](AuthApi.md#authRegister) | **POST** /api/auth/local/register | Register new user |
| [**authRequestPasswordReset()**](AuthApi.md#authRequestPasswordReset) | **POST** /api/auth/local/password-reset | Request password reset (OTP) |
| [**authResendVerification()**](AuthApi.md#authResendVerification) | **POST** /api/auth/resend-verification | Resend verification email (no auth) |
| [**authResetPassword()**](AuthApi.md#authResetPassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (legacy) |
| [**authSendMagicLink()**](AuthApi.md#authSendMagicLink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**authSendOtp()**](AuthApi.md#authSendOtp) | **POST** /api/auth/otp/send | Send OTP code |
| [**authVerifyEmail()**](AuthApi.md#authVerifyEmail) | **POST** /api/auth/verify-email | Verify email address (no auth) |
| [**authVerifyMagicLink()**](AuthApi.md#authVerifyMagicLink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**authVerifyOtp()**](AuthApi.md#authVerifyOtp) | **POST** /api/auth/otp/verify | Verify OTP code |


## `authConfirmPasswordReset()`

```php
authConfirmPasswordReset($auth_confirm_password_reset_request): \OpenAPI\Client\Model\MessageResponse
```

Confirm password reset with OTP

Set new password using the OTP sent to the user's email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user's email was not yet verified, it is marked as verified upon successful reset.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_confirm_password_reset_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","otp":"123456","newPassword":"NewSecurePass123!"}; // \OpenAPI\Client\Model\AuthConfirmPasswordResetRequest | Email, projectId, OTP code, and new password.

try {
    $result = $apiInstance->authConfirmPasswordReset($auth_confirm_password_reset_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authConfirmPasswordReset: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_confirm_password_reset_request** | [**\OpenAPI\Client\Model\AuthConfirmPasswordResetRequest**](../Model/AuthConfirmPasswordResetRequest.md)| Email, projectId, OTP code, and new password. | |

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

## `authConvertAnonymous()`

```php
authConvertAnonymous($auth_convert_anonymous_request): \OpenAPI\Client\Model\AuthConvertAnonymous200Response
```

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$auth_convert_anonymous_request = {"email":"user@example.com","password":"SecurePassword123!","firstName":"John","lastName":"Doe"}; // \OpenAPI\Client\Model\AuthConvertAnonymousRequest | Email, password, and optional firstName, lastName for the new full account.

try {
    $result = $apiInstance->authConvertAnonymous($auth_convert_anonymous_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authConvertAnonymous: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_convert_anonymous_request** | [**\OpenAPI\Client\Model\AuthConvertAnonymousRequest**](../Model/AuthConvertAnonymousRequest.md)| Email, password, and optional firstName, lastName for the new full account. | |

### Return type

[**\OpenAPI\Client\Model\AuthConvertAnonymous200Response**](../Model/AuthConvertAnonymous200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authCreateAnonymous()`

```php
authCreateAnonymous($auth_create_anonymous_request): \OpenAPI\Client\Model\AuthCreateAnonymous200Response
```

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_create_anonymous_request = {"projectId":"685ad30be129932fbb7a1047","deviceId":"device-uuid-123"}; // \OpenAPI\Client\Model\AuthCreateAnonymousRequest | Optional projectId and deviceId for the anonymous session.

try {
    $result = $apiInstance->authCreateAnonymous($auth_create_anonymous_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authCreateAnonymous: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_create_anonymous_request** | [**\OpenAPI\Client\Model\AuthCreateAnonymousRequest**](../Model/AuthCreateAnonymousRequest.md)| Optional projectId and deviceId for the anonymous session. | [optional] |

### Return type

[**\OpenAPI\Client\Model\AuthCreateAnonymous200Response**](../Model/AuthCreateAnonymous200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authGetOAuthProviders()`

```php
authGetOAuthProviders(): \OpenAPI\Client\Model\AuthGetOAuthProviders200Response
```

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->authGetOAuthProviders();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authGetOAuthProviders: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\AuthGetOAuthProviders200Response**](../Model/AuthGetOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authGetSession()`

```php
authGetSession($project_id): \OpenAPI\Client\Model\AuthGetSession200Response
```

Get current session

Get the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID to get session for.

try {
    $result = $apiInstance->authGetSession($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authGetSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID to get session for. | |

### Return type

[**\OpenAPI\Client\Model\AuthGetSession200Response**](../Model/AuthGetSession200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authLogin()`

```php
authLogin($auth_login_request): \OpenAPI\Client\Model\AuthLogin200Response
```

Login user

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_login_request = {"email":"sarah.chen@example.com","password":"SecurePass123!","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\AuthLoginRequest | Login credentials (email, password) and project ID.

try {
    $result = $apiInstance->authLogin($auth_login_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authLogin: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_login_request** | [**\OpenAPI\Client\Model\AuthLoginRequest**](../Model/AuthLoginRequest.md)| Login credentials (email, password) and project ID. | |

### Return type

[**\OpenAPI\Client\Model\AuthLogin200Response**](../Model/AuthLogin200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authLogout()`

```php
authLogout(): \OpenAPI\Client\Model\MessageResponse
```

Logout user

Logout the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->authLogout();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authLogout: ', $e->getMessage(), PHP_EOL;
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

## `authOauthCallback()`

```php
authOauthCallback($provider): \OpenAPI\Client\Model\AuthOauthCallback200Response
```

OAuth callback handler

OAuth provider redirects the user here after consent. The server exchanges the code for tokens, creates or finds the user, and redirects to the client with token, refreshToken, and expiresIn in query params.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = 'provider_example'; // string | OAuth provider identifier (e.g. google, github).

try {
    $result = $apiInstance->authOauthCallback($provider);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authOauthCallback: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**| OAuth provider identifier (e.g. google, github). | |

### Return type

[**\OpenAPI\Client\Model\AuthOauthCallback200Response**](../Model/AuthOauthCallback200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authOauthInitiate()`

```php
authOauthInitiate($provider, $project_id, $redirect_url): \OpenAPI\Client\Model\AuthOauthInitiate200Response
```

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. After user authentication, redirects to the OAuth provider's consent screen.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = google; // string | OAuth provider identifier (e.g. google, github).
$project_id = 685ad30be129932fbb7a1047; // string | Project ID for which OAuth is configured.
$redirect_url = https://client.app/auth/callback; // string | The URL to redirect to after authentication. Must be pre-registered in project settings.

try {
    $result = $apiInstance->authOauthInitiate($provider, $project_id, $redirect_url);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authOauthInitiate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**| OAuth provider identifier (e.g. google, github). | |
| **project_id** | **string**| Project ID for which OAuth is configured. | |
| **redirect_url** | **string**| The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional] |

### Return type

[**\OpenAPI\Client\Model\AuthOauthInitiate200Response**](../Model/AuthOauthInitiate200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authRefresh()`

```php
authRefresh($auth_refresh_request): \OpenAPI\Client\Model\AuthRefresh200Response
```

Refresh access token (dashboard and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **dashboard** (builder console) and **app** (end-user) auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_refresh_request = {"refreshToken":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."}; // \OpenAPI\Client\Model\AuthRefreshRequest | JSON body containing the refresh token to exchange for a new access token and refresh token (token rotation).

try {
    $result = $apiInstance->authRefresh($auth_refresh_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authRefresh: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_refresh_request** | [**\OpenAPI\Client\Model\AuthRefreshRequest**](../Model/AuthRefreshRequest.md)| JSON body containing the refresh token to exchange for a new access token and refresh token (token rotation). | |

### Return type

[**\OpenAPI\Client\Model\AuthRefresh200Response**](../Model/AuthRefresh200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authRegister()`

```php
authRegister($auth_register_request): \OpenAPI\Client\Model\AuthRegister201Response
```

Register new user

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_register_request = {"email":"sarah.chen@example.com","password":"SecurePass123!","firstName":"Sarah","lastName":"Chen","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\AuthRegisterRequest | Registration payload (email, password, firstName, lastName, projectId).

try {
    $result = $apiInstance->authRegister($auth_register_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authRegister: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_register_request** | [**\OpenAPI\Client\Model\AuthRegisterRequest**](../Model/AuthRegisterRequest.md)| Registration payload (email, password, firstName, lastName, projectId). | |

### Return type

[**\OpenAPI\Client\Model\AuthRegister201Response**](../Model/AuthRegister201Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authRequestPasswordReset()`

```php
authRequestPasswordReset($auth_request_password_reset_request): \OpenAPI\Client\Model\MessageResponse
```

Request password reset (OTP)

When projectId is provided, sends a 6-digit OTP to the user's email (app reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_request_password_reset_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\AuthRequestPasswordResetRequest | Email and optional projectId for app OTP or org token link.

try {
    $result = $apiInstance->authRequestPasswordReset($auth_request_password_reset_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authRequestPasswordReset: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_request_password_reset_request** | [**\OpenAPI\Client\Model\AuthRequestPasswordResetRequest**](../Model/AuthRequestPasswordResetRequest.md)| Email and optional projectId for app OTP or org token link. | |

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

## `authResendVerification()`

```php
authResendVerification($auth_resend_verification_request): \OpenAPI\Client\Model\MessageResponse
```

Resend verification email (no auth)

Sends a new verification email to the given email (and optional project). For unauthenticated users who have not verified yet. Rate limited (e.g. 3 per 15 min per IP).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_resend_verification_request = new \OpenAPI\Client\Model\AuthResendVerificationRequest(); // \OpenAPI\Client\Model\AuthResendVerificationRequest | Email address to resend to; optional `projectId` for project-scoped verification links.

try {
    $result = $apiInstance->authResendVerification($auth_resend_verification_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authResendVerification: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_resend_verification_request** | [**\OpenAPI\Client\Model\AuthResendVerificationRequest**](../Model/AuthResendVerificationRequest.md)| Email address to resend to; optional &#x60;projectId&#x60; for project-scoped verification links. | |

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

## `authResetPassword()`

```php
authResetPassword($token, $auth_reset_password_request): \OpenAPI\Client\Model\MessageResponse
```

Reset password with token (legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for app resets.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$token = 'token_example'; // string | Password reset token from email link.
$auth_reset_password_request = {"password":"NewSecurePass123!","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\AuthResetPasswordRequest | New password and optional projectId.

try {
    $result = $apiInstance->authResetPassword($token, $auth_reset_password_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authResetPassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **token** | **string**| Password reset token from email link. | |
| **auth_reset_password_request** | [**\OpenAPI\Client\Model\AuthResetPasswordRequest**](../Model/AuthResetPasswordRequest.md)| New password and optional projectId. | |

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

## `authSendMagicLink()`

```php
authSendMagicLink($magic_link_request): \OpenAPI\Client\Model\MessageResponse
```

Send magic link

Sends a one-time magic link to the given email for the project. The user clicks the link and is authenticated without a password. Use verify endpoint with the token from the link. Public endpoint; rate limited.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$magic_link_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","redirectUrl":"https://app.example.com/auth/callback"}; // \OpenAPI\Client\Model\MagicLinkRequest | Email, projectId, and optional redirect URL for the magic link.

try {
    $result = $apiInstance->authSendMagicLink($magic_link_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authSendMagicLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **magic_link_request** | [**\OpenAPI\Client\Model\MagicLinkRequest**](../Model/MagicLinkRequest.md)| Email, projectId, and optional redirect URL for the magic link. | |

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

## `authSendOtp()`

```php
authSendOtp($otp_send_request): \OpenAPI\Client\Model\MessageResponse
```

Send OTP code

Sends a one-time code via SMS or email for the given project. Use verify endpoint to exchange the code for a session. Public endpoint; rate limited.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$otp_send_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","method":"email"}; // \OpenAPI\Client\Model\OTPSendRequest | Project ID, delivery method (sms/email), and phone or email.

try {
    $result = $apiInstance->authSendOtp($otp_send_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authSendOtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **otp_send_request** | [**\OpenAPI\Client\Model\OTPSendRequest**](../Model/OTPSendRequest.md)| Project ID, delivery method (sms/email), and phone or email. | |

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

## `authVerifyEmail()`

```php
authVerifyEmail($auth_verify_email_request): \OpenAPI\Client\Model\MessageResponse
```

Verify email address (no auth)

Verifies the user's email using the token from the link sent at signup. Use for project-scoped or general signup flows (unauthenticated). Same behavior as POST /api/users/verify-email.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_verify_email_request = new \OpenAPI\Client\Model\AuthVerifyEmailRequest(); // \OpenAPI\Client\Model\AuthVerifyEmailRequest | Verification token from the email link; optional `projectId` for project-scoped signup.

try {
    $result = $apiInstance->authVerifyEmail($auth_verify_email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authVerifyEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_verify_email_request** | [**\OpenAPI\Client\Model\AuthVerifyEmailRequest**](../Model/AuthVerifyEmailRequest.md)| Verification token from the email link; optional &#x60;projectId&#x60; for project-scoped signup. | |

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

## `authVerifyMagicLink()`

```php
authVerifyMagicLink($auth_verify_magic_link_request): \OpenAPI\Client\Model\AuthResponse
```

Verify magic link

Exchanges the magic link token (from the link sent by send) for a session. Returns token and user on success. Token is short-lived and single-use.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$auth_verify_magic_link_request = {"token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJwcm9qZWN0SWQiOiI2ODVhZDMwYmUxMjk5MzJmYmI3YTEwNDciLCJpYXQiOjE3NTA3ODA4OTgsImV4cCI6MTc1MDc4NDQ5OH0.example"}; // \OpenAPI\Client\Model\AuthVerifyMagicLinkRequest | The token from the magic link URL.

try {
    $result = $apiInstance->authVerifyMagicLink($auth_verify_magic_link_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authVerifyMagicLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **auth_verify_magic_link_request** | [**\OpenAPI\Client\Model\AuthVerifyMagicLinkRequest**](../Model/AuthVerifyMagicLinkRequest.md)| The token from the magic link URL. | |

### Return type

[**\OpenAPI\Client\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `authVerifyOtp()`

```php
authVerifyOtp($otp_verify_request): \OpenAPI\Client\Model\AuthResponse
```

Verify OTP code

Verifies the OTP code and returns a session token and user. Public endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\AuthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$otp_verify_request = {"identifier":"user@example.com","otp":"123456","projectId":"685ad30be129932fbb7a1047"}; // \OpenAPI\Client\Model\OTPVerifyRequest | Identifier (phone/email), OTP code, and project ID.

try {
    $result = $apiInstance->authVerifyOtp($otp_verify_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthApi->authVerifyOtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **otp_verify_request** | [**\OpenAPI\Client\Model\OTPVerifyRequest**](../Model/OTPVerifyRequest.md)| Identifier (phone/email), OTP code, and project ID. | |

### Return type

[**\OpenAPI\Client\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
