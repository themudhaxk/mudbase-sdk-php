# # User

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**_id** | **string** |  | [optional]
**email** | **string** |  | [optional]
**first_name** | **string** |  | [optional]
**last_name** | **string** |  | [optional]
**full_name** | **string** |  | [optional]
**avatar** | **string** |  | [optional]
**role** | **string** |  | [optional]
**custom_role** | **string** | Application-level role slug from the project&#39;s Multi-Role feature (e.g. \&quot;customer\&quot;, \&quot;seller\&quot;). Null for org-level (org/admin/member/viewer) users who aren&#39;t project end-users. | [optional]
**is_anonymous** | **bool** | True for a guest session created via POST /api/auth/anonymous that hasn&#39;t been converted to a full account yet. | [optional]
**email_verified** | **bool** |  | [optional]
**phone_verified** | **bool** |  | [optional]
**two_factor_enabled** | **bool** |  | [optional]
**last_login** | **\DateTime** |  | [optional]
**created_at** | **\DateTime** |  | [optional]
**updated_at** | **\DateTime** |  | [optional]
**org** | [**\MudbaseSDK\Model\OrganizationSummary**](OrganizationSummary.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
