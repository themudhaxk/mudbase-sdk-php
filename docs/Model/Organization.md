# # Organization

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**name** | **string** |  | [optional]
**slug** | **string** |  | [optional]
**description** | **string** |  | [optional]
**logo** | **string** | Optional logo URL. Org-related emails use the platform logo (env); this field is for legacy or future UI use only. | [optional]
**website** | **string** |  | [optional]
**plan** | [**\OpenAPI\Client\Model\Plan**](Plan.md) |  | [optional]
**usage** | [**\OpenAPI\Client\Model\Usage**](Usage.md) |  | [optional]
**limits** | [**\OpenAPI\Client\Model\Limits**](Limits.md) |  | [optional]
**billing** | [**\OpenAPI\Client\Model\Billing**](Billing.md) |  | [optional]
**settings** | **object** | May include customDomainAddon (optional billing/legacy flag; not required for custom domains on Growth/Scale). | [optional]
**deployment_type** | **string** |  | [optional]
**dedicated** | **object** | Dedicated API/DB routing; may include edgeTlsStatus, infraMeteringLastReportAt. | [optional]
**preferred_region** | **string** |  | [optional]
**infrastructure_environments** | **object[]** |  | [optional]
**allowed_domains** | **object[]** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
