# # PresignedPostResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**key** | **string** | Object key (S3) clients should upload to | [optional]
**url** | **string** | Presigned URL to PUT the file body to directly | [optional]
**method** | **string** | HTTP method the client must use against &#x60;url&#x60; (always PUT - R2 does not implement the S3 POST Object API) | [optional]
**headers** | **object** | Headers the client must send with the PUT request (e.g. Content-Type) - mismatching these from what was signed causes a SignatureDoesNotMatch error | [optional]
**expires_in** | **int** | Expiration of the presigned URL in seconds | [optional]
**max_file_upload_bytes** | **int** | Maximum upload size in bytes for this org plan. Not enforced by the presigned URL itself (PUT has no content-length-range equivalent) - checked server-side by /api/files/upload/confirm after the upload completes | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
