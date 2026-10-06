# # RegisterRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **string** |  |
**password** | **string** |  |
**first_name** | **string** |  |
**last_name** | **string** |  |
**org_name** | **string** |  | [optional]
**agreed_to_terms** | **bool** | Must be &#x60;true&#x60; - the server rejects the request otherwise. Required to stop a direct API call from creating an account without accepting the Terms of Service and Privacy Policy. |
**captcha** | **string** | Google reCAPTCHA v3 response token, required only when the platform&#39;s anti-bot CAPTCHA gate is enabled. A missing token then gets a 400 with &#x60;captchaRequired: true&#x60; and a &#x60;siteKey&#x60;. Solving this needs a real browser, so this endpoint backs the web console&#39;s own signup form (&#x60;https://www.mudbase.dev/console/register&#x60;) and is not meant for scripted/server-to-server account creation. To integrate: create your Mudbase account once through the console, then use the API key from Settings -&gt; API Keys for everything else - collections, documents, storage, and the rest of the API are all fully scriptable from there. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
