# # GetPaymentProcessingStatus200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**onboarded** | **bool** |  | [optional]
**enabled** | **bool** | Whether payment collection is actually toggled on (implies approved). | [optional]
**approval_status** | **string** | not_submitted, pending_review, approved, or rejected. | [optional]
**status** | **string** | Derived overall status for the console to render: not_onboarded, pending_review, rejected, disabled, or active. | [optional]
**rejection_reason** | **string** |  | [optional]
**stablecoin** | [**\MudbaseSDK\Model\GetPaymentProcessingStatus200ResponseDataStablecoin**](GetPaymentProcessingStatus200ResponseDataStablecoin.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
