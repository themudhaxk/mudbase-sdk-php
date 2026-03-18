# # PresignedPostResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**key** | **string** | Object key (S3) clients should upload to | [optional]
**url** | **string** | URL to POST the multipart form to | [optional]
**fields** | **object** | Form fields required for the presigned POST (Policy, X-Amz-Signature, etc.) | [optional]
**expires_in** | **int** | Expiration of the presigned POST in seconds | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
