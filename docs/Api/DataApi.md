# OpenAPI\Client\DataApi

CRUD operations on collection data

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**dataCreate()**](DataApi.md#dataCreate) | **POST** /api/data/projects/{projectId}/collections/{collectionId}/data | Create data in collection |
| [**dataDelete()**](DataApi.md#dataDelete) | **DELETE** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Delete document |
| [**dataGet()**](DataApi.md#dataGet) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Get single document |
| [**dataList()**](DataApi.md#dataList) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data | List data in collection |
| [**dataUpdate()**](DataApi.md#dataUpdate) | **PATCH** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Update document |


## `dataCreate()`

```php
dataCreate($project_id, $collection_id, $body): \OpenAPI\Client\Model\DataResponse
```

Create data in collection

Create a new document in a collection. Request body must match the collection schema. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\DataApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$body = {"email":"john.doe@example.com","firstName":"John","lastName":"Doe","role":"developer","status":"active"}; // object | Document fields matching the collection schema.

try {
    $result = $apiInstance->dataCreate($project_id, $collection_id, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DataApi->dataCreate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **body** | **object**| Document fields matching the collection schema. | |

### Return type

[**\OpenAPI\Client\Model\DataResponse**](../Model/DataResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `dataDelete()`

```php
dataDelete($project_id, $collection_id, $document_id): \OpenAPI\Client\Model\MessageResponse
```

Delete document

Delete a document from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\DataApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$document_id = 'document_id_example'; // string | Document ID.

try {
    $result = $apiInstance->dataDelete($project_id, $collection_id, $document_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DataApi->dataDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **document_id** | **string**| Document ID. | |

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

## `dataGet()`

```php
dataGet($project_id, $collection_id, $document_id): \OpenAPI\Client\Model\DataResponse
```

Get single document

Get a document by ID from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\DataApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$document_id = 'document_id_example'; // string | Document ID.

try {
    $result = $apiInstance->dataGet($project_id, $collection_id, $document_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DataApi->dataGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **document_id** | **string**| Document ID. | |

### Return type

[**\OpenAPI\Client\Model\DataResponse**](../Model/DataResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `dataList()`

```php
dataList($project_id, $collection_id, $page, $limit, $sort, $filter): \OpenAPI\Client\Model\DataListResponse
```

List data in collection

List all documents in a collection with optional pagination, sort, and filter. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\DataApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$page = 1; // int | Page number (1-based).
$limit = 20; // int | Number of documents per page.
$sort = '-createdAt'; // string | Sort field and order (e.g. -createdAt, name).
$filter = 'filter_example'; // string | JSON string for filtering documents (e.g. {\"status\":\"active\"}).

try {
    $result = $apiInstance->dataList($project_id, $collection_id, $page, $limit, $sort, $filter);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DataApi->dataList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **page** | **int**| Page number (1-based). | [optional] [default to 1] |
| **limit** | **int**| Number of documents per page. | [optional] [default to 20] |
| **sort** | **string**| Sort field and order (e.g. -createdAt, name). | [optional] [default to &#39;-createdAt&#39;] |
| **filter** | **string**| JSON string for filtering documents (e.g. {\&quot;status\&quot;:\&quot;active\&quot;}). | [optional] |

### Return type

[**\OpenAPI\Client\Model\DataListResponse**](../Model/DataListResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `dataUpdate()`

```php
dataUpdate($project_id, $collection_id, $document_id, $body): \OpenAPI\Client\Model\DataResponse
```

Update document

Update a document in a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: BearerToken
$config = OpenAPI\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\Client\Api\DataApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string | Project ID.
$collection_id = 'collection_id_example'; // string | Collection ID.
$document_id = 'document_id_example'; // string | Document ID.
$body = {"firstName":"Sarah","lastName":"Chen","email":"sarah.chen@example.com","role":"admin","status":"active"}; // object | Partial document fields to update.

try {
    $result = $apiInstance->dataUpdate($project_id, $collection_id, $document_id, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DataApi->dataUpdate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**| Project ID. | |
| **collection_id** | **string**| Collection ID. | |
| **document_id** | **string**| Document ID. | |
| **body** | **object**| Partial document fields to update. | |

### Return type

[**\OpenAPI\Client\Model\DataResponse**](../Model/DataResponse.md)

### Authorization

[BearerToken](../../README.md#BearerToken)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
