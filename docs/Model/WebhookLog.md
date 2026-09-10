# # WebhookLog

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** | MongoDB id — use as &#x60;webhookId&#x60; path param for retry | [optional]
**org** | **string** | Organization that owns the project | [optional]
**project** | **string** | Project id this delivery belongs to | [optional]
**webhook_id** | **string** | Internal correlation string (e.g. manual-173…), not the retry path id | [optional]
**url** | **string** |  | [optional]
**method** | **string** |  | [optional]
**event** | **string** |  | [optional]
**status** | **string** |  | [optional]
**payload** | **object** | JSON body sent to your endpoint | [optional]
**headers** | **object** | Outbound request headers (e.g. X-MUDBASE-Event, Content-Type) | [optional]
**response** | [**\MudbaseSDK\Model\WebhookLogResponse**](WebhookLogResponse.md) |  | [optional]
**duration** | **int** | Round-trip time in milliseconds | [optional]
**attempts** | **int** |  | [optional]
**max_attempts** | **int** |  | [optional]
**error** | **string** |  | [optional]
**next_retry** | **\DateTime** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
