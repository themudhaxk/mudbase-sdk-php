# # OrgDomainEntryWithDns

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** | Subdocument id when present (MongoDB) | [optional]
**hostname** | **string** |  | [optional]
**hostname_normalized** | **string** |  | [optional]
**status** | **string** |  | [optional]
**is_primary** | **bool** |  | [optional]
**source** | **string** |  | [optional]
**verification_token** | **string** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**verified_at** | **\DateTime** |  | [optional]
**last_verified_at** | **\DateTime** |  | [optional]
**dns_txt_host** | **string** | FQDN for the TXT record (e.g. _mudbase-verify.example.com) | [optional]
**dns_txt_value** | **string** | Exact TXT string value (mudbase-domain-verification&#x3D;&lt;token&gt;) | [optional]
**edge** | [**\OpenAPI\Client\Model\OrgEdgeHints**](OrgEdgeHints.md) |  | [optional]
**platform_activation_pending** | **bool** | True while Mudbase TXT passed but custom host not yet active (includes CNAME and platform DNS pipeline). | [optional]
**custom_domain_live_for_api_traffic** | **bool** |  | [optional]
**custom_domain_verification_step** | **int** | Console wizard step 1–3; null when active/verified. | [optional]
**routing_cname_target** | **string** | Routing CNAME target: Fly Certificates API &#x60;dns_requirements.cname&#x60; when Fly ACME has provisioned and stored requirements; otherwise fallback from env &#x60;CUSTOM_DOMAIN_API_CNAME_TARGET&#x60;. | [optional]
**dns_records** | [**\OpenAPI\Client\Model\OrgDnsRecord[]**](OrgDnsRecord.md) | Unified checklist: Mudbase ownership TXT, routing CNAME from Fly &#x60;dns_requirements.cname&#x60; (purpose &#x60;routing&#x60;) when provisioned else env fallback, and Fly rows (&#x60;fly_ownership&#x60;, &#x60;acme_challenge&#x60;, …) when Fly ACME is enabled and the certificate has been provisioned after Mudbase TXT. Empty or absent when Fly ACME is off or not yet provisioned. Prefer this over &#x60;platformDnsVerification&#x60; alone for org-facing DNS UI. | [optional]
**fly_certificate_status** | **string** | Fly Certificates API &#x60;status&#x60; when **&#x60;CUSTOM_DOMAIN_FLY_ACME_ENABLED&#x60;** and token/app are configured (e.g. &#x60;pending_validation&#x60;, &#x60;active&#x60;). Null when Fly ACME is not in use for this deployment. | [optional]
**platform_dns_verification** | [**\OpenAPI\Client\Model\OrgPlatformDnsVerificationCustomer**](OrgPlatformDnsVerificationCustomer.md) |  | [optional]
**cname_submitted_at** | **\DateTime** |  | [optional]
**cname_approved_at** | **\DateTime** |  | [optional]
**platform_dns_verification_submitted_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
