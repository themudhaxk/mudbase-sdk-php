# # WebPushConfigResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**enabled** | **bool** | Whether native Web Push is enabled for this project. | [optional]
**has_keys** | **bool** | Whether a VAPID keypair has been provisioned. | [optional]
**public_key** | **string** | The VAPID application-server public key clients subscribe with. Null when native Web Push is not enabled. | [optional]
**vapid_subject** | **string** | RFC 8292 contact subject (a &#x60;mailto:&#x60; address or &#x60;https&#x60; URL). | [optional]
**generated_at** | **\DateTime** | When the current VAPID keypair was generated. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
