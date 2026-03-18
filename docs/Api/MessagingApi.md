# OpenAPI\Client\MessagingApi

Push notifications, email, and SMS

All URIs are relative to https://cloud.dev.mudbase, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**messagingGetHistory()**](MessagingApi.md#messagingGetHistory) | **GET** /api/messaging/projects/{projectId}/messaging/history | Get message history |
| [**messagingGetStats()**](MessagingApi.md#messagingGetStats) | **GET** /api/messaging/projects/{projectId}/messaging/stats | Get message statistics |
| [**messagingSendEmail()**](MessagingApi.md#messagingSendEmail) | **POST** /api/messaging/projects/{projectId}/messaging/email | Send transactional email |
| [**messagingSendPush()**](MessagingApi.md#messagingSendPush) | **POST** /api/messaging/projects/{projectId}/messaging/push | Send push notification |
| [**messagingSendSms()**](MessagingApi.md#messagingSendSms) | **POST** /api/messaging/projects/{projectId}/messaging/sms | Send SMS to one or more recipients (E.164 format) |


## `messagingGetHistory()`

```php
messagingGetHistory($project_id, $type, $page, $limit, $status): \OpenAPI\Client\Model\MessageHistoryResponse
```

Get message history

Get message history (push, email, SMS) with filtering and pagination. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the messaging project.
$type = 'type_example'; // string | Filter by message type (push, email, or sms).
$page = 1; // int | Page number for pagination (1-based).
$limit = 20; // int | Maximum number of messages per page.
$status = 'status_example'; // string | Filter by delivery status.

try {
    $result = $apiInstance->messagingGetHistory($project_id, $type, $page, $limit, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MessagingApi->messagingGetHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **type** | **string**| Filter by message type (push, email, or sms). | [optional] |
| **page** | **int**| Page number for pagination (1-based). | [optional] [default to 1] |
| **limit** | **int**| Maximum number of messages per page. | [optional] [default to 20] |
| **status** | **string**| Filter by delivery status. | [optional] |

### Return type

[**\OpenAPI\Client\Model\MessageHistoryResponse**](../Model/MessageHistoryResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `messagingGetStats()`

```php
messagingGetStats($project_id, $start_date, $end_date): \OpenAPI\Client\Model\MessageStatsResponse
```

Get message statistics

Get messaging statistics including total messages, success rates, and breakdown by type (push, email, SMS). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the messaging project.
$start_date = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Start of the date range for statistics (ISO 8601).
$end_date = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | End of the date range for statistics (ISO 8601).

try {
    $result = $apiInstance->messagingGetStats($project_id, $start_date, $end_date);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MessagingApi->messagingGetStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **start_date** | **\DateTime**| Start of the date range for statistics (ISO 8601). | [optional] |
| **end_date** | **\DateTime**| End of the date range for statistics (ISO 8601). | [optional] |

### Return type

[**\OpenAPI\Client\Model\MessageStatsResponse**](../Model/MessageStatsResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `messagingSendEmail()`

```php
messagingSendEmail($project_id, $email_request): \OpenAPI\Client\Model\MessageSentResponse
```

Send transactional email

Send a transactional email to one or more recipients. Supports HTML and plain text. Use for verification emails, password resets, notifications, and marketing. Attachments and templates can be configured per project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the messaging project.
$email_request = {"to":"user@example.com","subject":"Welcome to Mudbase","html":"<h1>Welcome!</h1><p>Thank you for joining.</p>","text":"Welcome! Thank you for joining."}; // \OpenAPI\Client\Model\EmailRequest | Recipient(s), subject, HTML and/or plain text body; optional reply-to and attachments.

try {
    $result = $apiInstance->messagingSendEmail($project_id, $email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MessagingApi->messagingSendEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **email_request** | [**\OpenAPI\Client\Model\EmailRequest**](../Model/EmailRequest.md)| Recipient(s), subject, HTML and/or plain text body; optional reply-to and attachments. | |

### Return type

[**\OpenAPI\Client\Model\MessageSentResponse**](../Model/MessageSentResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `messagingSendPush()`

```php
messagingSendPush($project_id, $push_notification_request): \OpenAPI\Client\Model\MessageSentResponse
```

Send push notification

Send a push notification to one or more devices. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the messaging project.
$push_notification_request = {"tokens":["device_token_123","device_token_456"],"title":"New Notification","body":"You have a new message","data":{},"imageUrl":"https://example.com/image.jpg"}; // \OpenAPI\Client\Model\PushNotificationRequest | Device tokens, notification title/body, optional data payload and image URL.

try {
    $result = $apiInstance->messagingSendPush($project_id, $push_notification_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MessagingApi->messagingSendPush: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **push_notification_request** | [**\OpenAPI\Client\Model\PushNotificationRequest**](../Model/PushNotificationRequest.md)| Device tokens, notification title/body, optional data payload and image URL. | |

### Return type

[**\OpenAPI\Client\Model\MessageSentResponse**](../Model/MessageSentResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `messagingSendSms()`

```php
messagingSendSms($project_id, $sms_request): \OpenAPI\Client\Model\MessageSentResponse
```

Send SMS to one or more recipients (E.164 format)

Send an SMS message to one or more phone numbers in E.164 format. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\MessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID (MongoDB ObjectId) for the messaging project.
$sms_request = {"to":"+1234567890","message":"Your verification code is 123456","from":"Mudbase"}; // \OpenAPI\Client\Model\SMSRequest | Recipient phone number(s), message body, and optional sender ID.

try {
    $result = $apiInstance->messagingSendSms($project_id, $sms_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MessagingApi->messagingSendSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID (MongoDB ObjectId) for the messaging project. | |
| **sms_request** | [**\OpenAPI\Client\Model\SMSRequest**](../Model/SMSRequest.md)| Recipient phone number(s), message body, and optional sender ID. | |

### Return type

[**\OpenAPI\Client\Model\MessageSentResponse**](../Model/MessageSentResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
