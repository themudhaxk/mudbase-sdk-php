# MudbaseSDK\OrganizationsApi

Organization and team management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addOrgCustomDomain()**](OrganizationsApi.md#addOrgCustomDomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add a custom domain |
| [**createOrganization()**](OrganizationsApi.md#createOrganization) | **POST** /api/orgs | ~~Create new organization~~ (disabled) |
| [**deleteOrgCustomDomain()**](OrganizationsApi.md#deleteOrgCustomDomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove a custom domain |
| [**deleteOrganization()**](OrganizationsApi.md#deleteOrganization) | **DELETE** /api/orgs/{orgId} | Delete organization |
| [**deleteSubOrganization()**](OrganizationsApi.md#deleteSubOrganization) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Delete sub-organization~~ (deprecated) |
| [**getOrgCustomDomainDnsInstructions()**](OrganizationsApi.md#getOrgCustomDomainDnsInstructions) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/dns-instructions | Get DNS TXT record instructions for one hostname |
| [**getOrganization()**](OrganizationsApi.md#getOrganization) | **GET** /api/orgs/{orgId} | Get organization details by ID |
| [**getOrganizationMembers()**](OrganizationsApi.md#getOrganizationMembers) | **GET** /api/orgs/{orgId}/members | Get organization members |
| [**getOrganizationUsage()**](OrganizationsApi.md#getOrganizationUsage) | **GET** /api/orgs/{orgId}/usage | Get organization usage and billing |
| [**getOrganizationUsers()**](OrganizationsApi.md#getOrganizationUsers) | **GET** /api/orgs/{orgId}/users | List organization users with metadata |
| [**getProjectUsers()**](OrganizationsApi.md#getProjectUsers) | **GET** /api/orgs/{orgId}/projects/{projectId}/users | List project users with metadata |
| [**getSubOrganizations()**](OrganizationsApi.md#getSubOrganizations) | **GET** /api/orgs/{orgId}/suborgs | ~~Get sub-organizations~~ (deprecated) |
| [**getUserOverview()**](OrganizationsApi.md#getUserOverview) | **GET** /api/orgs/{orgId}/users/{userId}/overview | Get user overview and data footprint |
| [**internalCustomDomainAddon()**](OrganizationsApi.md#internalCustomDomainAddon) | **POST** /internal/org/custom-domain-addon | Enable/disable Growth/Scale custom domain add-on (internal) |
| [**internalCustomDomainSweepStatus()**](OrganizationsApi.md#internalCustomDomainSweepStatus) | **GET** /internal/custom-domain/sweep-status | Custom domain background sweep status (internal) |
| [**internalDomainDnsRecheckBatch()**](OrganizationsApi.md#internalDomainDnsRecheckBatch) | **POST** /internal/domain-dns/recheck-batch | Batch DNS re-verification for drift (internal) |
| [**internalProvisionEnterprise()**](OrganizationsApi.md#internalProvisionEnterprise) | **POST** /internal/provision-enterprise | Provision enterprise dedicated API/DB (internal) |
| [**inviteSubOrganizationMember()**](OrganizationsApi.md#inviteSubOrganizationMember) | **POST** /api/orgs/{orgId}/suborgs/{suborgId}/invite | ~~Invite member to sub-organization~~ (deprecated) |
| [**inviteTeamMember()**](OrganizationsApi.md#inviteTeamMember) | **POST** /api/orgs/{orgId}/invite | Invite team member to organization |
| [**listOrgCustomDomains()**](OrganizationsApi.md#listOrgCustomDomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS verification hints |
| [**listOrganizations()**](OrganizationsApi.md#listOrganizations) | **GET** /api/orgs | Get all organizations for user |
| [**orgCustomDomainPlatformReady()**](OrganizationsApi.md#orgCustomDomainPlatformReady) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops that hosting or edge work is ready (email) |
| [**orgCustomDomainSubmitCname()**](OrganizationsApi.md#orgCustomDomainSubmitCname) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-cname | Custom domain step 2 (optional): org confirms routing CNAME was added |
| [**orgCustomDomainSubmitPlatformDnsVerificationDeprecated()**](OrganizationsApi.md#orgCustomDomainSubmitPlatformDnsVerificationDeprecated) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-platform-dns-verification | Deprecated — use POST .../verify-platform-dns |
| [**orgCustomDomainVerifyPlatformDns()**](OrganizationsApi.md#orgCustomDomainVerifyPlatformDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-platform-dns | Custom domain step 3: verify platform DNS (manual TXT or managed certificate readiness) |
| [**patchOrgCustomDomain()**](OrganizationsApi.md#patchOrgCustomDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Update domain status or regenerate verification token |
| [**removeSubOrganizationMember()**](OrganizationsApi.md#removeSubOrganizationMember) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId} | ~~Remove member from sub-organization~~ (deprecated) |
| [**removeTeamMember()**](OrganizationsApi.md#removeTeamMember) | **DELETE** /api/orgs/{orgId}/members/{userId} | Remove team member from organization |
| [**setOrgPrimaryDomain()**](OrganizationsApi.md#setOrgPrimaryDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**updateMemberRole()**](OrganizationsApi.md#updateMemberRole) | **PATCH** /api/orgs/{orgId}/members/{userId}/role | Update member role |
| [**updateOrganization()**](OrganizationsApi.md#updateOrganization) | **PATCH** /api/orgs/{orgId} | Update organization |
| [**updateOrganizationPlan()**](OrganizationsApi.md#updateOrganizationPlan) | **PATCH** /api/orgs/plan/{orgId} | Update organization plan |
| [**updateSubOrganization()**](OrganizationsApi.md#updateSubOrganization) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Update sub-organization~~ (deprecated) |
| [**updateSubOrganizationMemberRole()**](OrganizationsApi.md#updateSubOrganizationMemberRole) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId}/role | ~~Update sub-organization member role~~ (deprecated) |
| [**updateUserAccountStatus()**](OrganizationsApi.md#updateUserAccountStatus) | **PATCH** /api/orgs/{orgId}/users/{userId}/status | Update user account status (activate or suspend) |
| [**verifyOrgCustomDomainDns()**](OrganizationsApi.md#verifyOrgCustomDomainDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain ownership via DNS TXT |


## `addOrgCustomDomain()`

```php
addOrgCustomDomain($org_id, $project_id, $add_org_domain_request): \MudbaseSDK\Model\OrgAddDomainResponse
```

Add a custom domain

Creates a pending domain row; the response **`domain`** uses the compact **`OrgDomainEntryOrgConsole`** shape (**`dnsRecords`** includes the Mudbase ownership TXT). **`dnsRecords`** may include the Mudbase TXT and routing CNAME only until the Mudbase TXT succeeds and the managed certificate is provisioned. **`flyCertificateStatus`** is typically omitted until certificate provisioning runs after the first successful **`verify-dns`**.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$add_org_domain_request = {"hostname":"hostname_example"}; // \MudbaseSDK\Model\AddOrgDomainRequest

try {
    $result = $apiInstance->addOrgCustomDomain($org_id, $project_id, $add_org_domain_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->addOrgCustomDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **add_org_domain_request** | [**\MudbaseSDK\Model\AddOrgDomainRequest**](../Model/AddOrgDomainRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\OrgAddDomainResponse**](../Model/OrgAddDomainResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createOrganization()`

```php
createOrganization($create_organization_request)
```

~~Create new organization~~ (disabled)

~~Create a new organization.~~ This endpoint is disabled and kept only for backward compatibility in documentation. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_organization_request = {"name":"Mudbase Inc","description":"Main organization","logo":"https://example.com/logo.png","website":"https://mudbase.dev","parentOrgId":"685acbe0e129932fbb7a0fc3"}; // \MudbaseSDK\Model\CreateOrganizationRequest

try {
    $apiInstance->createOrganization($create_organization_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->createOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_organization_request** | [**\MudbaseSDK\Model\CreateOrganizationRequest**](../Model/CreateOrganizationRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteOrgCustomDomain()`

```php
deleteOrgCustomDomain($org_id, $project_id, $hostname)
```

Remove a custom domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $apiInstance->deleteOrgCustomDomain($org_id, $project_id, $hostname);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->deleteOrgCustomDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteOrganization()`

```php
deleteOrganization($org_id): \MudbaseSDK\Model\DeleteOrganization200Response
```

Delete organization

Delete an organization permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string

try {
    $result = $apiInstance->deleteOrganization($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->deleteOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\DeleteOrganization200Response**](../Model/DeleteOrganization200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSubOrganization()`

```php
deleteSubOrganization($org_id, $suborg_id): \MudbaseSDK\Model\DeleteSubOrganization200Response
```

~~Delete sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string

try {
    $result = $apiInstance->deleteSubOrganization($org_id, $suborg_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->deleteSubOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **suborg_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\DeleteSubOrganization200Response**](../Model/DeleteSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrgCustomDomainDnsInstructions()`

```php
getOrgCustomDomainDnsInstructions($org_id, $project_id, $hostname): \MudbaseSDK\Model\OrgDnsInstructionsResponse
```

Get DNS TXT record instructions for one hostname

Returns the same shape as list/add for one hostname (URL-encode `hostname` in the path), including **`dnsRecords`** and **`flyCertificateStatus`** when applicable. See **`listOrgCustomDomains`** for how managed certificate provisioning affects those fields.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $result = $apiInstance->getOrgCustomDomainDnsInstructions($org_id, $project_id, $hostname);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getOrgCustomDomainDnsInstructions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgDnsInstructionsResponse**](../Model/OrgDnsInstructionsResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrganization()`

```php
getOrganization($org_id): \MudbaseSDK\Model\Organization
```

Get organization details by ID

Get organization details by ID. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string

try {
    $result = $apiInstance->getOrganization($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\Organization**](../Model/Organization.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrganizationMembers()`

```php
getOrganizationMembers($org_id): \MudbaseSDK\Model\GetOrganizationMembers200Response
```

Get organization members

Get all members of an organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string

try {
    $result = $apiInstance->getOrganizationMembers($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getOrganizationMembers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetOrganizationMembers200Response**](../Model/GetOrganizationMembers200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrganizationUsage()`

```php
getOrganizationUsage($org_id): \MudbaseSDK\Model\GetOrganizationUsage200Response
```

Get organization usage and billing

Get usage statistics and billing information for an organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string

try {
    $result = $apiInstance->getOrganizationUsage($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getOrganizationUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetOrganizationUsage200Response**](../Model/GetOrganizationUsage200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOrganizationUsers()`

```php
getOrganizationUsers($org_id, $status): \MudbaseSDK\Model\GetOrganizationUsers200Response
```

List organization users with metadata

Get all users in the organization with metadata (email, full name, role, accountStatus, phone, lastLogin, etc.). Optional query `status` filters by accountStatus (pending, active, suspended). Requires organization access and owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$status = 'status_example'; // string | Filter by account status (pending, active, suspended)

try {
    $result = $apiInstance->getOrganizationUsers($org_id, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getOrganizationUsers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **status** | **string**| Filter by account status (pending, active, suspended) | [optional] |

### Return type

[**\MudbaseSDK\Model\GetOrganizationUsers200Response**](../Model/GetOrganizationUsers200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectUsers()`

```php
getProjectUsers($org_id, $project_id, $status): \MudbaseSDK\Model\GetProjectUsers200Response
```

List project users with metadata

Get all users in a project with metadata (email, full name, role, accountStatus, etc.). Optional query `status` filters by accountStatus. Project must belong to the organization. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$project_id = 685ad30be129932fbb7a1047; // string
$status = 'status_example'; // string | Filter by account status (pending, active, suspended)

try {
    $result = $apiInstance->getProjectUsers($org_id, $project_id, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getProjectUsers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **status** | **string**| Filter by account status (pending, active, suspended) | [optional] |

### Return type

[**\MudbaseSDK\Model\GetProjectUsers200Response**](../Model/GetProjectUsers200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSubOrganizations()`

```php
getSubOrganizations($org_id): \MudbaseSDK\Model\GetSubOrganizations200Response
```

~~Get sub-organizations~~ (deprecated)

Get all sub-organizations under a parent organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string

try {
    $result = $apiInstance->getSubOrganizations($org_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getSubOrganizations: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetSubOrganizations200Response**](../Model/GetSubOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getUserOverview()`

```php
getUserOverview($org_id, $user_id): \MudbaseSDK\Model\GetUserOverview200Response
```

Get user overview and data footprint

Get a user's profile plus footprint (files count/size, sessions, API keys, collections in project). Use for dashboard to see everything tied to the user. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$user_id = 'user_id_example'; // string

try {
    $result = $apiInstance->getUserOverview($org_id, $user_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->getUserOverview: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **user_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetUserOverview200Response**](../Model/GetUserOverview200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `internalCustomDomainAddon()`

```php
internalCustomDomainAddon($internal_custom_domain_addon_request)
```

Enable/disable Growth/Scale custom domain add-on (internal)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: InternalApiKey
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$internal_custom_domain_addon_request = {"orgId":"orgId_example","enabled":true}; // \MudbaseSDK\Model\InternalCustomDomainAddonRequest

try {
    $apiInstance->internalCustomDomainAddon($internal_custom_domain_addon_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalCustomDomainAddon: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **internal_custom_domain_addon_request** | [**\MudbaseSDK\Model\InternalCustomDomainAddonRequest**](../Model/InternalCustomDomainAddonRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../../README.md#InternalApiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `internalCustomDomainSweepStatus()`

```php
internalCustomDomainSweepStatus()
```

Custom domain background sweep status (internal)

Returns the last automated custom-domain sweep (TXT recheck + certificate provisioning retry), job env flags, and deploy troubleshooting hints when the proxy reports the app is not listening on 0.0.0.0:PORT. Requires header `X-Internal-Api-Key` (same as other /internal routes).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: InternalApiKey
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->internalCustomDomainSweepStatus();
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalCustomDomainSweepStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../../README.md#InternalApiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `internalDomainDnsRecheckBatch()`

```php
internalDomainDnsRecheckBatch($internal_domain_dns_recheck_batch_request)
```

Batch DNS re-verification for drift (internal)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: InternalApiKey
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$internal_domain_dns_recheck_batch_request = {"maxOrgs":1,"recheckOlderThanHours":1}; // \MudbaseSDK\Model\InternalDomainDnsRecheckBatchRequest

try {
    $apiInstance->internalDomainDnsRecheckBatch($internal_domain_dns_recheck_batch_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalDomainDnsRecheckBatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **internal_domain_dns_recheck_batch_request** | [**\MudbaseSDK\Model\InternalDomainDnsRecheckBatchRequest**](../Model/InternalDomainDnsRecheckBatchRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../../README.md#InternalApiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `internalProvisionEnterprise()`

```php
internalProvisionEnterprise($provision_enterprise_request)
```

Provision enterprise dedicated API/DB (internal)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: InternalApiKey
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = MudbaseSDK\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$provision_enterprise_request = {"orgId":"orgId_example","provisionRequestId":"provisionRequestId_example","apiBaseUrl":"apiBaseUrl_example","dbRef":"dbRef_example","serverId":"serverId_example"}; // \MudbaseSDK\Model\ProvisionEnterpriseRequest

try {
    $apiInstance->internalProvisionEnterprise($provision_enterprise_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalProvisionEnterprise: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provision_enterprise_request** | [**\MudbaseSDK\Model\ProvisionEnterpriseRequest**](../Model/ProvisionEnterpriseRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../../README.md#InternalApiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `inviteSubOrganizationMember()`

```php
inviteSubOrganizationMember($org_id, $suborg_id, $invite_member_request): \MudbaseSDK\Model\InviteSubOrganizationMember200Response
```

~~Invite member to sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$invite_member_request = {"email":"user@suborg.example.com","role":"viewer"}; // \MudbaseSDK\Model\InviteMemberRequest

try {
    $result = $apiInstance->inviteSubOrganizationMember($org_id, $suborg_id, $invite_member_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->inviteSubOrganizationMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **suborg_id** | **string**|  | |
| **invite_member_request** | [**\MudbaseSDK\Model\InviteMemberRequest**](../Model/InviteMemberRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\InviteSubOrganizationMember200Response**](../Model/InviteSubOrganizationMember200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `inviteTeamMember()`

```php
inviteTeamMember($org_id, $invite_member_request): \MudbaseSDK\Model\InviteTeamMember200Response
```

Invite team member to organization

Send an invitation to a user to join the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$invite_member_request = {"email":"newuser@example.com","role":"member"}; // \MudbaseSDK\Model\InviteMemberRequest

try {
    $result = $apiInstance->inviteTeamMember($org_id, $invite_member_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->inviteTeamMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **invite_member_request** | [**\MudbaseSDK\Model\InviteMemberRequest**](../Model/InviteMemberRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\InviteTeamMember200Response**](../Model/InviteTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listOrgCustomDomains()`

```php
listOrgCustomDomains($org_id, $project_id): \MudbaseSDK\Model\OrgDomainsListResponse
```

List custom domains and DNS verification hints

Returns allowed hostnames for **this project**, primary hostname (per project), API base URL, and per-domain DNS guidance.  Each row uses **`dnsRecords`** for the Mudbase ownership TXT (purpose **`mudbase_ownership`**) and the routing **CNAME** target that Mudbase provisions for the hostname (else the platform default target). Once the ownership TXT has passed at least once, Mudbase provisions and manages the TLS certificate for the hostname automatically and may add further checklist rows (for example `acme_challenge`) needed to complete certificate issuance. The certificate status field mirrors the managed certificate’s state during issuance (e.g. `pending_validation`, `active`).  Managed edge TLS details are present only on deployments that serve managed edge certificates.  Requires Growth, Scale, or Enterprise plan (custom domains included in plan features).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->listOrgCustomDomains($org_id, $project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->listOrgCustomDomains: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgDomainsListResponse**](../Model/OrgDomainsListResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listOrganizations()`

```php
listOrganizations(): \MudbaseSDK\Model\ListOrganizations200Response
```

Get all organizations for user

Get all organizations the authenticated user belongs to. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listOrganizations();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->listOrganizations: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\MudbaseSDK\Model\ListOrganizations200Response**](../Model/ListOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `orgCustomDomainPlatformReady()`

```php
orgCustomDomainPlatformReady($org_id, $project_id, $hostname, $org_custom_domain_platform_ready_request)
```

Notify platform ops that hosting or edge work is ready (email)

Legacy optional ping: ops are emailed automatically on first successful Mudbase TXT verify. Use this only for an extra nudge. Sends an email to ops while the domain is in platform setup (after Mudbase TXT verification through later pipeline states). Recipients default to `admin@mudhaxkservices.com` and `admin@mudbase.dev` when `CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS` is unset; override with that env (comma/space-separated). Returns **503** `email_provider_not_configured` if the platform email provider is not configured.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string
$org_custom_domain_platform_ready_request = {"note":"note_example"}; // \MudbaseSDK\Model\OrgCustomDomainPlatformReadyRequest

try {
    $apiInstance->orgCustomDomainPlatformReady($org_id, $project_id, $hostname, $org_custom_domain_platform_ready_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->orgCustomDomainPlatformReady: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |
| **org_custom_domain_platform_ready_request** | [**\MudbaseSDK\Model\OrgCustomDomainPlatformReadyRequest**](../Model/OrgCustomDomainPlatformReadyRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `orgCustomDomainSubmitCname()`

```php
orgCustomDomainSubmitCname($org_id, $project_id, $hostname): \MudbaseSDK\Model\OrgPatchDomainResponse
```

Custom domain step 2 (optional): org confirms routing CNAME was added

Usually unnecessary. With automated certificate provisioning, the Mudbase TXT verify may already set `cname_approved`. Legacy pipelines may queue `cname_pending_staff` until staff **`approve-cname`**. Use **`routingCnameTarget`** from **`GET .../projects/{projectId}/domains`** (the managed routing CNAME target when provisioned, else the platform default target).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $result = $apiInstance->orgCustomDomainSubmitCname($org_id, $project_id, $hostname);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->orgCustomDomainSubmitCname: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `orgCustomDomainSubmitPlatformDnsVerificationDeprecated()`

```php
orgCustomDomainSubmitPlatformDnsVerificationDeprecated($org_id, $project_id, $hostname): \MudbaseSDK\Model\OrgPatchDomainResponse
```

Deprecated — use POST .../verify-platform-dns

Deprecated alias of **`orgCustomDomainVerifyPlatformDns`** (same behavior: manual TXT and/or automated certificate provisioning per deployment).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $result = $apiInstance->orgCustomDomainSubmitPlatformDnsVerificationDeprecated($org_id, $project_id, $hostname);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->orgCustomDomainSubmitPlatformDnsVerificationDeprecated: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `orgCustomDomainVerifyPlatformDns()`

```php
orgCustomDomainVerifyPlatformDns($org_id, $project_id, $hostname): \MudbaseSDK\Model\OrgPatchDomainResponse
```

Custom domain step 3: verify platform DNS (manual TXT or managed certificate readiness)

**Manual path:** After staff **`PATCH .../platform-dns-verification`**, the org adds the published TXT and calls this endpoint. The API resolves public TXT at **`platformDnsVerification.recordName`** and matches **`recordValue`**. On success, `status` → **`platform_dns_pending_review`** until staff **`POST .../activate`**.  **Automated path (default):** When automated certificate provisioning is in effect, the org calls this after the Mudbase TXT and the certificate DNS rows are in place (status typically **`cname_approved`** from automated verify-dns). The API checks the managed certificate with bounded retries. On success, `status` → **`active`** and the org may receive the activation email, with no staff **`approve-cname`** or **`activate`** required.  **Legacy path:** In the legacy staff pipeline, staff **`approve-cname`** may be required first; after the managed certificate is ready, **`status`** becomes **`active`** on auto-activation, else **`platform_dns_pending_review`** until staff **`activate`**.  **`platform_dns_verification_failed`** may include **`details.flyStatus`** / **`details.flyError`** with provisioning error context.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $result = $apiInstance->orgCustomDomainVerifyPlatformDns($org_id, $project_id, $hostname);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->orgCustomDomainVerifyPlatformDns: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `patchOrgCustomDomain()`

```php
patchOrgCustomDomain($org_id, $project_id, $hostname, $patch_org_domain_request): \MudbaseSDK\Model\OrgPatchDomainResponse
```

Update domain status or regenerate verification token

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string
$patch_org_domain_request = {"status":"pending","regenerateToken":true}; // \MudbaseSDK\Model\PatchOrgDomainRequest

try {
    $result = $apiInstance->patchOrgCustomDomain($org_id, $project_id, $hostname, $patch_org_domain_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->patchOrgCustomDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |
| **patch_org_domain_request** | [**\MudbaseSDK\Model\PatchOrgDomainRequest**](../Model/PatchOrgDomainRequest.md)|  | [optional] |

### Return type

[**\MudbaseSDK\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeSubOrganizationMember()`

```php
removeSubOrganizationMember($org_id, $suborg_id, $user_id): \MudbaseSDK\Model\RemoveTeamMember200Response
```

~~Remove member from sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string

try {
    $result = $apiInstance->removeSubOrganizationMember($org_id, $suborg_id, $user_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->removeSubOrganizationMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **suborg_id** | **string**|  | |
| **user_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\RemoveTeamMember200Response**](../Model/RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeTeamMember()`

```php
removeTeamMember($org_id, $user_id): \MudbaseSDK\Model\RemoveTeamMember200Response
```

Remove team member from organization

Remove a user from the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string

try {
    $result = $apiInstance->removeTeamMember($org_id, $user_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->removeTeamMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **user_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\RemoveTeamMember200Response**](../Model/RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `setOrgPrimaryDomain()`

```php
setOrgPrimaryDomain($org_id, $project_id, $set_org_primary_domain_request)
```

Set primary custom domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$set_org_primary_domain_request = {"hostname":"hostname_example"}; // \MudbaseSDK\Model\SetOrgPrimaryDomainRequest

try {
    $apiInstance->setOrgPrimaryDomain($org_id, $project_id, $set_org_primary_domain_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->setOrgPrimaryDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **set_org_primary_domain_request** | [**\MudbaseSDK\Model\SetOrgPrimaryDomainRequest**](../Model/SetOrgPrimaryDomainRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMemberRole()`

```php
updateMemberRole($org_id, $user_id, $update_member_role_request): \MudbaseSDK\Model\UpdateMemberRole200Response
```

Update member role

Update a member's role in the organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string
$update_member_role_request = {"role":"admin"}; // \MudbaseSDK\Model\UpdateMemberRoleRequest

try {
    $result = $apiInstance->updateMemberRole($org_id, $user_id, $update_member_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateMemberRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **user_id** | **string**|  | |
| **update_member_role_request** | [**\MudbaseSDK\Model\UpdateMemberRoleRequest**](../Model/UpdateMemberRoleRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateMemberRole200Response**](../Model/UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateOrganization()`

```php
updateOrganization($org_id, $update_organization_request): \MudbaseSDK\Model\UpdateOrganization200Response
```

Update organization

Update organization details. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$update_organization_request = {"name":"Mudbase Inc Updated","description":"Updated organization description","logo":"https://example.com/new-logo.png","website":"https://mudbase.dev"}; // \MudbaseSDK\Model\UpdateOrganizationRequest

try {
    $result = $apiInstance->updateOrganization($org_id, $update_organization_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **update_organization_request** | [**\MudbaseSDK\Model\UpdateOrganizationRequest**](../Model/UpdateOrganizationRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateOrganization200Response**](../Model/UpdateOrganization200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateOrganizationPlan()`

```php
updateOrganizationPlan($org_id, $update_organization_plan_request): \MudbaseSDK\Model\UpdateOrganizationPlan200Response
```

Update organization plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$update_organization_plan_request = {"plan":"pro"}; // \MudbaseSDK\Model\UpdateOrganizationPlanRequest

try {
    $result = $apiInstance->updateOrganizationPlan($org_id, $update_organization_plan_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateOrganizationPlan: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **update_organization_plan_request** | [**\MudbaseSDK\Model\UpdateOrganizationPlanRequest**](../Model/UpdateOrganizationPlanRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateOrganizationPlan200Response**](../Model/UpdateOrganizationPlan200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSubOrganization()`

```php
updateSubOrganization($org_id, $suborg_id, $update_organization_request): \MudbaseSDK\Model\UpdateSubOrganization200Response
```

~~Update sub-organization~~ (deprecated)

Update a sub-organization's configuration. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$update_organization_request = {"name":"Sub-Organization Updated","description":"Updated sub-organization description","logo":"https://example.com/sub-logo.png","website":"https://sub.mudbase.dev"}; // \MudbaseSDK\Model\UpdateOrganizationRequest

try {
    $result = $apiInstance->updateSubOrganization($org_id, $suborg_id, $update_organization_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateSubOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **suborg_id** | **string**|  | |
| **update_organization_request** | [**\MudbaseSDK\Model\UpdateOrganizationRequest**](../Model/UpdateOrganizationRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateSubOrganization200Response**](../Model/UpdateSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSubOrganizationMemberRole()`

```php
updateSubOrganizationMemberRole($org_id, $suborg_id, $user_id, $update_member_role_request): \MudbaseSDK\Model\UpdateMemberRole200Response
```

~~Update sub-organization member role~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string
$update_member_role_request = {"role":"admin"}; // \MudbaseSDK\Model\UpdateMemberRoleRequest

try {
    $result = $apiInstance->updateSubOrganizationMemberRole($org_id, $suborg_id, $user_id, $update_member_role_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateSubOrganizationMemberRole: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **suborg_id** | **string**|  | |
| **user_id** | **string**|  | |
| **update_member_role_request** | [**\MudbaseSDK\Model\UpdateMemberRoleRequest**](../Model/UpdateMemberRoleRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateMemberRole200Response**](../Model/UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateUserAccountStatus()`

```php
updateUserAccountStatus($org_id, $user_id, $update_user_account_status_request): \MudbaseSDK\Model\UpdateUserAccountStatus200Response
```

Update user account status (activate or suspend)

Set a user's account status to active or suspended. Used to approve pending users or suspend/activate accounts. Cannot change status of an organization owner. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$user_id = 'user_id_example'; // string
$update_user_account_status_request = {"accountStatus":"active"}; // \MudbaseSDK\Model\UpdateUserAccountStatusRequest

try {
    $result = $apiInstance->updateUserAccountStatus($org_id, $user_id, $update_user_account_status_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->updateUserAccountStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **user_id** | **string**|  | |
| **update_user_account_status_request** | [**\MudbaseSDK\Model\UpdateUserAccountStatusRequest**](../Model/UpdateUserAccountStatusRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\UpdateUserAccountStatus200Response**](../Model/UpdateUserAccountStatus200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyOrgCustomDomainDns()`

```php
verifyOrgCustomDomainDns($org_id, $project_id, $hostname): \MudbaseSDK\Model\OrgVerifyCustomDomainDnsSuccessResponse
```

Verify domain ownership via DNS TXT

Looks up TXT at `_mudbase-verify.<hostname>` for value `mudbase-domain-verification=<token>`.  On a successful verify, Mudbase begins provisioning and managing the TLS certificate for the hostname automatically. Depending on the deployment, the response may include managed edge TLS details with domain-control validation (DCV) hints for the certificate.  When automated certificate provisioning is in effect, a successful verify records the certificate’s DNS requirements and status may advance to **`cname_approved`** in the same response (no staff **`approve-cname`** step). Otherwise, first success from `pending`/`failed` may move to **`cname_pending_staff`** and queue platform review as before.  The **200** response may include **`dnsRecords`**, certificate status, and **`routingCnameTarget`** for the managed certificate once its requirements are provisioned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string

try {
    $result = $apiInstance->verifyOrgCustomDomainDns($org_id, $project_id, $hostname);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->verifyOrgCustomDomainDns: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\OrgVerifyCustomDomainDnsSuccessResponse**](../Model/OrgVerifyCustomDomainDnsSuccessResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
