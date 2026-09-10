# # OrgVerifyCustomDomainDnsSuccessResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**success** | **bool** |  |
**hostname** | **string** |  |
**status** | **string** | Domain row status after check (typically cname_pending_staff after first TXT success from pending/failed; legacy dns_verified possible) |
**verification_token** | **string** |  |
**challenge_host** | **string** | Same as dnsTxtHost (_mudbase-verify.&lt;hostname&gt;) |
**expected_txt** | **string** | Same as dnsTxtValue |
**dns_txt_host** | **string** |  |
**dns_txt_value** | **string** |  |
**edge** | [**\MudbaseSDK\Model\OrgEdgeHints**](OrgEdgeHints.md) |  | [optional]
**dns_records** | [**\MudbaseSDK\Model\OrgDnsRecord[]**](OrgDnsRecord.md) | Same shape as &#x60;OrgDomainEntryWithDns.dnsRecords&#x60; when certificate provisioning ran after this successful verify; omit or empty when provisioning is disabled or not yet run. | [optional]
**fly_certificate_status** | **string** | Managed certificate status after verify when provisioning is active; null otherwise | [optional]
**fly_acme_enabled** | **bool** | True when automated managed-certificate provisioning is configured for this deployment. | [optional]
**fly_acme_disabled_reason** | **string** | When &#x60;flyAcmeEnabled&#x60; is false, why automated provisioning did not run (ops misconfiguration hint). | [optional]
**fly_provision_error** | **string** | When provisioning is enabled but certificate issuance failed, the provider error message for support; null on success. | [optional]
**fly_legacy_staff_pipeline** | **bool** | When true, the legacy staff pipeline is on: status may stay &#x60;cname_pending_staff&#x60; and staff approve-cname is required even if certificate provisioning succeeds. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
