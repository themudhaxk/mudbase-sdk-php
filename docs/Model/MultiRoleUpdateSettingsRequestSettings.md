# # MultiRoleUpdateSettingsRequestSettings

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**allow_multiple_roles** | **bool** | Whether an end user may hold multiple app roles. | [optional]
**require_role_selection** | **bool** | If true, signup must pick a role; if false and &#x60;autoAssignDefault&#x60; is true, &#x60;defaultRole&#x60; is used when omitted. | [optional]
**auto_assign_default** | **bool** | When true, assigns &#x60;defaultRole&#x60; when the client does not specify a role at signup. | [optional]
**data_owner_field** | **string** | Default document field for &#x60;dataScope: own&#x60; (e.g. &#x60;createdBy&#x60;, &#x60;userId&#x60;). | [optional] [default to 'createdBy']

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
