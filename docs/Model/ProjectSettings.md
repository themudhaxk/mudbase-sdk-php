# # ProjectSettings

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**allow_anonymous_auth** | **bool** | Allow anonymous (unauthenticated) users | [optional] [default to true]
**require_email_verification** | **bool** | When true, users who sign up with email do not receive a token until they verify their email; login is blocked until verified. | [optional] [default to true]
**require_phone_verification** | **bool** | When true, users who sign in with phone (e.g. OTP) must have verified their phone before receiving a token. | [optional] [default to false]
**default_user_account_status** | **string** | Default account status for new signups. **active** &#x3D; user can use the app immediately. **pending** &#x3D; user must be approved by an org owner/admin (PATCH org user status to active) before they can perform protected operations. | [optional] [default to 'active']
**enable_realtime** | **bool** |  | [optional] [default to true]
**enable_storage** | **bool** |  | [optional] [default to true]
**enable_functions** | **bool** |  | [optional] [default to false]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
