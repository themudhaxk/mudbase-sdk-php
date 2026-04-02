# # ChatSendMessageRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** |  |
**content** | **string** | Plaintext body; omit when sending e2ee (use e2ee.ciphertext for E2EE text). | [optional]
**e2ee** | [**\OpenAPI\Client\Model\ChatSendMessageRequestE2ee**](ChatSendMessageRequestE2ee.md) |  | [optional]
**reply_to** | **string** |  | [optional]
**mentions** | **string[]** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
