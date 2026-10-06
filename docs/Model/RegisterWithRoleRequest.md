# # RegisterWithRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **string** |  |
**password** | **string** |  |
**first_name** | **string** |  |
**last_name** | **string** |  |
**project_id** | **string** |  |
**agreed_to_terms** | **bool** | Optional. End users signing up inside a customer&#39;s app have never seen or agreed to Mudbase&#39;s own Terms of Service, so this field is not required here and is never recorded as platform ToS acceptance. A generated-app form may send it if the app has its own ToS checkbox, but Mudbase does not write it to any consent record. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
