# # PushNotificationRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**tokens** | **string[]** | Registered device push tokens to deliver to (device-token channel). | [optional]
**endpoints** | **string[]** | Registered Web Push subscription endpoints to deliver to (native Web Push channel). | [optional]
**user_ids** | **string[]** | Deliver to every Web Push subscription registered under these user ids (native Web Push channel). | [optional]
**web_push_broadcast** | **bool** | When true, deliver to every enabled Web Push subscription registered to the project (native Web Push channel). Ignored when the project has not enabled native Web Push. | [optional]
**title** | **string** |  |
**body** | **string** |  |
**data** | **object** |  | [optional]
**image_url** | **string** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
