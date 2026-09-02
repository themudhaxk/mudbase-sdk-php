# # PushSentResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**success** | **bool** | True when at least one recipient across any channel was delivered to. | [optional]
**message_id** | **string** |  | [optional]
**success_count** | **int** |  | [optional]
**failure_count** | **int** |  | [optional]
**channels** | [**\OpenAPI\Client\Model\PushSentResponseDataChannels**](PushSentResponseDataChannels.md) |  | [optional]
**rejected_tokens** | **string[]** | Device tokens that were passed but are not registered to the project, and so were dropped. Omitted when empty. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
