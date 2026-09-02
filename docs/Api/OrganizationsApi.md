# OpenAPI\Client\OrganizationsApi

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
| [**orgCustomDomainVerifyPlatformDns()**](OrganizationsApi.md#orgCustomDomainVerifyPlatformDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-platform-dns | Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness) |
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
addOrgCustomDomain($org_id, $project_id, $add_org_domain_request): \OpenAPI\Client\Model\OrgAddDomainResponse
```

Add a custom domain

Creates a pending domain row; the response **`domain`** uses the compact **`OrgDomainEntryOrgConsole`** shape (**`dnsRecords`** includes the Mudbase ownership TXT). **`dnsRecords`** may include Mudbase TXT and routing CNAME only until Mudbase TXT succeeds and Fly ACME (if enabled) provisions a certificate. **`flyCertificateStatus`** is typically omitted until Fly ACME runs after first successful **`verify-dns`**.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$add_org_domain_request = {"hostname":"hostname_example"}; // \OpenAPI\Client\Model\AddOrgDomainRequest

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
| **add_org_domain_request** | [**\OpenAPI\Client\Model\AddOrgDomainRequest**](../Model/AddOrgDomainRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\OrgAddDomainResponse**](../Model/OrgAddDomainResponse.md)

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_organization_request = {"name":"Mudbase Inc","description":"Main organization","logo":"https://example.com/logo.png","website":"https://mudbase.dev","parentOrgId":"685acbe0e129932fbb7a0fc3"}; // \OpenAPI\Client\Model\CreateOrganizationRequest

try {
    $apiInstance->createOrganization($create_organization_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->createOrganization: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_organization_request** | [**\OpenAPI\Client\Model\CreateOrganizationRequest**](../Model/CreateOrganizationRequest.md)|  | |

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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
deleteOrganization($org_id): \OpenAPI\Client\Model\DeleteOrganization200Response
```

Delete organization

Delete an organization permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\DeleteOrganization200Response**](../Model/DeleteOrganization200Response.md)

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
deleteSubOrganization($org_id, $suborg_id): \OpenAPI\Client\Model\DeleteSubOrganization200Response
```

~~Delete sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\DeleteSubOrganization200Response**](../Model/DeleteSubOrganization200Response.md)

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
getOrgCustomDomainDnsInstructions($org_id, $project_id, $hostname): \OpenAPI\Client\Model\OrgDnsInstructionsResponse
```

Get DNS TXT record instructions for one hostname

Returns the same shape as list/add for one hostname (URL-encode `hostname` in the path), including **`dnsRecords`** and **`flyCertificateStatus`** when applicable. See **`listOrgCustomDomains`** for how Fly ACME and Cloudflare SaaS affect those fields.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgDnsInstructionsResponse**](../Model/OrgDnsInstructionsResponse.md)

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
getOrganization($org_id): \OpenAPI\Client\Model\Organization
```

Get organization details by ID

Get organization details by ID. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\Organization**](../Model/Organization.md)

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
getOrganizationMembers($org_id): \OpenAPI\Client\Model\GetOrganizationMembers200Response
```

Get organization members

Get all members of an organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetOrganizationMembers200Response**](../Model/GetOrganizationMembers200Response.md)

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
getOrganizationUsage($org_id): \OpenAPI\Client\Model\GetOrganizationUsage200Response
```

Get organization usage and billing

Get usage statistics and billing information for an organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetOrganizationUsage200Response**](../Model/GetOrganizationUsage200Response.md)

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
getOrganizationUsers($org_id, $status): \OpenAPI\Client\Model\GetOrganizationUsers200Response
```

List organization users with metadata

Get all users in the organization with metadata (email, full name, role, accountStatus, phone, lastLogin, etc.). Optional query `status` filters by accountStatus (pending, active, suspended). Requires organization access and owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetOrganizationUsers200Response**](../Model/GetOrganizationUsers200Response.md)

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
getProjectUsers($org_id, $project_id, $status): \OpenAPI\Client\Model\GetProjectUsers200Response
```

List project users with metadata

Get all users in a project with metadata (email, full name, role, accountStatus, etc.). Optional query `status` filters by accountStatus. Project must belong to the organization. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetProjectUsers200Response**](../Model/GetProjectUsers200Response.md)

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
getSubOrganizations($org_id): \OpenAPI\Client\Model\GetSubOrganizations200Response
```

~~Get sub-organizations~~ (deprecated)

Get all sub-organizations under a parent organization. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetSubOrganizations200Response**](../Model/GetSubOrganizations200Response.md)

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
getUserOverview($org_id, $user_id): \OpenAPI\Client\Model\GetUserOverview200Response
```

Get user overview and data footprint

Get a user's profile plus footprint (files count/size, sessions, API keys, collections in project). Use for dashboard to see everything tied to the user. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\GetUserOverview200Response**](../Model/GetUserOverview200Response.md)

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$internal_custom_domain_addon_request = {"orgId":"orgId_example","enabled":true}; // \OpenAPI\Client\Model\InternalCustomDomainAddonRequest

try {
    $apiInstance->internalCustomDomainAddon($internal_custom_domain_addon_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalCustomDomainAddon: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **internal_custom_domain_addon_request** | [**\OpenAPI\Client\Model\InternalCustomDomainAddonRequest**](../Model/InternalCustomDomainAddonRequest.md)|  | |

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

Returns the last automated custom-domain sweep (TXT recheck + Fly ACME retry), job env flags, and Fly deploy troubleshooting hints when the proxy reports the app is not listening on 0.0.0.0:PORT. Requires header `X-Internal-Api-Key` (same as other /internal routes).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: InternalApiKey
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$internal_domain_dns_recheck_batch_request = {"maxOrgs":1,"recheckOlderThanHours":1}; // \OpenAPI\Client\Model\InternalDomainDnsRecheckBatchRequest

try {
    $apiInstance->internalDomainDnsRecheckBatch($internal_domain_dns_recheck_batch_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalDomainDnsRecheckBatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **internal_domain_dns_recheck_batch_request** | [**\OpenAPI\Client\Model\InternalDomainDnsRecheckBatchRequest**](../Model/InternalDomainDnsRecheckBatchRequest.md)|  | [optional] |

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-Internal-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Internal-Api-Key', 'Bearer');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$provision_enterprise_request = {"orgId":"orgId_example","provisionRequestId":"provisionRequestId_example","apiBaseUrl":"apiBaseUrl_example","dbRef":"dbRef_example","serverId":"serverId_example"}; // \OpenAPI\Client\Model\ProvisionEnterpriseRequest

try {
    $apiInstance->internalProvisionEnterprise($provision_enterprise_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->internalProvisionEnterprise: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **provision_enterprise_request** | [**\OpenAPI\Client\Model\ProvisionEnterpriseRequest**](../Model/ProvisionEnterpriseRequest.md)|  | |

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
inviteSubOrganizationMember($org_id, $suborg_id, $invite_member_request): \OpenAPI\Client\Model\InviteSubOrganizationMember200Response
```

~~Invite member to sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$invite_member_request = {"email":"user@suborg.example.com","role":"viewer"}; // \OpenAPI\Client\Model\InviteMemberRequest

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
| **invite_member_request** | [**\OpenAPI\Client\Model\InviteMemberRequest**](../Model/InviteMemberRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\InviteSubOrganizationMember200Response**](../Model/InviteSubOrganizationMember200Response.md)

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
inviteTeamMember($org_id, $invite_member_request): \OpenAPI\Client\Model\InviteTeamMember200Response
```

Invite team member to organization

Send an invitation to a user to join the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$invite_member_request = {"email":"newuser@example.com","role":"member"}; // \OpenAPI\Client\Model\InviteMemberRequest

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
| **invite_member_request** | [**\OpenAPI\Client\Model\InviteMemberRequest**](../Model/InviteMemberRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\InviteTeamMember200Response**](../Model/InviteTeamMember200Response.md)

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
listOrgCustomDomains($org_id, $project_id): \OpenAPI\Client\Model\OrgDomainsListResponse
```

List custom domains and DNS verification hints

Returns allowed hostnames for **this project**, primary hostname (per project), API base URL, and per-domain DNS guidance.  Each row uses **`dnsRecords`** for the Mudbase ownership TXT (purpose **`mudbase_ownership`**) and routing **CNAME** from Fly **`dns_requirements.cname`** when Fly ACME has provisioned (else fallback **`CUSTOM_DOMAIN_API_CNAME_TARGET`**), and—when Fly ACME is enabled (**`FLY_API_TOKEN`** + **`CUSTOM_DOMAIN_FLY_ACME_ENABLED`**)—Fly rows (`fly_ownership`, `acme_challenge`, etc.) after the org has passed Mudbase TXT at least once. **`flyCertificateStatus`** mirrors Fly’s certificate state when ACME automation is on (e.g. `pending_validation`, `active`).  **`edge`** appears only when edge SSL (SSL-for-SaaS) is configured. Fly ACME and edge SSL are mutually exclusive on the server.  Requires Growth, Scale, or Enterprise plan (custom domains included in plan features).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgDomainsListResponse**](../Model/OrgDomainsListResponse.md)

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
listOrganizations(): \OpenAPI\Client\Model\ListOrganizations200Response
```

Get all organizations for user

Get all organizations the authenticated user belongs to. Requires: OrgBearerAuth (organization-level authentication only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\ListOrganizations200Response**](../Model/ListOrganizations200Response.md)

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string
$org_custom_domain_platform_ready_request = {"note":"note_example"}; // \OpenAPI\Client\Model\OrgCustomDomainPlatformReadyRequest

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
| **org_custom_domain_platform_ready_request** | [**\OpenAPI\Client\Model\OrgCustomDomainPlatformReadyRequest**](../Model/OrgCustomDomainPlatformReadyRequest.md)|  | [optional] |

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
orgCustomDomainSubmitCname($org_id, $project_id, $hostname): \OpenAPI\Client\Model\OrgPatchDomainResponse
```

Custom domain step 2 (optional): org confirms routing CNAME was added

Usually unnecessary. With Fly ACME default automation, Mudbase TXT verify may already set `cname_approved`. Legacy pipelines may queue `cname_pending_staff` until staff **`approve-cname`**. Use **`routingCnameTarget`** from **`GET .../projects/{projectId}/domains`** (Fly **`dns_requirements.cname`** when provisioned, else **`CUSTOM_DOMAIN_API_CNAME_TARGET`**).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

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
orgCustomDomainSubmitPlatformDnsVerificationDeprecated($org_id, $project_id, $hostname): \OpenAPI\Client\Model\OrgPatchDomainResponse
```

Deprecated — use POST .../verify-platform-dns

Deprecated alias of **`orgCustomDomainVerifyPlatformDns`** (same behavior — manual TXT and/or Fly ACME path per server config).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

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
orgCustomDomainVerifyPlatformDns($org_id, $project_id, $hostname): \OpenAPI\Client\Model\OrgPatchDomainResponse
```

Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness)

**Manual path (no Fly ACME):** After staff **`PATCH .../platform-dns-verification`**, the org adds the published TXT and calls this endpoint. The API resolves public TXT at **`platformDnsVerification.recordName`** and matches **`recordValue`**. On success, `status` → **`platform_dns_pending_review`** until staff **`POST .../activate`**.  **Fly ACME path (default):** When Fly ACME is enabled and **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE`** is **not** set, the org calls this after Mudbase TXT and Fly DNS rows are in place (status typically **`cname_approved`** from automated verify-dns). The API triggers Fly **`POST .../check`** and **`GET`** certificate with bounded retries. On success, `status` → **`active`** and the org may receive the activation email—**no** staff **`approve-cname`** or **`activate`** required.  **Fly legacy:** If **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE=true`**, behavior matches the older flow: staff **`approve-cname`** may be required first; after a ready Fly cert, **`status`** becomes **`active`** only when **`CUSTOM_DOMAIN_FLY_AUTO_ACTIVATE=true`**, else **`platform_dns_pending_review`** until staff **`activate`**.  **`platform_dns_verification_failed`** may include **`details.flyStatus`** / **`details.flyError`** on the Fly path.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

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
patchOrgCustomDomain($org_id, $project_id, $hostname, $patch_org_domain_request): \OpenAPI\Client\Model\OrgPatchDomainResponse
```

Update domain status or regenerate verification token

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$hostname = 'hostname_example'; // string
$patch_org_domain_request = {"status":"pending","regenerateToken":true}; // \OpenAPI\Client\Model\PatchOrgDomainRequest

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
| **patch_org_domain_request** | [**\OpenAPI\Client\Model\PatchOrgDomainRequest**](../Model/PatchOrgDomainRequest.md)|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\OrgPatchDomainResponse**](../Model/OrgPatchDomainResponse.md)

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
removeSubOrganizationMember($org_id, $suborg_id, $user_id): \OpenAPI\Client\Model\RemoveTeamMember200Response
```

~~Remove member from sub-organization~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\RemoveTeamMember200Response**](../Model/RemoveTeamMember200Response.md)

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
removeTeamMember($org_id, $user_id): \OpenAPI\Client\Model\RemoveTeamMember200Response
```

Remove team member from organization

Remove a user from the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\RemoveTeamMember200Response**](../Model/RemoveTeamMember200Response.md)

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
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$set_org_primary_domain_request = {"hostname":"hostname_example"}; // \OpenAPI\Client\Model\SetOrgPrimaryDomainRequest

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
| **set_org_primary_domain_request** | [**\OpenAPI\Client\Model\SetOrgPrimaryDomainRequest**](../Model/SetOrgPrimaryDomainRequest.md)|  | |

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
updateMemberRole($org_id, $user_id, $update_member_role_request): \OpenAPI\Client\Model\UpdateMemberRole200Response
```

Update member role

Update a member's role in the organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string
$update_member_role_request = {"role":"admin"}; // \OpenAPI\Client\Model\UpdateMemberRoleRequest

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
| **update_member_role_request** | [**\OpenAPI\Client\Model\UpdateMemberRoleRequest**](../Model/UpdateMemberRoleRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateMemberRole200Response**](../Model/UpdateMemberRole200Response.md)

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
updateOrganization($org_id, $update_organization_request): \OpenAPI\Client\Model\UpdateOrganization200Response
```

Update organization

Update organization details. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$update_organization_request = {"name":"Mudbase Inc Updated","description":"Updated organization description","logo":"https://example.com/new-logo.png","website":"https://mudbase.dev"}; // \OpenAPI\Client\Model\UpdateOrganizationRequest

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
| **update_organization_request** | [**\OpenAPI\Client\Model\UpdateOrganizationRequest**](../Model/UpdateOrganizationRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateOrganization200Response**](../Model/UpdateOrganization200Response.md)

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
updateOrganizationPlan($org_id, $update_organization_plan_request): \OpenAPI\Client\Model\UpdateOrganizationPlan200Response
```

Update organization plan

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$update_organization_plan_request = {"plan":"pro"}; // \OpenAPI\Client\Model\UpdateOrganizationPlanRequest

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
| **update_organization_plan_request** | [**\OpenAPI\Client\Model\UpdateOrganizationPlanRequest**](../Model/UpdateOrganizationPlanRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateOrganizationPlan200Response**](../Model/UpdateOrganizationPlan200Response.md)

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
updateSubOrganization($org_id, $suborg_id, $update_organization_request): \OpenAPI\Client\Model\UpdateSubOrganization200Response
```

~~Update sub-organization~~ (deprecated)

Update a sub-organization's configuration. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$update_organization_request = {"name":"Sub-Organization Updated","description":"Updated sub-organization description","logo":"https://example.com/sub-logo.png","website":"https://sub.mudbase.dev"}; // \OpenAPI\Client\Model\UpdateOrganizationRequest

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
| **update_organization_request** | [**\OpenAPI\Client\Model\UpdateOrganizationRequest**](../Model/UpdateOrganizationRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateSubOrganization200Response**](../Model/UpdateSubOrganization200Response.md)

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
updateSubOrganizationMemberRole($org_id, $suborg_id, $user_id, $update_member_role_request): \OpenAPI\Client\Model\UpdateMemberRole200Response
```

~~Update sub-organization member role~~ (deprecated)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 685acbe0e129932fbb7a0fc3; // string
$suborg_id = 685acbe0e129932fbb7a0fc4; // string
$user_id = 685acbe0e129932fbb7a0fc2; // string
$update_member_role_request = {"role":"admin"}; // \OpenAPI\Client\Model\UpdateMemberRoleRequest

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
| **update_member_role_request** | [**\OpenAPI\Client\Model\UpdateMemberRoleRequest**](../Model/UpdateMemberRoleRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateMemberRole200Response**](../Model/UpdateMemberRole200Response.md)

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
updateUserAccountStatus($org_id, $user_id, $update_user_account_status_request): \OpenAPI\Client\Model\UpdateUserAccountStatus200Response
```

Update user account status (activate or suspend)

Set a user's account status to active or suspended. Used to approve pending users or suspend/activate accounts. Cannot change status of an organization owner. Requires owner or admin role.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$user_id = 'user_id_example'; // string
$update_user_account_status_request = {"accountStatus":"active"}; // \OpenAPI\Client\Model\UpdateUserAccountStatusRequest

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
| **update_user_account_status_request** | [**\OpenAPI\Client\Model\UpdateUserAccountStatusRequest**](../Model/UpdateUserAccountStatusRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\UpdateUserAccountStatus200Response**](../Model/UpdateUserAccountStatus200Response.md)

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
verifyOrgCustomDomainDns($org_id, $project_id, $hostname): \OpenAPI\Client\Model\OrgVerifyCustomDomainDnsSuccessResponse
```

Verify domain ownership via DNS TXT

Looks up TXT at `_mudbase-verify.<hostname>` for value `mudbase-domain-verification=<token>`.  When the server has **`CLOUDFLARE_API_TOKEN`** and **`CLOUDFLARE_ZONE_ID`** configured (and Fly ACME is **not** enabled), a successful verify also creates or refreshes a Cloudflare Custom Hostname (SSL for SaaS) and returns **`cloudflare`** with DCV hints.  When **Fly ACME** is enabled (**`FLY_API_TOKEN`** + **`CUSTOM_DOMAIN_FLY_ACME_ENABLED=true`** + app slug), a successful verify calls Fly’s Certificates API (`POST .../certificates/acme`) and persists DNS requirements. If Fly returns DNS rows and **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE`** is **not** set, status advances to **`cname_approved`** in the same response (no staff **`approve-cname`**); **`org.domain.cname_staff_queued`** is not logged for that path. Otherwise (legacy Fly or non-Fly), first success from `pending`/`failed` may move to **`cname_pending_staff`** and queue staff as before.  The **200** response may include **`dnsRecords`**, **`flyCertificateStatus`**, and **`routingCnameTarget`** from Fly’s **`dns_requirements.cname`** when provisioned.  Cloudflare SaaS and Fly ACME cannot both be enabled; the API process refuses to start if both are configured.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
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

[**\OpenAPI\Client\Model\OrgVerifyCustomDomainDnsSuccessResponse**](../Model/OrgVerifyCustomDomainDnsSuccessResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
