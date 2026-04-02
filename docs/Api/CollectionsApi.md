# OpenAPI\Client\CollectionsApi

Database schema and collection management

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**collectionsCreate()**](CollectionsApi.md#collectionsCreate) | **POST** /api/schemas/projects/{projectId}/collections | Create new collection |
| [**collectionsDelete()**](CollectionsApi.md#collectionsDelete) | **DELETE** /api/schemas/projects/{projectId}/collections/{collectionId} | Delete collection |
| [**collectionsGet()**](CollectionsApi.md#collectionsGet) | **GET** /api/schemas/projects/{projectId}/collections/{collectionId} | Get single collection |
| [**collectionsList()**](CollectionsApi.md#collectionsList) | **GET** /api/schemas/projects/{projectId}/collections | List collections in project |
| [**collectionsUpdate()**](CollectionsApi.md#collectionsUpdate) | **PATCH** /api/schemas/projects/{projectId}/collections/{collectionId} | Update collection |


## `collectionsCreate()`

```php
collectionsCreate($project_id, $create_collection_request): \OpenAPI\Client\Model\CollectionsCreate201Response
```

Create new collection

Create a new collection in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\CollectionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$create_collection_request = {"name":"products","fields":[{"name":"title","type":"string","required":true},{"name":"price","type":"number","required":true},{"name":"description","type":"string"}]}; // \OpenAPI\Client\Model\CreateCollectionRequest | Collection name, optional slug, fields, permissions, and settings.

try {
    $result = $apiInstance->collectionsCreate($project_id, $create_collection_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CollectionsApi->collectionsCreate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **create_collection_request** | [**\OpenAPI\Client\Model\CreateCollectionRequest**](../Model/CreateCollectionRequest.md)| Collection name, optional slug, fields, permissions, and settings. | |

### Return type

[**\OpenAPI\Client\Model\CollectionsCreate201Response**](../Model/CollectionsCreate201Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `collectionsDelete()`

```php
collectionsDelete($project_id, $collection_id): \OpenAPI\Client\Model\MessageResponse
```

Delete collection

Delete a collection permanently. This is a destructive operation. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\CollectionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.

try {
    $result = $apiInstance->collectionsDelete($project_id, $collection_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CollectionsApi->collectionsDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |

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

## `collectionsGet()`

```php
collectionsGet($project_id, $collection_id): \OpenAPI\Client\Model\Collection
```

Get single collection

Get collection details by ID. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\CollectionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.

try {
    $result = $apiInstance->collectionsGet($project_id, $collection_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CollectionsApi->collectionsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |

### Return type

[**\OpenAPI\Client\Model\Collection**](../Model/Collection.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `collectionsList()`

```php
collectionsList($project_id): \OpenAPI\Client\Model\CollectionsList200Response
```

List collections in project

List all collections in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\CollectionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.

try {
    $result = $apiInstance->collectionsList($project_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CollectionsApi->collectionsList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |

### Return type

[**\OpenAPI\Client\Model\CollectionsList200Response**](../Model/CollectionsList200Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `collectionsUpdate()`

```php
collectionsUpdate($project_id, $collection_id, $update_collection_request): \OpenAPI\Client\Model\CollectionsCreate201Response
```

Update collection

Update collection configuration (name, fields, permissions). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\CollectionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$update_collection_request = {"name":"products_updated","fields":[{"name":"title","type":"string","required":true},{"name":"price","type":"number","required":true}]}; // \OpenAPI\Client\Model\UpdateCollectionRequest | Fields to update (name, fields, permissions, settings).

try {
    $result = $apiInstance->collectionsUpdate($project_id, $collection_id, $update_collection_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CollectionsApi->collectionsUpdate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **update_collection_request** | [**\OpenAPI\Client\Model\UpdateCollectionRequest**](../Model/UpdateCollectionRequest.md)| Fields to update (name, fields, permissions, settings). | |

### Return type

[**\OpenAPI\Client\Model\CollectionsCreate201Response**](../Model/CollectionsCreate201Response.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
