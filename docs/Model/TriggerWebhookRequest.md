# # TriggerWebhookRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**project_id** | **string** | Target project (must belong to your org) |
**url** | **string** | HTTPS URL validated against SSRF rules |
**event** | **string** | Event name (sent as X-MUDBASE-Event) |
**payload** | **object** | JSON body POSTed to your endpoint |
**method** | **string** |  | [optional] [default to 'POST']

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
