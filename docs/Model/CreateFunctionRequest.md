# # CreateFunctionRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  |
**description** | **string** |  | [optional]
**code** | **string** | Function body (async, has access to payload, db, files, messaging, wallet, utils, env, console) |
**trigger** | [**\OpenAPI\Client\Model\FunctionTrigger**](FunctionTrigger.md) |  |
**environment** | **array<string,string>** | Per-function env vars injected into sandbox | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
