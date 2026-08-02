# # CreateRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  |
**description** | **string** |  | [optional]
**permissions** | [**\OpenAPI\Client\Model\CreateRoleRequestPermissionsInner[]**](CreateRoleRequestPermissionsInner.md) | Legacy resource-level permissions. For data CRUD, prefer &#x60;collectionPermissions&#x60; below. | [optional]
**hierarchy** | **float** |  | [optional]
**collection_permissions** | [**array<string,\OpenAPI\Client\Model\CreateRoleRequestCollectionPermissionsValue>**](CreateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; value can be action array or object with actions + conditions. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
