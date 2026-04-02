# # MultiRoleUpdateCollectionPermissionsRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**actions** | **string[]** |  | [optional]
**conditions** | **object** |  | [optional]
**data_scope** | **string** | &#x60;all&#x60; &#x3D; no automatic row-owner filter. &#x60;own&#x60; &#x3D; only documents where the owner field (default &#x60;createdBy&#x60;) matches the authenticated app user. | [optional]
**owner_field** | **string** | Optional per-assignment override for the document field used when &#x60;dataScope&#x60; is &#x60;own&#x60; (project default is &#x60;settings.dataOwnerField&#x60;, usually &#x60;createdBy&#x60;). | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
