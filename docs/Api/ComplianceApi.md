# OpenAPI\Client\ComplianceApi

Compliance automation and security event logging (GDPR, SOC 2)

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**apiGdprErasePost()**](ComplianceApi.md#apiGdprErasePost) | **POST** /api/gdpr/erase | Erase my personal data (GDPR Art. 17) |
| [**apiGdprExportGet()**](ComplianceApi.md#apiGdprExportGet) | **GET** /api/gdpr/export | Export my personal data (GDPR Art. 15) |
| [**generateAccessReview()**](ComplianceApi.md#generateAccessReview) | **POST** /api/compliance/access-review | Generate access review report (SOC 2) |
| [**generateDataProcessingRecord()**](ComplianceApi.md#generateDataProcessingRecord) | **POST** /api/compliance/data-processing-record | Generate data processing record (GDPR Article 30) |
| [**getComplianceSummary()**](ComplianceApi.md#getComplianceSummary) | **GET** /api/compliance/summary | Get compliance summary |
| [**logSecurityEvent()**](ComplianceApi.md#logSecurityEvent) | **POST** /api/compliance/security-event | Log security event |


## `apiGdprErasePost()`

```php
apiGdprErasePost($api_gdpr_erase_post_request): \OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response
```

Erase my personal data (GDPR Art. 17)

Anonymizes the subject's PII, revokes sessions/tokens, and anonymizes (never hard-deletes) financial/legal-retention records. Idempotent and self-scoped.  Requires re-proving your current password (skipped only for OAuth-only accounts with no password set) and, if 2FA is enabled, a fresh TOTP code - the same step-up re-authentication already required by the less-destructive `PATCH /api/users/password` and `POST /api/users/2fa/disable`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$api_gdpr_erase_post_request = new \OpenAPI\Client\Model\ApiGdprErasePostRequest(); // \OpenAPI\Client\Model\ApiGdprErasePostRequest

try {
    $result = $apiInstance->apiGdprErasePost($api_gdpr_erase_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->apiGdprErasePost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **api_gdpr_erase_post_request** | [**\OpenAPI\Client\Model\ApiGdprErasePostRequest**](../Model/ApiGdprErasePostRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\ApplyRoleFeaturePreset200Response**](../Model/ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `apiGdprExportGet()`

```php
apiGdprExportGet(): object
```

Export my personal data (GDPR Art. 15)

Returns the authenticated subject's personal data as a downloadable JSON attachment. Self-scoped — a caller can only export their own data.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->apiGdprExportGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->apiGdprExportGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

**object**

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generateAccessReview()`

```php
generateAccessReview($generate_access_review_request): \OpenAPI\Client\Model\GenerateAccessReview200Response
```

Generate access review report (SOC 2)

Generate access review report for compliance audits (SOC 2, ISO 27001, etc.). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$generate_access_review_request = {"orgId":"685acbe0e129932fbb7a0fc3","reviewPeriod":{"start":"2024-10-01T00:00:00.000Z","end":"2024-12-31T23:59:59.000Z"}}; // \OpenAPI\Client\Model\GenerateAccessReviewRequest

try {
    $result = $apiInstance->generateAccessReview($generate_access_review_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->generateAccessReview: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **generate_access_review_request** | [**\OpenAPI\Client\Model\GenerateAccessReviewRequest**](../Model/GenerateAccessReviewRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GenerateAccessReview200Response**](../Model/GenerateAccessReview200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generateDataProcessingRecord()`

```php
generateDataProcessingRecord($generate_data_processing_record_request): \OpenAPI\Client\Model\GenerateDataProcessingRecord200Response
```

Generate data processing record (GDPR Article 30)

Generate GDPR Article 30 compliant data processing record

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$generate_data_processing_record_request = {"orgId":"685acbe0e129932fbb7a0fc3","recordDate":"2024-12-16T00:00:00.000Z"}; // \OpenAPI\Client\Model\GenerateDataProcessingRecordRequest

try {
    $result = $apiInstance->generateDataProcessingRecord($generate_data_processing_record_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->generateDataProcessingRecord: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **generate_data_processing_record_request** | [**\OpenAPI\Client\Model\GenerateDataProcessingRecordRequest**](../Model/GenerateDataProcessingRecordRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GenerateDataProcessingRecord200Response**](../Model/GenerateDataProcessingRecord200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getComplianceSummary()`

```php
getComplianceSummary(): \OpenAPI\Client\Model\GetComplianceSummary200Response
```

Get compliance summary

Get compliance dashboard data (GDPR, SOC 2, security status). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getComplianceSummary();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->getComplianceSummary: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\OpenAPI\Client\Model\GetComplianceSummary200Response**](../Model/GetComplianceSummary200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `logSecurityEvent()`

```php
logSecurityEvent($log_security_event_request): \OpenAPI\Client\Model\LogSecurityEvent200Response
```

Log security event

Log a security event for compliance and audit purposes

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$log_security_event_request = {"eventType":"unauthorized_access_attempt","severity":"high","details":{"userId":"685acbe0e129932fbb7a0fc2","resource":"admin-panel","ipAddress":"192.168.1.100","action":"blocked","reason":"Insufficient permissions"}}; // \OpenAPI\Client\Model\LogSecurityEventRequest

try {
    $result = $apiInstance->logSecurityEvent($log_security_event_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->logSecurityEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **log_security_event_request** | [**\OpenAPI\Client\Model\LogSecurityEventRequest**](../Model/LogSecurityEventRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\LogSecurityEvent200Response**](../Model/LogSecurityEvent200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
