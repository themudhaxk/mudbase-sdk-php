# # CreateApiKeyRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  |
**project_id** | **string** | MongoDB ObjectId of the project |
**permissions** | [**\OpenAPI\Client\Model\ApiKeyPermission[]**](ApiKeyPermission.md) | Optional. Permission objects (resource + actions). Omit or pass [] for full access (all resources and actions). Include only the entries you want; remove resources or actions to restrict the key. | [optional]
**rate_limit** | [**\OpenAPI\Client\Model\RateLimit**](RateLimit.md) |  | [optional]
**expires_at** | **\DateTime** | Optional. When provided, must be a valid ISO 8601 date-time in the future. Omit for no expiration. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
