# # InitializeOrgPlanCheckoutRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**plan_name** | **string** | Plan id from GET /api/billing/plans (excludes free and enterprise) |
**billing_cycle** | **string** | Yearly &#x3D; 8% discount | [optional] [default to 'monthly']
**redirect_url** | **string** | Override redirect after payment (default FRONTEND_URL/billing/callback) | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
