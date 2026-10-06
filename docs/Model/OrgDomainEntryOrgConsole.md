# # OrgDomainEntryOrgConsole

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**hostname** | **string** |  | [optional]
**status** | **string** |  | [optional]
**is_primary** | **bool** |  | [optional]
**source** | **string** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**verified_at** | **\DateTime** |  | [optional]
**last_verified_at** | **\DateTime** |  | [optional]
**cname_submitted_at** | **\DateTime** |  | [optional]
**cname_approved_at** | **\DateTime** |  | [optional]
**custom_domain_verification_step** | **int** |  | [optional]
**routing_cname_target** | **string** |  | [optional]
**dns_records** | [**\MudbaseSDK\Model\OrgDnsRecord[]**](OrgDnsRecord.md) |  | [optional]
**platform_activation_pending** | **bool** |  | [optional]
**custom_domain_live_for_api_traffic** | **bool** |  | [optional]
**edge** | [**\MudbaseSDK\Model\OrgEdgeHints**](OrgEdgeHints.md) |  | [optional]
**fly_certificate_status** | **string** |  | [optional]
**platform_dns_verification** | [**\MudbaseSDK\Model\OrgPlatformDnsVerificationCustomer**](OrgPlatformDnsVerificationCustomer.md) |  | [optional]
**platform_dns_verification_submitted_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
