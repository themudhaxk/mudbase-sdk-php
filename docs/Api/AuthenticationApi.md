# MudbaseSDK\AuthenticationApi

User authentication and authorization

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**acceptInvite()**](AuthenticationApi.md#acceptInvite) | **POST** /api/auth/accept-invite | Accept organization invitation |
| [**confirmLocalPasswordResetWithOtp()**](AuthenticationApi.md#confirmLocalPasswordResetWithOtp) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP (project-based) |
| [**convertAnonymousAccount()**](AuthenticationApi.md#convertAnonymousAccount) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**createAnonymousSession()**](AuthenticationApi.md#createAnonymousSession) | **POST** /api/auth/anonymous | Create anonymous session |
| [**getAvailableOAuthProviders()**](AuthenticationApi.md#getAvailableOAuthProviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**getCurrentSession()**](AuthenticationApi.md#getCurrentSession) | **GET** /api/auth/session | Get current session |
| [**getLocalSession()**](AuthenticationApi.md#getLocalSession) | **GET** /api/auth/local/session | Get current session (project-based) |
| [**getOrgOAuthProviders()**](AuthenticationApi.md#getOrgOAuthProviders) | **GET** /api/auth/oauth-org/providers | Get available OAuth providers for organization-based auth |
| [**initiateOAuth()**](AuthenticationApi.md#initiateOAuth) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**initiateOrgOAuth()**](AuthenticationApi.md#initiateOrgOAuth) | **GET** /api/auth/oauth-org/{provider} | Initiate OAuth authentication for organization |
| [**loginLocalUser()**](AuthenticationApi.md#loginLocalUser) | **POST** /api/auth/local/login | Login user (project-based) |
| [**loginUser()**](AuthenticationApi.md#loginUser) | **POST** /api/auth/login | Login user |
| [**logoutLocalUser()**](AuthenticationApi.md#logoutLocalUser) | **POST** /api/auth/local/logout | Logout user (project-based) |
| [**logoutUser()**](AuthenticationApi.md#logoutUser) | **POST** /api/auth/logout | Logout user |
| [**oauthCallback()**](AuthenticationApi.md#oauthCallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler (project-based) |
| [**orgOAuthCallback()**](AuthenticationApi.md#orgOAuthCallback) | **GET** /api/auth/oauth-org/callback/{provider} | OAuth callback handler for organization |
| [**refreshToken()**](AuthenticationApi.md#refreshToken) | **POST** /api/auth/refresh | Refresh access token (org and project) |
| [**registerLocalUser()**](AuthenticationApi.md#registerLocalUser) | **POST** /api/auth/local/register | Register new user (project-based) |
| [**registerUser()**](AuthenticationApi.md#registerUser) | **POST** /api/auth/register | Register new user |
| [**requestLocalPasswordReset()**](AuthenticationApi.md#requestLocalPasswordReset) | **POST** /api/auth/local/password-reset | Request password reset (project-based, OTP) |
| [**requestPasswordReset()**](AuthenticationApi.md#requestPasswordReset) | **POST** /api/auth/password-reset | Request password reset (organization / platform) |
| [**resendVerificationAuth()**](AuthenticationApi.md#resendVerificationAuth) | **POST** /api/auth/resend-verification | Resend verification email (no auth) |
| [**resetLocalPassword()**](AuthenticationApi.md#resetLocalPassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (project-based, legacy) |
| [**resetPassword()**](AuthenticationApi.md#resetPassword) | **POST** /api/auth/password-reset/{token} | Reset password with token (organization / platform) |
| [**sendMagicLink()**](AuthenticationApi.md#sendMagicLink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**sendOTP()**](AuthenticationApi.md#sendOTP) | **POST** /api/auth/otp/send | Send OTP code |
| [**validatePasswordResetToken()**](AuthenticationApi.md#validatePasswordResetToken) | **POST** /api/auth/password-reset/validate | Validate password reset token |
| [**verifyEmailAuth()**](AuthenticationApi.md#verifyEmailAuth) | **POST** /api/auth/verify-email | Verify email address (no auth) |
| [**verifyMagicLink()**](AuthenticationApi.md#verifyMagicLink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**verifyOTP()**](AuthenticationApi.md#verifyOTP) | **POST** /api/auth/otp/verify | Verify OTP code |


## `acceptInvite()`

```php
acceptInvite($accept_invite_request): \MudbaseSDK\Model\AcceptInvite201Response
```

Accept organization invitation

Accept an organization invitation using the token from the invite email link (e.g. `/invite/{token}?orgId=...`). Creates a new user with the invited email and adds them to the organization with the invited role. Returns a JWT and user so the client can log the user in immediately. No authentication required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$accept_invite_request = {"token":"a1b2c3d4e5f6...","password":"SecurePass123!","firstName":"Jane","lastName":"Doe"}; // \MudbaseSDK\Model\AcceptInviteRequest

try {
    $result = $apiInstance->acceptInvite($accept_invite_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->acceptInvite: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **accept_invite_request** | [**\MudbaseSDK\Model\AcceptInviteRequest**](../Model/AcceptInviteRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AcceptInvite201Response**](../Model/AcceptInvite201Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `confirmLocalPasswordResetWithOtp()`

```php
confirmLocalPasswordResetWithOtp($confirm_local_password_reset_with_otp_request): \MudbaseSDK\Model\MessageResponse
```

Confirm password reset with OTP (project-based)

Set new password using the OTP sent to the user's email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user's email was not yet verified, it is marked as verified upon successful reset.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$confirm_local_password_reset_with_otp_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","otp":"123456","newPassword":"NewSecurePass123!"}; // \MudbaseSDK\Model\ConfirmLocalPasswordResetWithOtpRequest

try {
    $result = $apiInstance->confirmLocalPasswordResetWithOtp($confirm_local_password_reset_with_otp_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->confirmLocalPasswordResetWithOtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **confirm_local_password_reset_with_otp_request** | [**\MudbaseSDK\Model\ConfirmLocalPasswordResetWithOtpRequest**](../Model/ConfirmLocalPasswordResetWithOtpRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `convertAnonymousAccount()`

```php
convertAnonymousAccount($convert_anonymous_account_request): \MudbaseSDK\Model\ConvertAnonymousAccount200Response
```

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$convert_anonymous_account_request = {"email":"user@example.com","password":"SecurePassword123!","firstName":"John","lastName":"Doe"}; // \MudbaseSDK\Model\ConvertAnonymousAccountRequest

try {
    $result = $apiInstance->convertAnonymousAccount($convert_anonymous_account_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->convertAnonymousAccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **convert_anonymous_account_request** | [**\MudbaseSDK\Model\ConvertAnonymousAccountRequest**](../Model/ConvertAnonymousAccountRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\ConvertAnonymousAccount200Response**](../Model/ConvertAnonymousAccount200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createAnonymousSession()`

```php
createAnonymousSession($create_anonymous_session_request): \MudbaseSDK\Model\CreateAnonymousSession200Response
```

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$create_anonymous_session_request = {"projectId":"685ad30be129932fbb7a1047","deviceId":"device-uuid-123"}; // \MudbaseSDK\Model\CreateAnonymousSessionRequest

try {
    $result = $apiInstance->createAnonymousSession($create_anonymous_session_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->createAnonymousSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_anonymous_session_request** | [**\MudbaseSDK\Model\CreateAnonymousSessionRequest**](../Model/CreateAnonymousSessionRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\CreateAnonymousSession200Response**](../Model/CreateAnonymousSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getAvailableOAuthProviders()`

```php
getAvailableOAuthProviders(): \MudbaseSDK\Model\GetAvailableOAuthProviders200Response
```

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getAvailableOAuthProviders();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->getAvailableOAuthProviders: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\MudbaseSDK\Model\GetAvailableOAuthProviders200Response**](../Model/GetAvailableOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCurrentSession()`

```php
getCurrentSession(): \MudbaseSDK\Model\SessionResponse
```

Get current session

Get the current authenticated user session information. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCurrentSession();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->getCurrentSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\MudbaseSDK\Model\SessionResponse**](../Model/SessionResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getLocalSession()`

```php
getLocalSession($project_id): \MudbaseSDK\Model\GetLocalSession200Response
```

Get current session (project-based)

Get the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getLocalSession($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->getLocalSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\GetLocalSession200Response**](../Model/GetLocalSession200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrgOAuthProviders()`

```php
getOrgOAuthProviders(): \MudbaseSDK\Model\GetOrgOAuthProviders200Response
```

Get available OAuth providers for organization-based auth

Returns a list of OAuth providers that are configured and available for organization-based authentication. Providers are configured via environment variables (e.g., GOOGLE_CLIENT_ID, GITHUB_CLIENT_ID).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getOrgOAuthProviders();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->getOrgOAuthProviders: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\MudbaseSDK\Model\GetOrgOAuthProviders200Response**](../Model/GetOrgOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `initiateOAuth()`

```php
initiateOAuth($provider, $project_id, $redirect_url)
```

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. Returns an HTTP 302 redirect to the OAuth provider's consent screen. Note: Swagger \"Try it out\" may show \"Failed to fetch\" for this endpoint due to browser CORS restrictions on cross-origin redirects. Use top-level browser navigation or curl to test.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = google; // string
$project_id = 685ad30be129932fbb7a1047; // string
$redirect_url = https://client.app/auth/callback; // string | The URL to redirect to after authentication. Must be pre-registered in project settings.

try {
    $apiInstance->initiateOAuth($provider, $project_id, $redirect_url);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->initiateOAuth: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**|  | |
| **project_id** | **string**|  | |
| **redirect_url** | **string**| The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional] |

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

## `initiateOrgOAuth()`

```php
initiateOrgOAuth($provider, $redirect_url)
```

Initiate OAuth authentication for organization

Initiates OAuth authentication flow for organization-level signup/login. The OAuth provider must be configured via environment variables (e.g., GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET). After successful authentication, creates a new organization and user account, or logs in existing user.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = google; // string
$redirect_url = https://client.app/auth/callback; // string | The URL to redirect to after authentication

try {
    $apiInstance->initiateOrgOAuth($provider, $redirect_url);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->initiateOrgOAuth: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**|  | |
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

## `loginLocalUser()`

```php
loginLocalUser($login_local_user_request): \MudbaseSDK\Model\LoginLocalUser200Response
```

Login user (project-based)

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$login_local_user_request = {"email":"sarah.chen@example.com","password":"SecurePass123!","projectId":"685ad30be129932fbb7a1047"}; // \MudbaseSDK\Model\LoginLocalUserRequest

try {
    $result = $apiInstance->loginLocalUser($login_local_user_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->loginLocalUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **login_local_user_request** | [**\MudbaseSDK\Model\LoginLocalUserRequest**](../Model/LoginLocalUserRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\LoginLocalUser200Response**](../Model/LoginLocalUser200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `loginUser()`

```php
loginUser($login_request): \MudbaseSDK\Model\AuthResponse
```

Login user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$login_request = {"email":"john.doe@mudbase.dev","password":"SecurePass123!"}; // \MudbaseSDK\Model\LoginRequest

try {
    $result = $apiInstance->loginUser($login_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->loginUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **login_request** | [**\MudbaseSDK\Model\LoginRequest**](../Model/LoginRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `logoutLocalUser()`

```php
logoutLocalUser(): \MudbaseSDK\Model\MessageResponse
```

Logout user (project-based)

Logout the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->logoutLocalUser();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->logoutLocalUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `logoutUser()`

```php
logoutUser(): \MudbaseSDK\Model\MessageResponse
```

Logout user

Logout the current authenticated user session. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->logoutUser();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->logoutUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `oauthCallback()`

```php
oauthCallback($provider)
```

OAuth callback handler (project-based)

Handles OAuth callback for project-based authentication. This route must be matched before /api/auth/oauth/{provider}/{projectId}. Redirects to frontend with query params token, refreshToken, and expiresIn.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = 'provider_example'; // string

try {
    $apiInstance->oauthCallback($provider);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->oauthCallback: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**|  | |

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

## `orgOAuthCallback()`

```php
orgOAuthCallback($provider, $code, $state)
```

OAuth callback handler for organization

Handles OAuth callback for organization-based authentication. Creates a new organization and user account if the user doesn't exist, or logs in existing user. Redirects to frontend with query params token, refreshToken, and expiresIn.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider = google; // string
$code = 'code_example'; // string | Authorization code from OAuth provider
$state = 'state_example'; // string | State parameter for CSRF protection

try {
    $apiInstance->orgOAuthCallback($provider, $code, $state);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->orgOAuthCallback: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provider** | **string**|  | |
| **code** | **string**| Authorization code from OAuth provider | [optional] |
| **state** | **string**| State parameter for CSRF protection | [optional] |

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

## `refreshToken()`

```php
refreshToken($refresh_token_request): \MudbaseSDK\Model\RefreshToken200Response
```

Refresh access token (org and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **org-based** (platform/dashboard) and **project-based** auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$refresh_token_request = {"refreshToken":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."}; // \MudbaseSDK\Model\RefreshTokenRequest

try {
    $result = $apiInstance->refreshToken($refresh_token_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->refreshToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **refresh_token_request** | [**\MudbaseSDK\Model\RefreshTokenRequest**](../Model/RefreshTokenRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\RefreshToken200Response**](../Model/RefreshToken200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `registerLocalUser()`

```php
registerLocalUser($register_local_user_request): \MudbaseSDK\Model\RegisterLocalUser201Response
```

Register new user (project-based)

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$register_local_user_request = {"email":"sarah.chen@example.com","password":"SecurePass123!","firstName":"Sarah","lastName":"Chen","projectId":"685ad30be129932fbb7a1047"}; // \MudbaseSDK\Model\RegisterLocalUserRequest

try {
    $result = $apiInstance->registerLocalUser($register_local_user_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->registerLocalUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **register_local_user_request** | [**\MudbaseSDK\Model\RegisterLocalUserRequest**](../Model/RegisterLocalUserRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\RegisterLocalUser201Response**](../Model/RegisterLocalUser201Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `registerUser()`

```php
registerUser($register_request): \MudbaseSDK\Model\AuthResponse
```

Register new user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$register_request = {"email":"john.doe@mudbase.dev","password":"SecurePass123!","firstName":"John","lastName":"Doe","orgName":"Mudbase"}; // \MudbaseSDK\Model\RegisterRequest

try {
    $result = $apiInstance->registerUser($register_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->registerUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **register_request** | [**\MudbaseSDK\Model\RegisterRequest**](../Model/RegisterRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestLocalPasswordReset()`

```php
requestLocalPasswordReset($request_local_password_reset_request): \MudbaseSDK\Model\MessageResponse
```

Request password reset (project-based, OTP)

When projectId is provided, sends a 6-digit OTP to the user's email (project-based reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$request_local_password_reset_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047"}; // \MudbaseSDK\Model\RequestLocalPasswordResetRequest

try {
    $result = $apiInstance->requestLocalPasswordReset($request_local_password_reset_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->requestLocalPasswordReset: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **request_local_password_reset_request** | [**\MudbaseSDK\Model\RequestLocalPasswordResetRequest**](../Model/RequestLocalPasswordResetRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestPasswordReset()`

```php
requestPasswordReset($request_password_reset_request): \MudbaseSDK\Model\MessageResponse
```

Request password reset (organization / platform)

Sends a password reset link to the user's email. Use this for organization (platform) accounts. For project-based accounts use POST /api/auth/local/password-reset with projectId (sends OTP instead).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$request_password_reset_request = {"email":"john.doe@mudbase.dev"}; // \MudbaseSDK\Model\RequestPasswordResetRequest

try {
    $result = $apiInstance->requestPasswordReset($request_password_reset_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->requestPasswordReset: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **request_password_reset_request** | [**\MudbaseSDK\Model\RequestPasswordResetRequest**](../Model/RequestPasswordResetRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resendVerificationAuth()`

```php
resendVerificationAuth($resend_verification_auth_request): \MudbaseSDK\Model\MessageResponse
```

Resend verification email (no auth)

Sends a new verification email to the given email (and optional project). For unauthenticated users who have not verified yet. Rate limited (e.g. 3 per 15 min per IP).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$resend_verification_auth_request = {"email":"user@example.com"}; // \MudbaseSDK\Model\ResendVerificationAuthRequest

try {
    $result = $apiInstance->resendVerificationAuth($resend_verification_auth_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->resendVerificationAuth: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **resend_verification_auth_request** | [**\MudbaseSDK\Model\ResendVerificationAuthRequest**](../Model/ResendVerificationAuthRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resetLocalPassword()`

```php
resetLocalPassword($token, $reset_local_password_request): \MudbaseSDK\Model\MessageResponse
```

Reset password with token (project-based, legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for project-based resets.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$token = 'token_example'; // string
$reset_local_password_request = {"password":"NewSecurePass123!","projectId":"685ad30be129932fbb7a1047"}; // \MudbaseSDK\Model\ResetLocalPasswordRequest

try {
    $result = $apiInstance->resetLocalPassword($token, $reset_local_password_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->resetLocalPassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **token** | **string**|  | |
| **reset_local_password_request** | [**\MudbaseSDK\Model\ResetLocalPasswordRequest**](../Model/ResetLocalPasswordRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resetPassword()`

```php
resetPassword($token, $reset_password_request): \MudbaseSDK\Model\MessageResponse
```

Reset password with token (organization / platform)

Set new password using the token from the reset link. Validate the token first with POST /api/auth/password-reset/validate before showing the form. If the user's email was not yet verified, it is marked as verified upon successful reset.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$token = 'token_example'; // string
$reset_password_request = {"password":"NewSecurePass123!"}; // \MudbaseSDK\Model\ResetPasswordRequest

try {
    $result = $apiInstance->resetPassword($token, $reset_password_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->resetPassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **token** | **string**|  | |
| **reset_password_request** | [**\MudbaseSDK\Model\ResetPasswordRequest**](../Model/ResetPasswordRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendMagicLink()`

```php
sendMagicLink($magic_link_request): \MudbaseSDK\Model\MessageResponse
```

Send magic link

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$magic_link_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","redirectUrl":"https://app.example.com/auth/callback"}; // \MudbaseSDK\Model\MagicLinkRequest

try {
    $result = $apiInstance->sendMagicLink($magic_link_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->sendMagicLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **magic_link_request** | [**\MudbaseSDK\Model\MagicLinkRequest**](../Model/MagicLinkRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendOTP()`

```php
sendOTP($otp_send_request): \MudbaseSDK\Model\MessageResponse
```

Send OTP code

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$otp_send_request = {"email":"user@example.com","projectId":"685ad30be129932fbb7a1047","method":"email"}; // \MudbaseSDK\Model\OTPSendRequest

try {
    $result = $apiInstance->sendOTP($otp_send_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->sendOTP: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **otp_send_request** | [**\MudbaseSDK\Model\OTPSendRequest**](../Model/OTPSendRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `validatePasswordResetToken()`

```php
validatePasswordResetToken($validate_password_reset_token_request): \MudbaseSDK\Model\ValidatePasswordResetToken200Response
```

Validate password reset token

Call before showing the \"set new password\" form. Validates that the token from the reset link is still valid and not expired. Organization (platform) reset only.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$validate_password_reset_token_request = {"token":"abc123..."}; // \MudbaseSDK\Model\ValidatePasswordResetTokenRequest

try {
    $result = $apiInstance->validatePasswordResetToken($validate_password_reset_token_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->validatePasswordResetToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **validate_password_reset_token_request** | [**\MudbaseSDK\Model\ValidatePasswordResetTokenRequest**](../Model/ValidatePasswordResetTokenRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\ValidatePasswordResetToken200Response**](../Model/ValidatePasswordResetToken200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyEmailAuth()`

```php
verifyEmailAuth($verify_email_auth_request): \MudbaseSDK\Model\MessageResponse
```

Verify email address (no auth)

Verifies the user's email using the token from the link sent at signup. Use this for both organization and project signups (unauthenticated). Same behavior as POST /api/users/verify-email.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$verify_email_auth_request = {"token":"verification-token-from-email-link"}; // \MudbaseSDK\Model\VerifyEmailAuthRequest

try {
    $result = $apiInstance->verifyEmailAuth($verify_email_auth_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->verifyEmailAuth: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **verify_email_auth_request** | [**\MudbaseSDK\Model\VerifyEmailAuthRequest**](../Model/VerifyEmailAuthRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyMagicLink()`

```php
verifyMagicLink($verify_magic_link_request): \MudbaseSDK\Model\AuthResponse
```

Verify magic link

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$verify_magic_link_request = {"token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJwcm9qZWN0SWQiOiI2ODVhZDMwYmUxMjk5MzJmYmI3YTEwNDciLCJpYXQiOjE3NTA3ODA4OTgsImV4cCI6MTc1MDc4NDQ5OH0.example"}; // \MudbaseSDK\Model\VerifyMagicLinkRequest

try {
    $result = $apiInstance->verifyMagicLink($verify_magic_link_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->verifyMagicLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **verify_magic_link_request** | [**\MudbaseSDK\Model\VerifyMagicLinkRequest**](../Model/VerifyMagicLinkRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyOTP()`

```php
verifyOTP($otp_verify_request): \MudbaseSDK\Model\AuthResponse
```

Verify OTP code

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new MudbaseSDK\Api\AuthenticationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$otp_verify_request = {"identifier":"user@example.com","otp":"123456","projectId":"685ad30be129932fbb7a1047"}; // \MudbaseSDK\Model\OTPVerifyRequest

try {
    $result = $apiInstance->verifyOTP($otp_verify_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AuthenticationApi->verifyOTP: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **otp_verify_request** | [**\MudbaseSDK\Model\OTPVerifyRequest**](../Model/OTPVerifyRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AuthResponse**](../Model/AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
