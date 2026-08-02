# OpenAPI\Client\EmailApi

Project-scoped transactional email queue, templates, analytics, and BYO SMTP (&#x60;/api/projects/{projectId}/email/...&#x60;).  ### Template &#x60;{{placeholders}}&#x60; rules  - Placeholders use the form &#x60;{{variableName}}&#x60; (case-sensitive). Every name that appears in &#x60;subject&#x60;, &#x60;htmlBody&#x60;, or &#x60;textBody&#x60; must be listed in the request body **&#x60;variables&#x60;** array **without** braces (e.g. use &#x60;userName&#x60; for &#x60;{{userName}}&#x60;). - When sending with **&#x60;POST .../email/send&#x60;**, pass values in **&#x60;data&#x60;**. The worker merges &#x60;data&#x60; with **layout defaults** (branding, footer, year, etc. from &#x60;augmentTemplateData&#x60;). - **Outer email shell** (header logo, brand title, footer, “Powered by …” on free plan) is applied **after** your HTML is rendered. You normally do **not** put shell tokens inside &#x60;htmlBody&#x60;; they are filled by the platform around your content.  ### Common placeholders (transactional / auth templates)  **Identity &amp; app:** &#x60;{{appName}}&#x60;, &#x60;{{appNameDisplay}}&#x60;, &#x60;{{userName}}&#x60;, &#x60;{{USER_NAME}}&#x60;, &#x60;{{USER_EMAIL}}&#x60;, &#x60;{{orgName}}&#x60;, &#x60;{{projectName}}&#x60;, &#x60;{{projectId}}&#x60;.  **Links &amp; actions:** &#x60;{{resetUrl}}&#x60;, &#x60;{{verificationUrl}}&#x60;, &#x60;{{invitationUrl}}&#x60;, &#x60;{{magicLinkUrl}}&#x60;, &#x60;{{paymentLink}}&#x60;, &#x60;{{CTA_URL}}&#x60;, &#x60;{{SECURITY_URL}}&#x60;, &#x60;{{PLATFORM_URL}}&#x60;.  **Invites &amp; roles:** &#x60;{{inviterName}}&#x60;, &#x60;{{role}}&#x60;.  **OTP / expiry copy:** &#x60;{{otpCode}}&#x60;, &#x60;{{EXPIRY_MINUTES}}&#x60;, &#x60;{{expiresIn}}&#x60;.  **Sign-in alerts:** &#x60;{{REQUEST_TIME}}&#x60;, &#x60;{{REQUEST_IP}}&#x60;.  **Plans &amp; account:** &#x60;{{planName}}&#x60;, &#x60;{{PLAN_NAME}}&#x60;, &#x60;{{JOIN_DATE}}&#x60;.  **Usage &amp; org limits:** &#x60;{{percent}}&#x60;, &#x60;{{resource}}&#x60;, &#x60;{{used}}&#x60;, &#x60;{{limit}}&#x60;, &#x60;{{cutOffNote}}&#x60;.  **Overage &amp; spend (org billing emails):** &#x60;{{amount}}&#x60;, &#x60;{{period}}&#x60;, &#x60;{{softLimit}}&#x60;, &#x60;{{hardLimit}}&#x60;, &#x60;{{threshold}}&#x60;.  **Payout alerts:** &#x60;{{currency}}&#x60;, &#x60;{{errorMessage}}&#x60;, &#x60;{{collectedAmount}}&#x60;, &#x60;{{threshold}}&#x60; (along with &#x60;{{projectId}}&#x60; above).  ### Layout / branding (injected around your body; optional to reference in custom HTML)  Filled by the renderer when the shared layout wraps content: branding and footer context includes values such as **&#x60;BRAND_NAME&#x60;**, **&#x60;BRAND_INITIAL&#x60;**, **&#x60;LOGO_URL&#x60;**, **&#x60;primaryColor&#x60;**, **&#x60;senderLine&#x60;**, **&#x60;YEAR&#x60;**, **&#x60;PLATFORM_NAME&#x60;**, **&#x60;footerLine&#x60;**, **&#x60;POWERED_BY_PLATFORM&#x60;** (HTML fragment when shown). If you reference any of these **inside** your &#x60;subject&#x60; / &#x60;htmlBody&#x60; / &#x60;textBody&#x60;, include the matching key in **&#x60;variables&#x60;** as well.  ### Platform billing notification templates (separate helpers, e.g. subscription / trial / payment failed)  Typical keys include: &#x60;{{customerName}}&#x60;, &#x60;{{planName}}&#x60;, &#x60;{{currency}}&#x60;, &#x60;{{amount}}&#x60;, &#x60;{{billingCycle}}&#x60;, &#x60;{{nextBillingDate}}&#x60;, &#x60;{{endDate}}&#x60;, &#x60;{{dueDate}}&#x60;, &#x60;{{updatePaymentUrl}}&#x60;, &#x60;{{daysLeft}}&#x60;, &#x60;{{monthlyAmount}}&#x60;, &#x60;{{yearlyAmount}}&#x60;, &#x60;{{savings}}&#x60;, &#x60;{{subscribeUrl}}&#x60;.  ### Master list (every documented token, &#x60;{{name}}&#x60; form)  Alphabetical (case-sensitive token names as used in templates):  &#x60;{{amount}}&#x60;, &#x60;{{appName}}&#x60;, &#x60;{{appNameDisplay}}&#x60;, &#x60;{{billingCycle}}&#x60;, &#x60;{{BRAND_INITIAL}}&#x60;, &#x60;{{BRAND_NAME}}&#x60;, &#x60;{{collectedAmount}}&#x60;, &#x60;{{content}}&#x60;, &#x60;{{CTA_URL}}&#x60;, &#x60;{{currency}}&#x60;, &#x60;{{customerName}}&#x60;, &#x60;{{cutOffNote}}&#x60;, &#x60;{{daysLeft}}&#x60;, &#x60;{{dueDate}}&#x60;, &#x60;{{endDate}}&#x60;, &#x60;{{errorMessage}}&#x60;, &#x60;{{EXPIRY_MINUTES}}&#x60;, &#x60;{{expiresIn}}&#x60;, &#x60;{{footerLine}}&#x60;, &#x60;{{hardLimit}}&#x60;, &#x60;{{HEADER_LOGO}}&#x60;, &#x60;{{invitationUrl}}&#x60;, &#x60;{{inviterName}}&#x60;, &#x60;{{JOIN_DATE}}&#x60;, &#x60;{{limit}}&#x60;, &#x60;{{LOGO_URL}}&#x60;, &#x60;{{magicLinkUrl}}&#x60;, &#x60;{{monthlyAmount}}&#x60;, &#x60;{{nextBillingDate}}&#x60;, &#x60;{{orgName}}&#x60;, &#x60;{{otpCode}}&#x60;, &#x60;{{paymentLink}}&#x60;, &#x60;{{percent}}&#x60;, &#x60;{{period}}&#x60;, &#x60;{{PLAN_NAME}}&#x60;, &#x60;{{planName}}&#x60;, &#x60;{{PLATFORM_NAME}}&#x60;, &#x60;{{PLATFORM_URL}}&#x60;, &#x60;{{POWERED_BY_PLATFORM}}&#x60;, &#x60;{{primaryColor}}&#x60;, &#x60;{{projectId}}&#x60;, &#x60;{{projectName}}&#x60;, &#x60;{{REQUEST_IP}}&#x60;, &#x60;{{REQUEST_TIME}}&#x60;, &#x60;{{resetUrl}}&#x60;, &#x60;{{resource}}&#x60;, &#x60;{{role}}&#x60;, &#x60;{{SECURITY_URL}}&#x60;, &#x60;{{senderLine}}&#x60;, &#x60;{{savings}}&#x60;, &#x60;{{softLimit}}&#x60;, &#x60;{{subscribeUrl}}&#x60;, &#x60;{{threshold}}&#x60;, &#x60;{{updatePaymentUrl}}&#x60;, &#x60;{{used}}&#x60;, &#x60;{{USER_EMAIL}}&#x60;, &#x60;{{USER_NAME}}&#x60;, &#x60;{{userName}}&#x60;, &#x60;{{verificationUrl}}&#x60;, &#x60;{{YEAR}}&#x60;, &#x60;{{yearlyAmount}}&#x60;.  Custom templates may introduce other names; anything you type as &#x60;{{token}}&#x60; must be listed in **&#x60;variables&#x60;** and supplied (or defaulted) via **&#x60;data&#x60;** / layout.  Use **GET** &#x60;/api/projects/{projectId}/email/templates&#x60; and **GET** &#x60;/api/projects/{projectId}/email/templates/{name}&#x60; to see which names exist and whether the project uses a **custom** override (&#x60;isCustomized&#x60; / &#x60;isProjectOverride&#x60;).

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**enqueueProjectEmail()**](EmailApi.md#enqueueProjectEmail) | **POST** /api/projects/{projectId}/email/send | Enqueue project email (worker delivery) |
| [**getProjectEmailAnalytics()**](EmailApi.md#getProjectEmailAnalytics) | **GET** /api/projects/{projectId}/analytics/email | Email analytics for a project |
| [**getProjectEmailSmtp()**](EmailApi.md#getProjectEmailSmtp) | **GET** /api/projects/{projectId}/email/smtp | Get project SMTP settings (masked) |
| [**getProjectEmailTemplate()**](EmailApi.md#getProjectEmailTemplate) | **GET** /api/projects/{projectId}/email/templates/{name} | Get one email template (effective content) |
| [**listProjectEmailTemplates()**](EmailApi.md#listProjectEmailTemplates) | **GET** /api/projects/{projectId}/email/templates | List email templates (full catalog for the project) |
| [**patchProjectEmailSmtp()**](EmailApi.md#patchProjectEmailSmtp) | **PATCH** /api/projects/{projectId}/email/smtp | Update project SMTP relay (BYO) |
| [**previewProjectEmailTemplate()**](EmailApi.md#previewProjectEmailTemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/preview | Render template preview (sanitized HTML, no send) |
| [**restoreDefaultProjectEmailTemplate()**](EmailApi.md#restoreDefaultProjectEmailTemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/restore-default | Restore from platform global default or remove project override |
| [**testProjectEmailSmtp()**](EmailApi.md#testProjectEmailSmtp) | **POST** /api/projects/{projectId}/email/smtp/test | Verify SMTP and send a test message |
| [**upsertProjectEmailTemplate()**](EmailApi.md#upsertProjectEmailTemplate) | **PUT** /api/projects/{projectId}/email/templates/{name} | Upsert project email template (HTML sanitized; variables must cover {{placeholders}}) |
| [**verifyProjectEmailSmtpDomain()**](EmailApi.md#verifyProjectEmailSmtpDomain) | **POST** /api/projects/{projectId}/email/smtp/verify-domain | Check DNS (MX + SPF) for sending domain |


## `enqueueProjectEmail()`

```php
enqueueProjectEmail($project_id, $project_email_send_request): \OpenAPI\Client\Model\EnqueueProjectEmail202Response
```

Enqueue project email (worker delivery)

Queues a transactional email for sending through the email worker and configured provider (platform or per-project SMTP). Provide either `template` (with `data`) or both `subject` and `html`. Returns **202** with `jobId` when accepted.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$project_email_send_request = {"template":"magicLink","to":"user@example.com","data":{"userName":"Alex","magicLinkUrl":"https://app.example.com/auth/verify?token=abc","expiresIn":"15 minutes"},"idempotencyKey":"proj123:magicLink:user@example.com"}; // \OpenAPI\Client\Model\ProjectEmailSendRequest

try {
    $result = $apiInstance->enqueueProjectEmail($project_id, $project_email_send_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->enqueueProjectEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **project_email_send_request** | [**\OpenAPI\Client\Model\ProjectEmailSendRequest**](../Model/ProjectEmailSendRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\EnqueueProjectEmail202Response**](../Model/EnqueueProjectEmail202Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectEmailAnalytics()`

```php
getProjectEmailAnalytics($project_id, $from, $to): \OpenAPI\Client\Model\GetProjectEmailAnalytics200Response
```

Email analytics for a project

Aggregated email log stats for the project. Optional `from` and `to` query params filter by date range (ISO 8601).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$from = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$to = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime

try {
    $result = $apiInstance->getProjectEmailAnalytics($project_id, $from, $to);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->getProjectEmailAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **from** | **\DateTime**|  | [optional] |
| **to** | **\DateTime**|  | [optional] |

### Return type

[**\OpenAPI\Client\Model\GetProjectEmailAnalytics200Response**](../Model/GetProjectEmailAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectEmailSmtp()`

```php
getProjectEmailSmtp($project_id): \OpenAPI\Client\Model\GetProjectEmailSmtp200Response
```

Get project SMTP settings (masked)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->getProjectEmailSmtp($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->getProjectEmailSmtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetProjectEmailSmtp200Response**](../Model/GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProjectEmailTemplate()`

```php
getProjectEmailTemplate($project_id, $name): \OpenAPI\Client\Model\GetProjectEmailTemplate200Response
```

Get one email template (effective content)

Returns the template body that would be used when sending: project override if present, else global default, else built-in fallback. **`isProjectOverride`** is true only when this project has a stored row; **`effectiveSource`** is `project`, `global`, or `builtin`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$name = 'name_example'; // string

try {
    $result = $apiInstance->getProjectEmailTemplate($project_id, $name);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->getProjectEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **name** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\GetProjectEmailTemplate200Response**](../Model/GetProjectEmailTemplate200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listProjectEmailTemplates()`

```php
listProjectEmailTemplates($project_id): \OpenAPI\Client\Model\ListProjectEmailTemplates200Response
```

List email templates (full catalog for the project)

Returns every template name the worker can resolve for this project: **built-in** defaults, **global** platform rows (`project: null` in DB), and **project** overrides. Use **`isCustomized`** to see if this project has its own stored copy; **`effectiveSource`** shows which layer would be used at send time (`project` wins over `global` over `builtin`).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string

try {
    $result = $apiInstance->listProjectEmailTemplates($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->listProjectEmailTemplates: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |

### Return type

[**\OpenAPI\Client\Model\ListProjectEmailTemplates200Response**](../Model/ListProjectEmailTemplates200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `patchProjectEmailSmtp()`

```php
patchProjectEmailSmtp($project_id, $project_smtp_patch_request): \OpenAPI\Client\Model\GetProjectEmailSmtp200Response
```

Update project SMTP relay (BYO)

Set `authPass` in the body to store an encrypted password (never returned on GET). Validates host/user when enabling.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$project_smtp_patch_request = {"enabled":true,"host":"smtp.sendgrid.net","port":587,"secure":false,"authUser":"apikey","authPass":"SG.xxxx","fromName":"Acme App","fromEmail":"noreply@mail.example.com"}; // \OpenAPI\Client\Model\ProjectSmtpPatchRequest

try {
    $result = $apiInstance->patchProjectEmailSmtp($project_id, $project_smtp_patch_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->patchProjectEmailSmtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **project_smtp_patch_request** | [**\OpenAPI\Client\Model\ProjectSmtpPatchRequest**](../Model/ProjectSmtpPatchRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\GetProjectEmailSmtp200Response**](../Model/GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `previewProjectEmailTemplate()`

```php
previewProjectEmailTemplate($project_id, $name, $preview_project_email_template_request)
```

Render template preview (sanitized HTML, no send)

Body **`sampleData`** is merged with layout defaults; keys should match `{{placeholders}}` in the template (see **Email** tag for the catalog).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$name = 'name_example'; // string
$preview_project_email_template_request = {"sampleData":{}}; // \OpenAPI\Client\Model\PreviewProjectEmailTemplateRequest

try {
    $apiInstance->previewProjectEmailTemplate($project_id, $name, $preview_project_email_template_request);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->previewProjectEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **name** | **string**|  | |
| **preview_project_email_template_request** | [**\OpenAPI\Client\Model\PreviewProjectEmailTemplateRequest**](../Model/PreviewProjectEmailTemplateRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `restoreDefaultProjectEmailTemplate()`

```php
restoreDefaultProjectEmailTemplate($project_id, $name)
```

Restore from platform global default or remove project override

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$name = 'name_example'; // string

try {
    $apiInstance->restoreDefaultProjectEmailTemplate($project_id, $name);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->restoreDefaultProjectEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **name** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `testProjectEmailSmtp()`

```php
testProjectEmailSmtp($project_id, $project_smtp_test_request): \OpenAPI\Client\Model\DeleteFunction200Response
```

Verify SMTP and send a test message

Rate-limited. With `useSaved: true` (default), uses stored credentials; otherwise pass `host`, `authUser`, `authPass`, etc.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$project_smtp_test_request = {"to":"ops@example.com","useSaved":true}; // \OpenAPI\Client\Model\ProjectSmtpTestRequest

try {
    $result = $apiInstance->testProjectEmailSmtp($project_id, $project_smtp_test_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->testProjectEmailSmtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **project_smtp_test_request** | [**\OpenAPI\Client\Model\ProjectSmtpTestRequest**](../Model/ProjectSmtpTestRequest.md)|  | |

### Return type

[**\OpenAPI\Client\Model\DeleteFunction200Response**](../Model/DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `upsertProjectEmailTemplate()`

```php
upsertProjectEmailTemplate($project_id, $name, $upsert_project_email_template_request)
```

Upsert project email template (HTML sanitized; variables must cover {{placeholders}})

Saves a **project override** for `name`. HTML is sanitized. **`variables`** must list every `{{token}}` used in `subject`, `htmlBody`, and `textBody` (see **Email** tag description for the full placeholder catalog).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$name = 'name_example'; // string
$upsert_project_email_template_request = {"subject":"subject_example","htmlBody":"htmlBody_example"}; // \OpenAPI\Client\Model\UpsertProjectEmailTemplateRequest

try {
    $apiInstance->upsertProjectEmailTemplate($project_id, $name, $upsert_project_email_template_request);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->upsertProjectEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **name** | **string**|  | |
| **upsert_project_email_template_request** | [**\OpenAPI\Client\Model\UpsertProjectEmailTemplateRequest**](../Model/UpsertProjectEmailTemplateRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyProjectEmailSmtpDomain()`

```php
verifyProjectEmailSmtpDomain($project_id, $verify_project_email_smtp_domain_request)
```

Check DNS (MX + SPF) for sending domain

Resolves the domain from `domain`, `fromEmail`, or saved `emailSmtp.fromEmail`. Returns whether MX and SPF TXT exist. With `persist: true` and checks passed, sets `emailSmtp.domainVerifiedAt`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure API key authorization: ApiKeyAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-API-Key', 'Bearer');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$verify_project_email_smtp_domain_request = {"domain":"domain_example","fromEmail":"fromEmail_example","persist":true}; // \OpenAPI\Client\Model\VerifyProjectEmailSmtpDomainRequest

try {
    $apiInstance->verifyProjectEmailSmtpDomain($project_id, $verify_project_email_smtp_domain_request);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->verifyProjectEmailSmtpDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **verify_project_email_smtp_domain_request** | [**\OpenAPI\Client\Model\VerifyProjectEmailSmtpDomainRequest**](../Model/VerifyProjectEmailSmtpDomainRequest.md)|  | [optional] |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ApiKeyAuth](../../README.md#ApiKeyAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
