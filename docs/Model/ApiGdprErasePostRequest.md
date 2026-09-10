# # ApiGdprErasePostRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**confirm** | **string** | Must equal \&quot;DELETE\&quot; to proceed with erasure. |
**current_password** | **string** | Required unless the account has no password set (OAuth-only) | [optional]
**totp_token** | **string** | Required only if the account has 2FA enabled | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
