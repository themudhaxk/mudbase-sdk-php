# # MultiRoleAddRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**slug** | **string** |  |
**name** | **string** |  |
**description** | **string** |  | [optional]
**signup_endpoint** | **string** |  |
**requires_approval** | **bool** |  | [optional]
**requires_payment** | **bool** |  | [optional]
**requires_kyc** | **bool** |  | [optional]
**default_permissions** | [**\OpenAPI\Client\Model\MultiRoleAddRoleRequestDefaultPermissionsInner[]**](MultiRoleAddRoleRequestDefaultPermissionsInner.md) | Optional global/base permissions. For collection-level CRUD use &#x60;collectionPermissions&#x60;. | [optional]
**collection_permissions** | [**array<string,\OpenAPI\Client\Model\AppRoleCollectionPermissionValue>**](AppRoleCollectionPermissionValue.md) | Per-collection CRUD map. Keys are collection slugs; values are action arrays or objects with &#x60;actions&#x60; + optional &#x60;conditions&#x60;. | [optional]
**metadata** | **object** |  | [optional]
**feature_permissions** | **array<string,array<string,bool>>** | Per-role feature toggles for app JWTs: &#x60;{ [resource]: { [action]: boolean } }&#x60;. Use resource and action names that match the public API contract (see multi-role guide and simulate-permissions). **Messaging** accepts legacy keys (&#x60;email&#x60;, &#x60;sms&#x60;, &#x60;push&#x60;, …) and newer names (&#x60;send_email&#x60;, &#x60;send_sms&#x60;, …) as synonyms. Common resources: &#x60;messaging&#x60;, &#x60;integration&#x60;, &#x60;functions&#x60;, &#x60;data&#x60;, &#x60;search&#x60;, &#x60;usage&#x60;, &#x60;storage&#x60;, &#x60;chat&#x60;, &#x60;realtime&#x60;, &#x60;roleElevation&#x60;, &#x60;webhooks&#x60;. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
