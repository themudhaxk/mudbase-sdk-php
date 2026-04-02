# OpenAPI\Client\ComplianceApi

Compliance automation and security event logging (GDPR, SOC 2)

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**complianceLogSecurityEvent()**](ComplianceApi.md#complianceLogSecurityEvent) | **POST** /api/compliance/security-event | Log security event |


## `complianceLogSecurityEvent()`

```php
complianceLogSecurityEvent($compliance_log_security_event_request): \OpenAPI\Client\Model\ComplianceLogSecurityEvent200Response
```

Log security event

Log a security event for compliance and audit (e.g. SOC 2, GDPR). Event type and severity are required; optional details (userId, resource, ipAddress, etc.) for forensics.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ComplianceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$compliance_log_security_event_request = {"eventType":"unauthorized_access_attempt","severity":"high","details":{"userId":"685acbe0e129932fbb7a0fc2","resource":"admin-panel","ipAddress":"192.168.1.100","action":"blocked","reason":"Insufficient permissions"}}; // \OpenAPI\Client\Model\ComplianceLogSecurityEventRequest | Event type (e.g. unauthorized_access_attempt, brute_force_attempt), severity (low–critical), and optional details object for context.

try {
    $result = $apiInstance->complianceLogSecurityEvent($compliance_log_security_event_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComplianceApi->complianceLogSecurityEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **compliance_log_security_event_request** | [**\OpenAPI\Client\Model\ComplianceLogSecurityEventRequest**](../Model/ComplianceLogSecurityEventRequest.md)| Event type (e.g. unauthorized_access_attempt, brute_force_attempt), severity (low–critical), and optional details object for context. | |

### Return type

[**\OpenAPI\Client\Model\ComplianceLogSecurityEvent200Response**](../Model/ComplianceLogSecurityEvent200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
