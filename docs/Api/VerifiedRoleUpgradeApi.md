# OpenAPI\Client\VerifiedRoleUpgradeApi



All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**verifiedRoleUpgrade()**](VerifiedRoleUpgradeApi.md#verifiedRoleUpgrade) | **POST** /api/orgs/{orgId}/users/{userId}/upgrade | Verified role upgrade with payment verification |


## `verifiedRoleUpgrade()`

```php
verifiedRoleUpgrade($org_id, $user_id, $verified_role_upgrade_request): \OpenAPI\Client\Model\VerifiedRoleUpgrade200Response
```

Verified role upgrade with payment verification

Upgrade user role after verifying payment and KYC. Prevents replay attacks.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\VerifiedRoleUpgradeApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$org_id = 'org_id_example'; // string
$user_id = 'user_id_example'; // string
$verified_role_upgrade_request = {"targetRole":"seller","paymentIntentId":"pi_abc123","verificationId":"kyc_xyz789"}; // \OpenAPI\Client\Model\VerifiedRoleUpgradeRequest

try {
    $result = $apiInstance->verifiedRoleUpgrade($org_id, $user_id, $verified_role_upgrade_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VerifiedRoleUpgradeApi->verifiedRoleUpgrade: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **org_id** | **string**|  | |
| **user_id** | **string**|  | |
| **verified_role_upgrade_request** | [**\OpenAPI\Client\Model\VerifiedRoleUpgradeRequest**](../Model/VerifiedRoleUpgradeRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\VerifiedRoleUpgrade200Response**](../Model/VerifiedRoleUpgrade200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
