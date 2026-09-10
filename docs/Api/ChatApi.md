# MudbaseSDK\ChatApi

Real-time chat and messaging

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addParticipant()**](ChatApi.md#addParticipant) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/participants | Add participant to chat |
| [**addReaction()**](ChatApi.md#addReaction) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Add reaction to message |
| [**createChat()**](ChatApi.md#createChat) | **POST** /api/chat/projects/{projectId}/chats | Create new chat |
| [**deleteMessage()**](ChatApi.md#deleteMessage) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Delete message |
| [**editMessage()**](ChatApi.md#editMessage) | **PATCH** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Edit message |
| [**getChatDetails()**](ChatApi.md#getChatDetails) | **GET** /api/chat/projects/{projectId}/chats/{chatId} | Get chat details |
| [**getChatE2eeParticipantKeys()**](ChatApi.md#getChatE2eeParticipantKeys) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/e2ee/participant-keys | List participant E2EE public keys |
| [**getChatMessages()**](ChatApi.md#getChatMessages) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/messages | Get chat messages |
| [**getUserChats()**](ChatApi.md#getUserChats) | **GET** /api/chat/projects/{projectId}/chats | Get user chats |
| [**markMessagesAsRead()**](ChatApi.md#markMessagesAsRead) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/read | Mark messages as read |
| [**putChatE2eeKey()**](ChatApi.md#putChatE2eeKey) | **PUT** /api/chat/projects/{projectId}/me/chat-e2ee-key | Register chat E2EE identity public key |
| [**removeParticipant()**](ChatApi.md#removeParticipant) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/participants | Remove participant from chat |
| [**removeReaction()**](ChatApi.md#removeReaction) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Remove reaction from message |
| [**sendMessage()**](ChatApi.md#sendMessage) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages | Send message |


## `addParticipant()`

```php
addParticipant($project_id, $chat_id, $add_participant_request): \MudbaseSDK\Model\AddParticipant200Response
```

Add participant to chat

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$add_participant_request = {"userId":"685acbe0e129932fbb7a0fc2","role":"member"}; // \MudbaseSDK\Model\AddParticipantRequest

try {
    $result = $apiInstance->addParticipant($project_id, $chat_id, $add_participant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->addParticipant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **add_participant_request** | [**\MudbaseSDK\Model\AddParticipantRequest**](../Model/AddParticipantRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AddParticipant200Response**](../Model/AddParticipant200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `addReaction()`

```php
addReaction($project_id, $chat_id, $message_id, $add_reaction_request): \MudbaseSDK\Model\AddReaction200Response
```

Add reaction to message

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$message_id = 'message_id_example'; // string
$add_reaction_request = {"emoji":"👍"}; // \MudbaseSDK\Model\AddReactionRequest

try {
    $result = $apiInstance->addReaction($project_id, $chat_id, $message_id, $add_reaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->addReaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **message_id** | **string**|  | |
| **add_reaction_request** | [**\MudbaseSDK\Model\AddReactionRequest**](../Model/AddReactionRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\AddReaction200Response**](../Model/AddReaction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createChat()`

```php
createChat($project_id, $create_chat_request): \MudbaseSDK\Model\CreateChat201Response
```

Create new chat

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$create_chat_request = {"name":"Team Chat","description":"Main team communication","type":"group","participants":["685acbe0e129932fbb7a0fc2","685acbe0e129932fbb7a0fc3"],"settings":{}}; // \MudbaseSDK\Model\CreateChatRequest

try {
    $result = $apiInstance->createChat($project_id, $create_chat_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->createChat: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **create_chat_request** | [**\MudbaseSDK\Model\CreateChatRequest**](../Model/CreateChatRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\CreateChat201Response**](../Model/CreateChat201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteMessage()`

```php
deleteMessage($project_id, $chat_id, $message_id): \MudbaseSDK\Model\MessageResponse
```

Delete message

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$message_id = 'message_id_example'; // string

try {
    $result = $apiInstance->deleteMessage($project_id, $chat_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->deleteMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **message_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `editMessage()`

```php
editMessage($project_id, $chat_id, $message_id, $edit_message_request): \MudbaseSDK\Model\EditMessage200Response
```

Edit message

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$message_id = 'message_id_example'; // string
$edit_message_request = {"content":"Updated message content"}; // \MudbaseSDK\Model\EditMessageRequest

try {
    $result = $apiInstance->editMessage($project_id, $chat_id, $message_id, $edit_message_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->editMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **message_id** | **string**|  | |
| **edit_message_request** | [**\MudbaseSDK\Model\EditMessageRequest**](../Model/EditMessageRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\EditMessage200Response**](../Model/EditMessage200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getChatDetails()`

```php
getChatDetails($project_id, $chat_id): \MudbaseSDK\Model\GetChatDetails200Response
```

Get chat details

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string

try {
    $result = $apiInstance->getChatDetails($project_id, $chat_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->getChatDetails: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetChatDetails200Response**](../Model/GetChatDetails200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getChatE2eeParticipantKeys()`

```php
getChatE2eeParticipantKeys($project_id, $chat_id): \MudbaseSDK\Model\GetChatE2eeParticipantKeys200Response
```

List participant E2EE public keys

Returns registered identity public keys for users in this chat (for client-side key distribution).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string

try {
    $result = $apiInstance->getChatE2eeParticipantKeys($project_id, $chat_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->getChatE2eeParticipantKeys: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |

### Return type

[**\MudbaseSDK\Model\GetChatE2eeParticipantKeys200Response**](../Model/GetChatE2eeParticipantKeys200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getChatMessages()`

```php
getChatMessages($project_id, $chat_id, $page, $limit, $before, $after): \MudbaseSDK\Model\GetChatMessages200Response
```

Get chat messages

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$page = 1; // int
$limit = 50; // int
$before = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$after = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime

try {
    $result = $apiInstance->getChatMessages($project_id, $chat_id, $page, $limit, $before, $after);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->getChatMessages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 50] |
| **before** | **\DateTime**|  | [optional] |
| **after** | **\DateTime**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\GetChatMessages200Response**](../Model/GetChatMessages200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getUserChats()`

```php
getUserChats($project_id, $page, $limit): \MudbaseSDK\Model\GetUserChats200Response
```

Get user chats

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$page = 1; // int
$limit = 20; // int

try {
    $result = $apiInstance->getUserChats($project_id, $page, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->getUserChats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |

### Return type

[**\MudbaseSDK\Model\GetUserChats200Response**](../Model/GetUserChats200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `markMessagesAsRead()`

```php
markMessagesAsRead($project_id, $chat_id, $mark_messages_as_read_request): \MudbaseSDK\Model\MarkMessagesAsRead200Response
```

Mark messages as read

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$mark_messages_as_read_request = {"messageIds":["65a1b2c3d4e5f6789012345g","65a1b2c3d4e5f6789012345h"]}; // \MudbaseSDK\Model\MarkMessagesAsReadRequest

try {
    $result = $apiInstance->markMessagesAsRead($project_id, $chat_id, $mark_messages_as_read_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->markMessagesAsRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **mark_messages_as_read_request** | [**\MudbaseSDK\Model\MarkMessagesAsReadRequest**](../Model/MarkMessagesAsReadRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MarkMessagesAsRead200Response**](../Model/MarkMessagesAsRead200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `putChatE2eeKey()`

```php
putChatE2eeKey($project_id, $put_chat_e2ee_key_request): \MudbaseSDK\Model\PutChatE2eeKey200Response
```

Register chat E2EE identity public key

Stores your long-term public key for end-to-end encrypted chat (key agreement). Private keys never leave the client. Required for other participants to encrypt to you.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$put_chat_e2ee_key_request = {"identityPublicKey":"identityPublicKey_example"}; // \MudbaseSDK\Model\PutChatE2eeKeyRequest

try {
    $result = $apiInstance->putChatE2eeKey($project_id, $put_chat_e2ee_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->putChatE2eeKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **put_chat_e2ee_key_request** | [**\MudbaseSDK\Model\PutChatE2eeKeyRequest**](../Model/PutChatE2eeKeyRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\PutChatE2eeKey200Response**](../Model/PutChatE2eeKey200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeParticipant()`

```php
removeParticipant($project_id, $chat_id, $remove_participant_request): \MudbaseSDK\Model\MessageResponse
```

Remove participant from chat

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$remove_participant_request = {"userId":"685acbe0e129932fbb7a0fc2"}; // \MudbaseSDK\Model\RemoveParticipantRequest

try {
    $result = $apiInstance->removeParticipant($project_id, $chat_id, $remove_participant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->removeParticipant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **remove_participant_request** | [**\MudbaseSDK\Model\RemoveParticipantRequest**](../Model/RemoveParticipantRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\MessageResponse**](../Model/MessageResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeReaction()`

```php
removeReaction($project_id, $chat_id, $message_id, $add_reaction_request): \MudbaseSDK\Model\RemoveReaction200Response
```

Remove reaction from message

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$message_id = 'message_id_example'; // string
$add_reaction_request = {"emoji":"👍"}; // \MudbaseSDK\Model\AddReactionRequest

try {
    $result = $apiInstance->removeReaction($project_id, $chat_id, $message_id, $add_reaction_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->removeReaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **message_id** | **string**|  | |
| **add_reaction_request** | [**\MudbaseSDK\Model\AddReactionRequest**](../Model/AddReactionRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\RemoveReaction200Response**](../Model/RemoveReaction200Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendMessage()`

```php
sendMessage($project_id, $chat_id, $send_message_request): \MudbaseSDK\Model\SendMessage201Response
```

Send message

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

// Configure Bearer (JWT) authorization: ProjectBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\ChatApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$chat_id = 'chat_id_example'; // string
$send_message_request = {"type":"text","content":"Hello everyone!","replyTo":null,"mentions":[]}; // \MudbaseSDK\Model\SendMessageRequest

try {
    $result = $apiInstance->sendMessage($project_id, $chat_id, $send_message_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChatApi->sendMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | |
| **chat_id** | **string**|  | |
| **send_message_request** | [**\MudbaseSDK\Model\SendMessageRequest**](../Model/SendMessageRequest.md)|  | |

### Return type

[**\MudbaseSDK\Model\SendMessage201Response**](../Model/SendMessage201Response.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth), [ProjectBearerAuth](../../README.md#ProjectBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
