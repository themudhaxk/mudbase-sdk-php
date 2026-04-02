# OpenAPI\Client\OrganizationsApi

Organization custom domains (DNS TXT at _mudbase-verify.&lt;hostname&gt;), verify-dns (typically queues cname_pending_staff and emails ops on first success), then staff CNAME approval, platform DNS, verify-platform-dns, activate. POST platform-ready is a legacy extra ops ping. Requires owner/admin JWT.

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**organizationsAddDomain()**](OrganizationsApi.md#organizationsAddDomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add custom domain |
| [**organizationsListDomains()**](OrganizationsApi.md#organizationsListDomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS TXT hints |
| [**organizationsPatchDomain()**](OrganizationsApi.md#organizationsPatchDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Patch domain status or regenerate token |
| [**organizationsRemoveDomain()**](OrganizationsApi.md#organizationsRemoveDomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove custom domain |
| [**organizationsReportDomainPlatformReady()**](OrganizationsApi.md#organizationsReportDomainPlatformReady) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops hosting / edge ready |
| [**organizationsSetPrimaryDomain()**](OrganizationsApi.md#organizationsSetPrimaryDomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**organizationsVerifyDomainDns()**](OrganizationsApi.md#organizationsVerifyDomainDns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain via DNS TXT |


## `organizationsAddDomain()`

```php
organizationsAddDomain($org_id, $project_id, $organizations_add_domain_request)
```

Add custom domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$organizations_add_domain_request = new \OpenAPI\Client\Model\OrganizationsAddDomainRequest(); // \OpenAPI\Client\Model\OrganizationsAddDomainRequest

try {
    $apiInstance->organizationsAddDomain($org_id, $project_id, $organizations_add_domain_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsAddDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **organizations_add_domain_request** | [**\OpenAPI\Client\Model\OrganizationsAddDomainRequest**](../Model/OrganizationsAddDomainRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsListDomains()`

```php
organizationsListDomains($org_id, $project_id)
```

List custom domains and DNS TXT hints

Owner/admin. Domains are per project. Returns dnsTxtHost, dnsTxtValue, platformActivationPending (dns_verified waiting for ops), and customDomainLiveForApiTraffic (active or legacy verified).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
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
    $apiInstance->organizationsListDomains($org_id, $project_id);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsListDomains: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsPatchDomain()`

```php
organizationsPatchDomain($org_id, $project_id, $hostname, $organizations_patch_domain_request)
```

Patch domain status or regenerate token

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
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
$organizations_patch_domain_request = new \OpenAPI\Client\Model\OrganizationsPatchDomainRequest(); // \OpenAPI\Client\Model\OrganizationsPatchDomainRequest

try {
    $apiInstance->organizationsPatchDomain($org_id, $project_id, $hostname, $organizations_patch_domain_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsPatchDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |
| **organizations_patch_domain_request** | [**\OpenAPI\Client\Model\OrganizationsPatchDomainRequest**](../Model/OrganizationsPatchDomainRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsRemoveDomain()`

```php
organizationsRemoveDomain($org_id, $project_id, $hostname)
```

Remove custom domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
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
    $apiInstance->organizationsRemoveDomain($org_id, $project_id, $hostname);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsRemoveDomain: ', $e->getMessage(), PHP_EOL;
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

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsReportDomainPlatformReady()`

```php
organizationsReportDomainPlatformReady($org_id, $project_id, $hostname, $organizations_report_domain_platform_ready_request)
```

Notify platform ops hosting / edge ready

Legacy optional ops email. First Mudbase TXT success already emails ops. Allowed during platform setup after Mudbase TXT. Recipients default to admin@mudhaxkservices.com and admin@mudbase.dev when CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS is unset. Returns 503 email_provider_not_configured if no email provider is configured. Does not change domain status.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
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
$organizations_report_domain_platform_ready_request = new \OpenAPI\Client\Model\OrganizationsReportDomainPlatformReadyRequest(); // \OpenAPI\Client\Model\OrganizationsReportDomainPlatformReadyRequest

try {
    $apiInstance->organizationsReportDomainPlatformReady($org_id, $project_id, $hostname, $organizations_report_domain_platform_ready_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsReportDomainPlatformReady: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **hostname** | **string**|  | |
| **organizations_report_domain_platform_ready_request** | [**\OpenAPI\Client\Model\OrganizationsReportDomainPlatformReadyRequest**](../Model/OrganizationsReportDomainPlatformReadyRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsSetPrimaryDomain()`

```php
organizationsSetPrimaryDomain($org_id, $project_id, $organizations_set_primary_domain_request)
```

Set primary custom domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\OrganizationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$project_id = 'project_id_example'; // string
$organizations_set_primary_domain_request = new \OpenAPI\Client\Model\OrganizationsSetPrimaryDomainRequest(); // \OpenAPI\Client\Model\OrganizationsSetPrimaryDomainRequest

try {
    $apiInstance->organizationsSetPrimaryDomain($org_id, $project_id, $organizations_set_primary_domain_request);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsSetPrimaryDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **project_id** | **string**|  | |
| **organizations_set_primary_domain_request** | [**\OpenAPI\Client\Model\OrganizationsSetPrimaryDomainRequest**](../Model/OrganizationsSetPrimaryDomainRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `organizationsVerifyDomainDns()`

```php
organizationsVerifyDomainDns($org_id, $project_id, $hostname)
```

Verify domain via DNS TXT

On first success from pending/failed, status becomes cname_pending_staff; ops email once; audit org.domain.txt_verified and org.domain.cname_staff_queued.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
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
    $apiInstance->organizationsVerifyDomainDns($org_id, $project_id, $hostname);
} catch (Exception $e) {
    echo 'Exception when calling OrganizationsApi->organizationsVerifyDomainDns: ', $e->getMessage(), PHP_EOL;
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

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
