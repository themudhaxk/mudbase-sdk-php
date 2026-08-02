# # McpConfigGet200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**enabled** | **bool** |  | [optional]
**plan** | **string** |  | [optional]
**allowed_plans** | **string[]** |  | [optional]
**free_promo_active** | **bool** | True if this org is on the free plan and MCP is temporarily enabled via the launch promo | [optional]
**free_promo_ends_at** | **\DateTime** | When the free-plan MCP promo ends (null if not active) | [optional]
**endpoint** | **string** |  | [optional]
**tools** | [**\OpenAPI\Client\Model\McpConfigGet200ResponseToolsInner[]**](McpConfigGet200ResponseToolsInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
