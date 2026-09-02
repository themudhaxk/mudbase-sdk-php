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
**edge** | [**\OpenAPI\Client\Model\OrgEdgeHints**](OrgEdgeHints.md) |  | [optional]
**dns_records** | [**\OpenAPI\Client\Model\OrgDnsRecord[]**](OrgDnsRecord.md) | Same shape as &#x60;OrgDomainEntryWithDns.dnsRecords&#x60; when Fly ACME ran after this successful verify; omit or empty when Fly ACME is disabled or not provisioned. | [optional]
**fly_certificate_status** | **string** | Fly certificate status after verify when Fly ACME is active; null otherwise | [optional]
**fly_acme_enabled** | **bool** | True when Fly ACME would call the Certificates API (token, app, CUSTOM_DOMAIN_FLY_ACME_ENABLED). | [optional]
**fly_acme_disabled_reason** | **string** | When &#x60;flyAcmeEnabled&#x60; is false, why Fly ACME did not run (ops misconfiguration hint). | [optional]
**fly_provision_error** | **string** | When Fly ACME is enabled but POST acme failed, Fly API error message for support; null on success. | [optional]
**fly_legacy_staff_pipeline** | **bool** | When true, &#x60;CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE&#x60; is on — status may stay &#x60;cname_pending_staff&#x60; and staff approve-cname is required even if Fly provision succeeds. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
