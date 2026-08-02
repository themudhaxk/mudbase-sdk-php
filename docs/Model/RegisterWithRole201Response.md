# # RegisterWithRole201Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**message** | **string** |  | [optional]
**require_verification** | **bool** | True when the project requires email verification before a session is issued - no token is returned in that case. | [optional]
**token** | **string** | JWT access token. Absent when requireVerification is true. | [optional]
**refresh_token** | **string** | JWT refresh token. Absent when requireVerification is true. | [optional]
**expires_in** | **int** | Access token TTL in seconds. Absent when requireVerification is true. | [optional]
**user** | [**\OpenAPI\Client\Model\RegisterWithRole201ResponseUser**](RegisterWithRole201ResponseUser.md) |  | [optional]
**role** | [**\OpenAPI\Client\Model\RegisterWithRole201ResponseRole**](RegisterWithRole201ResponseRole.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
