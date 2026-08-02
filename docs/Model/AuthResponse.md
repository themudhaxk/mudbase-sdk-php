# # AuthResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**message** | **string** |  | [optional]
**token** | **string** | JWT access token (use in Authorization Bearer header) | [optional]
**refresh_token** | **string** | JWT refresh token (use with POST /api/auth/refresh to get new token pair) | [optional]
**expires_in** | **int** | Access token TTL in seconds (e.g. 1800 for 30 minutes) | [optional]
**user** | [**\OpenAPI\Client\Model\User**](User.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
