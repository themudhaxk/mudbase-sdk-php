# OpenAPI\Client\ChatApi

Real-time chat and messaging

All URIs are relative to https://cloud.dev.mudbase, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**chatAddParticipant()**](ChatApi.md#chatAddParticipant) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/participants | Add participant to chat |
| [**chatAddReaction()**](ChatApi.md#chatAddReaction) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Add reaction to message |
| [**chatCreate()**](ChatApi.md#chatCreate) | **POST** /api/chat/projects/{projectId}/chats | Create new chat |
| [**chatDeleteMessage()**](ChatApi.md#chatDeleteMessage) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Delete message |
| [**chatEditMessage()**](ChatApi.md#chatEditMessage) | **PATCH** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Edit message |
| [**chatGet()**](ChatApi.md#chatGet) | **GET** /api/chat/projects/{projectId}/chats/{chatId} | Get chat details |
| [**chatGetMessages()**](ChatApi.md#chatGetMessages) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/messages | Get chat messages |
| [**chatList()**](ChatApi.md#chatList) | **GET** /api/chat/projects/{projectId}/chats | Get user chats |
| [**chatMarkAsRead()**](ChatApi.md#chatMarkAsRead) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/read | Mark messages as read |
| [**chatRemoveParticipant()**](ChatApi.md#chatRemoveParticipant) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/participants | Remove participant from chat |
| [**chatRemoveReaction()**](ChatApi.md#chatRemoveReaction) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Remove reaction from message |
| [**chatSendMessage()**](ChatApi.md#chatSendMessage) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages | Send message |


## `chatAddParticipant()`

```php
chatAddParticipant($project_id, $chat_id, $chat_add_participant_request): \OpenAPI\Client\Model\ChatAddParticipant200Response
```

Add participant to chat

Add a user to the chat with an optional role (admin or member).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$chat_add_participant_request = {"userId":"685acbe0e129932fbb7a0fc2","role":"member"}; // \OpenAPI\Client\Model\ChatAddParticipantRequest | User ID to add and optional role (admin, member).

try {
    $result = $apiInstance->chatAddParticipant($project_id, $chat_id, $chat_add_participant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatAddParticipant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **chat_add_participant_request** | [**\OpenAPI\Client\Model\ChatAddParticipantRequest**](../Model/ChatAddParticipantRequest.md)| User ID to add and optional role (admin, member). | |

### Return type

[**\OpenAPI\Client\Model\ChatAddParticipant200Response**](../Model/ChatAddParticipant200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatAddReaction()`

```php
chatAddReaction($project_id, $chat_id, $message_id, $chat_add_reaction_request): \OpenAPI\Client\Model\ChatAddReaction200Response
```

Add reaction to message

Add an emoji reaction to a message.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$message_id = 'message_id_example'; // string | Message ID.
$chat_add_reaction_request = {"emoji":"👍"}; // \OpenAPI\Client\Model\ChatAddReactionRequest | Emoji reaction (e.g. 👍, ❤️).

try {
    $result = $apiInstance->chatAddReaction($project_id, $chat_id, $message_id, $chat_add_reaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatAddReaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **message_id** | **string**| Message ID. | |
| **chat_add_reaction_request** | [**\OpenAPI\Client\Model\ChatAddReactionRequest**](../Model/ChatAddReactionRequest.md)| Emoji reaction (e.g. 👍, ❤️). | |

### Return type

[**\OpenAPI\Client\Model\ChatAddReaction200Response**](../Model/ChatAddReaction200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatCreate()`

```php
chatCreate($project_id, $chat_create_request): \OpenAPI\Client\Model\ChatCreate201Response
```

Create new chat

Create a new chat (direct, group, channel, or broadcast) with name, type, participants, and optional settings.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_create_request = {"name":"Team Chat","description":"Main team communication","type":"group","participants":["685acbe0e129932fbb7a0fc2","685acbe0e129932fbb7a0fc3"],"settings":{}}; // \OpenAPI\Client\Model\ChatCreateRequest | Chat name, type (direct/group/channel/broadcast), participants array, optional description and settings.

try {
    $result = $apiInstance->chatCreate($project_id, $chat_create_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatCreate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_create_request** | [**\OpenAPI\Client\Model\ChatCreateRequest**](../Model/ChatCreateRequest.md)| Chat name, type (direct/group/channel/broadcast), participants array, optional description and settings. | |

### Return type

[**\OpenAPI\Client\Model\ChatCreate201Response**](../Model/ChatCreate201Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatDeleteMessage()`

```php
chatDeleteMessage($project_id, $chat_id, $message_id): \OpenAPI\Client\Model\MessageResponse
```

Delete message

Delete a message from the chat (sender or admin). May be soft-delete or permanent depending on implementation.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$message_id = 'message_id_example'; // string | Message ID.

try {
    $result = $apiInstance->chatDeleteMessage($project_id, $chat_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatDeleteMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **message_id** | **string**| Message ID. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatEditMessage()`

```php
chatEditMessage($project_id, $chat_id, $message_id, $chat_edit_message_request): \OpenAPI\Client\Model\ChatEditMessage200Response
```

Edit message

Update the content of a message (sender only; supports edit history).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$message_id = 'message_id_example'; // string | Message ID.
$chat_edit_message_request = {"content":"Updated message content"}; // \OpenAPI\Client\Model\ChatEditMessageRequest | New message content.

try {
    $result = $apiInstance->chatEditMessage($project_id, $chat_id, $message_id, $chat_edit_message_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatEditMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **message_id** | **string**| Message ID. | |
| **chat_edit_message_request** | [**\OpenAPI\Client\Model\ChatEditMessageRequest**](../Model/ChatEditMessageRequest.md)| New message content. | |

### Return type

[**\OpenAPI\Client\Model\ChatEditMessage200Response**](../Model/ChatEditMessage200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatGet()`

```php
chatGet($project_id, $chat_id): \OpenAPI\Client\Model\ChatGet200Response
```

Get chat details

Returns full chat metadata including participants and roles for a single chat.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.

try {
    $result = $apiInstance->chatGet($project_id, $chat_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |

### Return type

[**\OpenAPI\Client\Model\ChatGet200Response**](../Model/ChatGet200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatGetMessages()`

```php
chatGetMessages($project_id, $chat_id, $page, $limit, $before, $after): \OpenAPI\Client\Model\ChatGetMessages200Response
```

Get chat messages

Returns paginated messages for a chat with optional before/after cursor for time-based pagination.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$page = 1; // int | Page number (1-based).
$limit = 50; // int | Number of messages per page.
$before = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Return messages before this timestamp (cursor).
$after = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Return messages after this timestamp (cursor).

try {
    $result = $apiInstance->chatGetMessages($project_id, $chat_id, $page, $limit, $before, $after);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatGetMessages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of messages per page. | [optional] [default to 50] |
| **before** | **\DateTime**| Return messages before this timestamp (cursor). | [optional] |
| **after** | **\DateTime**| Return messages after this timestamp (cursor). | [optional] |

### Return type

[**\OpenAPI\Client\Model\ChatGetMessages200Response**](../Model/ChatGetMessages200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatList()`

```php
chatList($project_id, $page, $limit): \OpenAPI\Client\Model\ChatList200Response
```

Get user chats

Returns paginated list of chats for the current user in the project, with last message and unread count.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$page = 1; // int | Page number (1-based).
$limit = 20; // int | Number of chats per page.

try {
    $result = $apiInstance->chatList($project_id, $page, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of chats per page. | [optional] [default to 20] |

### Return type

[**\OpenAPI\Client\Model\ChatList200Response**](../Model/ChatList200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatMarkAsRead()`

```php
chatMarkAsRead($project_id, $chat_id, $chat_mark_as_read_request): \OpenAPI\Client\Model\ChatMarkAsRead200Response
```

Mark messages as read

Mark one or more messages as read for the current user in the chat.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$chat_mark_as_read_request = {"messageIds":["65a1b2c3d4e5f6789012345g","65a1b2c3d4e5f6789012345h"]}; // \OpenAPI\Client\Model\ChatMarkAsReadRequest | Array of message IDs to mark as read.

try {
    $result = $apiInstance->chatMarkAsRead($project_id, $chat_id, $chat_mark_as_read_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatMarkAsRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **chat_mark_as_read_request** | [**\OpenAPI\Client\Model\ChatMarkAsReadRequest**](../Model/ChatMarkAsReadRequest.md)| Array of message IDs to mark as read. | |

### Return type

[**\OpenAPI\Client\Model\ChatMarkAsRead200Response**](../Model/ChatMarkAsRead200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatRemoveParticipant()`

```php
chatRemoveParticipant($project_id, $chat_id, $chat_remove_participant_request): \OpenAPI\Client\Model\MessageResponse
```

Remove participant from chat

Remove a user from the chat by userId.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$chat_remove_participant_request = {"userId":"685acbe0e129932fbb7a0fc2"}; // \OpenAPI\Client\Model\ChatRemoveParticipantRequest | User ID of the participant to remove.

try {
    $result = $apiInstance->chatRemoveParticipant($project_id, $chat_id, $chat_remove_participant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatRemoveParticipant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **chat_remove_participant_request** | [**\OpenAPI\Client\Model\ChatRemoveParticipantRequest**](../Model/ChatRemoveParticipantRequest.md)| User ID of the participant to remove. | |

### Return type

[**\OpenAPI\Client\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatRemoveReaction()`

```php
chatRemoveReaction($project_id, $chat_id, $message_id, $chat_add_reaction_request): \OpenAPI\Client\Model\ChatRemoveReaction200Response
```

Remove reaction from message

Remove the current user's emoji reaction from a message.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$message_id = 'message_id_example'; // string | Message ID.
$chat_add_reaction_request = {"emoji":"👍"}; // \OpenAPI\Client\Model\ChatAddReactionRequest | Emoji to remove (must match the reaction added by the user).

try {
    $result = $apiInstance->chatRemoveReaction($project_id, $chat_id, $message_id, $chat_add_reaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatRemoveReaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **message_id** | **string**| Message ID. | |
| **chat_add_reaction_request** | [**\OpenAPI\Client\Model\ChatAddReactionRequest**](../Model/ChatAddReactionRequest.md)| Emoji to remove (must match the reaction added by the user). | |

### Return type

[**\OpenAPI\Client\Model\ChatRemoveReaction200Response**](../Model/ChatRemoveReaction200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `chatSendMessage()`

```php
chatSendMessage($project_id, $chat_id, $chat_send_message_request): \OpenAPI\Client\Model\ChatSendMessage201Response
```

Send message

Send a message (text, image, video, audio, file, location, contact) to a chat with optional replyTo and mentions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$chat_id = 'chat_id_example'; // string | Chat ID.
$chat_send_message_request = {"type":"text","content":"Hello everyone!","replyTo":null,"mentions":[]}; // \OpenAPI\Client\Model\ChatSendMessageRequest | Message type, content, optional replyTo and mentions.

try {
    $result = $apiInstance->chatSendMessage($project_id, $chat_id, $chat_send_message_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->chatSendMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **chat_id** | **string**| Chat ID. | |
| **chat_send_message_request** | [**\OpenAPI\Client\Model\ChatSendMessageRequest**](../Model/ChatSendMessageRequest.md)| Message type, content, optional replyTo and mentions. | |

### Return type

[**\OpenAPI\Client\Model\ChatSendMessage201Response**](../Model/ChatSendMessage201Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
