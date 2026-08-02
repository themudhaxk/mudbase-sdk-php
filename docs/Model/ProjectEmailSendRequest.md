# # ProjectEmailSendRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**template** | **string** | Registered template name resolved by the email worker | [optional]
**to** | [**\OpenAPI\Client\Model\EmailRequestTo**](EmailRequestTo.md) |  | [optional]
**data** | **array<string,mixed>** |  | [optional]
**subject** | **string** |  | [optional]
**html** | **string** |  | [optional]
**idempotency_key** | **string** |  | [optional]
**branding_scope** | **string** | Email layout branding; defaults from project context when omitted | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
