# # GetPayoutCountries200ResponseDataCountriesInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**code** | **string** | ISO-3166 alpha-2 country code (e.g. NG, GH, KE, US, GB). | [optional]
**name** | **string** |  | [optional]
**currency** | **string** |  | [optional]
**banks_list_supported** | **bool** | Whether GET /payment-processing/banks returns a live bank list for this country. | [optional]
**mobile_money** | **bool** |  | [optional]
**international** | **bool** | True for a market whose settlement rail requires an account-level capability beyond the standard local-rail onboarding (currently US, GB). | [optional]
**fields** | [**\MudbaseSDK\Model\GetPayoutCountries200ResponseDataCountriesInnerFieldsInner[]**](GetPayoutCountries200ResponseDataCountriesInnerFieldsInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
