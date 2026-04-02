# # UpdateProjectRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  | [optional]
**description** | **string** |  | [optional]
**logo_url** | **string** | Public URL for the project logo/brand image. Prefer uploading via **POST /api/projects/{id}/logo** (stored under logo/project/ in platform storage). Used in project-related emails. | [optional]
**settings** | [**\OpenAPI\Client\Model\ProjectSettings**](ProjectSettings.md) |  | [optional]
**auth** | [**\OpenAPI\Client\Model\AuthConfig**](AuthConfig.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
