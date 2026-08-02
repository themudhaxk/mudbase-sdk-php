# OpenAPI\Client\ProjectsApi

Project management and configuration. GET /api/projects/{projectId}/dashboard/overview returns the full dashboard KPI bundle (usage, active users, org-wide uptime/latency, 14d volume, recent activity).

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**configureOAuthProvider()**](ProjectsApi.md#configureOAuthProvider) | **POST** /api/auth/oauth/projects/{projectId}/providers/{provider} | Configure OAuth provider for a project |
| [**createProject()**](ProjectsApi.md#createProject) | **POST** /api/projects/{orgId}/projects | Create new project |
| [**deleteProject()**](ProjectsApi.md#deleteProject) | **DELETE** /api/projects/{orgId}/projects/{id} | Delete project |
| [**getOAuthProviderConfig()**](ProjectsApi.md#getOAuthProviderConfig) | **GET** /api/auth/oauth/projects/{projectId}/providers/{provider} | Get OAuth provider configuration |
| [**getProject()**](ProjectsApi.md#getProject) | **GET** /api/projects/{orgId}/projects/{id} | Get single project |
| [**getProjectCaptchaConfig()**](ProjectsApi.md#getProjectCaptchaConfig) | **GET** /api/projects/{orgId}/projects/{id}/auth/captcha | Get project CAPTCHA configuration |
| [**getProjectDashboardOverview()**](ProjectsApi.md#getProjectDashboardOverview) | **GET** /api/projects/{projectId}/dashboard/overview | Project dashboard overview |
| [**getProjectOAuthProviders()**](ProjectsApi.md#getProjectOAuthProviders) | **GET** /api/auth/oauth/projects/{projectId}/providers | Get configured OAuth providers for a project |
| [**getProjectUsage()**](ProjectsApi.md#getProjectUsage) | **GET** /api/projects/{orgId}/projects/{id}/usage | Get project usage statistics |
| [**listProjects()**](ProjectsApi.md#listProjects) | **GET** /api/projects/{orgId}/projects | List all projects |
| [**updateOAuthProviderConfig()**](ProjectsApi.md#updateOAuthProviderConfig) | **PATCH** /api/auth/oauth/projects/{projectId}/providers/{provider} | Update OAuth provider configuration |
| [**updateProject()**](ProjectsApi.md#updateProject) | **PATCH** /api/projects/{orgId}/projects/{id} | Update project |
| [**uploadProjectLogo()**](ProjectsApi.md#uploadProjectLogo) | **POST** /api/projects/{id}/logo | Upload project logo (by project ID) |
| [**uploadProjectLogoByOrg()**](ProjectsApi.md#uploadProjectLogoByOrg) | **POST** /api/projects/{orgId}/projects/{id}/logo | Upload project logo (by org and project ID) |


## `configureOAuthProvider()`

```php
configureOAuthProvider($project_id, $provider, $configure_o_auth_provider_request): \OpenAPI\Client\Model\ConfigureOAuthProvider200Response
```

Configure OAuth provider for a project

Creates or updates the configuration for an OAuth provider for the specified project

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$provider = google; // string
$configure_o_auth_provider_request = {"enabled":true,"clientId":"123456789-abcdefghijklmnop.apps.googleusercontent.com","clientSecret":"GOCSPX-abcdefghijklmnopqrstuvwxyz","scope":["profile","email"],"displayName":"Sign in with Google"}; // \OpenAPI\Client\Model\ConfigureOAuthProviderRequest

try {
    $result = $apiInstance->configureOAuthProvider($project_id, $provider, $configure_o_auth_provider_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->configureOAuthProvider: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **provider** | **string**|  | |
| **configure_o_auth_provider_request** | [**\OpenAPI\Client\Model\ConfigureOAuthProviderRequest**](../Model/ConfigureOAuthProviderRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ConfigureOAuthProvider200Response**](../Model/ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createProject()`

```php
createProject($org_id, $create_project_request): \OpenAPI\Client\Model\CreateProject201Response
```

Create new project

Create a new project in an organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$create_project_request = {"name":"My New Project","description":"A new project description","orgId":"685acbe0e129932fbb7a0fc3"}; // \OpenAPI\Client\Model\CreateProjectRequest

try {
    $result = $apiInstance->createProject($org_id, $create_project_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->createProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **create_project_request** | [**\OpenAPI\Client\Model\CreateProjectRequest**](../Model/CreateProjectRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreateProject201Response**](../Model/CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteProject()`

```php
deleteProject($org_id, $id): \OpenAPI\Client\Model\MessageResponse
```

Delete project

Delete a project permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID

try {
    $result = $apiInstance->deleteProject($org_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->deleteProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |

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

## `getOAuthProviderConfig()`

```php
getOAuthProviderConfig($project_id, $provider): \OpenAPI\Client\Model\GetOAuthProviderConfig200Response
```

Get OAuth provider configuration

Returns the configuration for a specific OAuth provider for the project (without sensitive data)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$provider = google; // string

try {
    $result = $apiInstance->getOAuthProviderConfig($project_id, $provider);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getOAuthProviderConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **provider** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetOAuthProviderConfig200Response**](../Model/GetOAuthProviderConfig200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProject()`

```php
getProject($org_id, $id): \OpenAPI\Client\Model\Project
```

Get single project

Get project details by ID. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID

try {
    $result = $apiInstance->getProject($org_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |

### Return type

[**\OpenAPI\Client\Model\Project**](../Model/Project.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectCaptchaConfig()`

```php
getProjectCaptchaConfig($org_id, $id): \OpenAPI\Client\Model\GetProjectCaptchaConfig200Response
```

Get project CAPTCHA configuration

Get CAPTCHA configuration for a project. This is a public endpoint that returns the site key  and settings needed for frontend integration. Secret key is never returned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID

try {
    $result = $apiInstance->getProjectCaptchaConfig($org_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getProjectCaptchaConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |

### Return type

[**\OpenAPI\Client\Model\GetProjectCaptchaConfig200Response**](../Model/GetProjectCaptchaConfig200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectDashboardOverview()`

```php
getProjectDashboardOverview($project_id): \OpenAPI\Client\Model\ProjectDashboardOverviewResponse
```

Project dashboard overview

Single response for the project overview UI: project info, request counts and day-over-day % change, active users (distinct JWT users with project activity; realtime socket count when available), **Uptime** (30d headline) is organization-wide when enough HTTP samples exist, else DB heartbeat probes. **Average latency** (today / 7d) is **per project** and counts only routes documented in `openapi-docs.yaml` for customer/project API (excludes auth, `/api/users`, `/api/orgs`, role-elevation, and multi-role admin routes). Request volume and active users remain per-project. 14-day API call volume and recent audit activity are per-project. See docs/dashboard-overview-api.md.

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


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getProjectDashboardOverview($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getProjectDashboardOverview: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\ProjectDashboardOverviewResponse**](../Model/ProjectDashboardOverviewResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectOAuthProviders()`

```php
getProjectOAuthProviders($project_id): \OpenAPI\Client\Model\GetProjectOAuthProviders200Response
```

Get configured OAuth providers for a project

Returns a list of OAuth providers that are configured and enabled for the specified project

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string

try {
    $result = $apiInstance->getProjectOAuthProviders($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getProjectOAuthProviders: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetProjectOAuthProviders200Response**](../Model/GetProjectOAuthProviders200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectUsage()`

```php
getProjectUsage($org_id, $id): \OpenAPI\Client\Model\ProjectUsageResponse
```

Get project usage statistics

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID

try {
    $result = $apiInstance->getProjectUsage($org_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->getProjectUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |

### Return type

[**\OpenAPI\Client\Model\ProjectUsageResponse**](../Model/ProjectUsageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listProjects()`

```php
listProjects($org_id): \OpenAPI\Client\Model\ListProjects200Response
```

List all projects

List all projects in an organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID

try {
    $result = $apiInstance->listProjects($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->listProjects: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |

### Return type

[**\OpenAPI\Client\Model\ListProjects200Response**](../Model/ListProjects200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateOAuthProviderConfig()`

```php
updateOAuthProviderConfig($project_id, $provider, $update_o_auth_provider_config_request): \OpenAPI\Client\Model\ConfigureOAuthProvider200Response
```

Update OAuth provider configuration

Updates the configuration for an OAuth provider for the specified project

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 685ad30be129932fbb7a1047; // string
$provider = google; // string
$update_o_auth_provider_config_request = {"enabled":true,"clientId":"123456789-abcdefghijklmnop.apps.googleusercontent.com","clientSecret":"GOCSPX-abcdefghijklmnopqrstuvwxyz","scope":["profile","email"],"displayName":"Sign in with Google"}; // \OpenAPI\Client\Model\UpdateOAuthProviderConfigRequest

try {
    $result = $apiInstance->updateOAuthProviderConfig($project_id, $provider, $update_o_auth_provider_config_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->updateOAuthProviderConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **provider** | **string**|  | |
| **update_o_auth_provider_config_request** | [**\OpenAPI\Client\Model\UpdateOAuthProviderConfigRequest**](../Model/UpdateOAuthProviderConfigRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ConfigureOAuthProvider200Response**](../Model/ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateProject()`

```php
updateProject($org_id, $id, $update_project_request): \OpenAPI\Client\Model\CreateProject201Response
```

Update project

Update project configuration (name, description, settings). **Settings toggles:** **requireEmailVerification** (default true) — when on, new email signups do not get a token until they verify; login is blocked until verified. **requirePhoneVerification** (default false) — when on, phone/OTP users must verify before token. **defaultUserAccountStatus** — **active** (default) or **pending**; when pending, new users must be approved by org owner/admin before they can perform data/storage operations. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID
$update_project_request = {"name":"Updated Project Name","description":"Updated project description","settings":{"requireEmailVerification":true,"requirePhoneVerification":false,"defaultUserAccountStatus":"active"}}; // \OpenAPI\Client\Model\UpdateProjectRequest

try {
    $result = $apiInstance->updateProject($org_id, $id, $update_project_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->updateProject: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |
| **update_project_request** | [**\OpenAPI\Client\Model\UpdateProjectRequest**](../Model/UpdateProjectRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\CreateProject201Response**](../Model/CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `uploadProjectLogo()`

```php
uploadProjectLogo($id, $logo): \OpenAPI\Client\Model\UploadProjectLogo200Response
```

Upload project logo (by project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field and used in project-related emails and UI. Project is resolved from the authenticated user's org. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB.

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


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | Project ID
$logo = '/path/to/file.txt'; // \SplFileObject | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)

try {
    $result = $apiInstance->uploadProjectLogo($id, $logo);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->uploadProjectLogo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| Project ID | |
| **logo** | **\SplFileObject****\SplFileObject**| Logo image (PNG, JPEG, GIF, or WebP; max 2MB) | |

### Return type

[**\OpenAPI\Client\Model\UploadProjectLogo200Response**](../Model/UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `uploadProjectLogoByOrg()`

```php
uploadProjectLogoByOrg($org_id, $id, $logo): \OpenAPI\Client\Model\UploadProjectLogo200Response
```

Upload project logo (by org and project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. Requires project update permission and membership in the organization.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ProjectsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string | Organization ID
$id = 'id_example'; // string | Project ID
$logo = '/path/to/file.txt'; // \SplFileObject | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)

try {
    $result = $apiInstance->uploadProjectLogoByOrg($org_id, $id, $logo);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProjectsApi->uploadProjectLogoByOrg: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**| Organization ID | |
| **id** | **string**| Project ID | |
| **logo** | **\SplFileObject****\SplFileObject**| Logo image (PNG, JPEG, GIF, or WebP; max 2MB) | |

### Return type

[**\OpenAPI\Client\Model\UploadProjectLogo200Response**](../Model/UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
