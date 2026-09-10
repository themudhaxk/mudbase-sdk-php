# # UpdateMultiRoleSettingsRequestSettings

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**allow_multiple_roles** | **bool** | Whether an end user may hold multiple app roles. | [optional]
**require_role_selection** | **bool** | If true, signup must pick a role; if false and &#x60;autoAssignDefault&#x60; is true, &#x60;defaultRole&#x60; is used when omitted. | [optional]
**auto_assign_default** | **bool** | When true, assigns &#x60;defaultRole&#x60; when the client does not specify a role at signup. | [optional]
**data_owner_field** | **string** | Default document field for dataScope &#x60;own&#x60; (e.g. createdBy, userId). | [optional] [default to 'createdBy']

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
