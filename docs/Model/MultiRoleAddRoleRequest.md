# # MultiRoleAddRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**slug** | **string** |  |
**name** | **string** |  |
**description** | **string** |  | [optional]
**signup_endpoint** | **string** |  |
**default_permissions** | [**\OpenAPI\Client\Model\MultiRoleAddRoleRequestDefaultPermissionsInner[]**](MultiRoleAddRoleRequestDefaultPermissionsInner.md) | Optional global/base permissions. For collection-level CRUD use &#x60;collectionPermissions&#x60;. | [optional]
**collection_permissions** | [**array<string,\OpenAPI\Client\Model\MultiRoleUpdateRoleRequestCollectionPermissionsValue>**](MultiRoleUpdateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; values are action arrays or objects with &#x60;actions&#x60; + optional &#x60;conditions&#x60;. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
