# # AuthRegister201Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**message** | **string** |  | [optional]
**require_verification** | **bool** | true when email verification is required; no token in response | [optional]
**token** | **string** | Present only when requireEmailVerification is false | [optional]
**refresh_token** | **string** | Present only when requireEmailVerification is false | [optional]
**expires_in** | **int** | Present only when token is returned | [optional]
**user** | [**\OpenAPI\Client\Model\AuthRegister201ResponseUser**](AuthRegister201ResponseUser.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
