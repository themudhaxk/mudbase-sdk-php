# # MultiRoleUpdateRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  | [optional]
**description** | **string** |  | [optional]
**signup_endpoint** | **string** |  | [optional]
**requires_approval** | **bool** |  | [optional]
**requires_payment** | **bool** |  | [optional]
**requires_kyc** | **bool** |  | [optional]
**default_permissions** | **object[]** |  | [optional]
**collection_permissions** | [**array<string,\OpenAPI\Client\Model\MultiRoleUpdateRoleRequestCollectionPermissionsValue>**](MultiRoleUpdateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map (same as POST add role). | [optional]
**metadata** | **object** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
