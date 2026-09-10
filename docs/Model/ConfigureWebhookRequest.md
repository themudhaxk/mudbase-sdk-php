# # ConfigureWebhookRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**webhook_url** | **string** | URL to receive webhook payloads; set to null or omit to disable | [optional]
**webhook_secret** | **string** | Optional secret for signing payloads (e.g. X-Webhook-Signature) | [optional]
**webhook_events** | **string[]** | Event types to send (e.g. collection.insert, collection.update) | [optional]
**webhook_version** | **string** | Version string for payload format | [optional]
**transformations** | [**\MudbaseSDK\Model\GetWebhookConfig200ResponseDataTransformationsInner[]**](GetWebhookConfig200ResponseDataTransformationsInner.md) | Transformation rules to apply to payloads before delivery | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
