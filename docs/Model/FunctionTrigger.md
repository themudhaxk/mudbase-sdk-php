# # FunctionTrigger

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Trigger type |
**event** | **string** | Event name (e.g. create, update, delete for document; uploaded, deleted for file; tx, balance for wallet) | [optional]
**schedule** | **string** | For cron - minutely, hourly, daily, weekly, or custom cron expression | [optional]
**path** | **string** | HTTP path for http triggers | [optional]
**method** | **string** |  | [optional]
**collection_id** | **string** | For document triggers - filter by collection | [optional]
**bucket_id** | **string** | For file triggers - filter by bucket | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
