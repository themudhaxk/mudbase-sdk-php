# # ApiKycWebhookConfigPutRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**webhook_url** | **string** | Destination URL. Send null or empty string to clear. | [optional]
**webhook_secret** | **string** | Explicit signing secret (min 16 chars). Send null or empty string to clear. | [optional]
**generate_secret** | **bool** | When true, the server generates a new secret and returns it once. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
