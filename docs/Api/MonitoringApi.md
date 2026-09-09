# MudbaseSDK\MonitoringApi

Block scanner metrics, logs, analytics, errors, performance, and alerts

All URIs are relative to https://cloud.mudbase.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createMonitoringAlert()**](MonitoringApi.md#createMonitoringAlert) | **POST** /api/monitoring/alerts | Create monitoring alert |
| [**getMonitoringAnalytics()**](MonitoringApi.md#getMonitoringAnalytics) | **GET** /api/monitoring/analytics | Get usage analytics (time series) |
| [**getMonitoringErrors()**](MonitoringApi.md#getMonitoringErrors) | **GET** /api/monitoring/errors | Get error logs |
| [**getMonitoringLatencyInsights()**](MonitoringApi.md#getMonitoringLatencyInsights) | **GET** /api/monitoring/latency-insights | Latency insights (route templates, percentiles, impact scores) |
| [**getMonitoringLogs()**](MonitoringApi.md#getMonitoringLogs) | **GET** /api/monitoring/logs | Get audit logs |
| [**getMonitoringPerformance()**](MonitoringApi.md#getMonitoringPerformance) | **GET** /api/monitoring/performance | Get performance metrics |
| [**getMonitoringQueueMetrics()**](MonitoringApi.md#getMonitoringQueueMetrics) | **GET** /api/monitoring/queue-metrics | Usage metering queue job counts |
| [**listMonitoringAlerts()**](MonitoringApi.md#listMonitoringAlerts) | **GET** /api/monitoring/alerts | List monitoring alerts |


## `createMonitoringAlert()`

```php
createMonitoringAlert($create_monitoring_alert_request)
```

Create monitoring alert

Create a monitoring alert (plan limit alertsPerProject enforced).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_monitoring_alert_request = {"name":"name_example","condition":"condition_example","threshold":0.01,"action":"action_example","projectId":"projectId_example"}; // \MudbaseSDK\Model\CreateMonitoringAlertRequest

try {
    $apiInstance->createMonitoringAlert($create_monitoring_alert_request);
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->createMonitoringAlert: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_monitoring_alert_request** | [**\MudbaseSDK\Model\CreateMonitoringAlertRequest**](../Model/CreateMonitoringAlertRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringAnalytics()`

```php
getMonitoringAnalytics($project_id, $period, $granularity, $days): \MudbaseSDK\Model\MonitoringAnalyticsResponse
```

Get usage analytics (time series)

Aggregates UsageStat by day/week/month. Optional **projectId** scopes to one project. Query **days** (1–90) for a rolling window (e.g. **days=14**); when set, overrides **period**.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$period = 'month'; // string
$granularity = 'day'; // string
$days = 56; // int | Rolling window in days (1–90); when set, period becomes last_N_days

try {
    $result = $apiInstance->getMonitoringAnalytics($project_id, $period, $granularity, $days);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringAnalytics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | [optional] |
| **period** | **string**|  | [optional] [default to &#39;month&#39;] |
| **granularity** | **string**|  | [optional] [default to &#39;day&#39;] |
| **days** | **int**| Rolling window in days (1–90); when set, period becomes last_N_days | [optional] |

### Return type

[**\MudbaseSDK\Model\MonitoringAnalyticsResponse**](../Model/MonitoringAnalyticsResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringErrors()`

```php
getMonitoringErrors()
```

Get error logs

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->getMonitoringErrors();
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringErrors: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringLatencyInsights()`

```php
getMonitoringLatencyInsights()
```

Latency insights (route templates, percentiles, impact scores)

Per-process snapshot: normalized **routeKey** (METHOD + path template), **p50/p95/p99**, 4xx/5xx counts, **impactScore**, **alertsSuggested**, **rps**, **inFlight**, **eventLoopLagP99Ms**. One buffer per server instance.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->getMonitoringLatencyInsights();
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringLatencyInsights: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringLogs()`

```php
getMonitoringLogs($page, $limit, $project_id, $user_id, $level, $start_date, $end_date, $action, $resource): \MudbaseSDK\Model\MonitoringLogsResponse
```

Get audit logs

Paginated audit trail for the org. Use **projectId** to scope to one project; **level=all** or **audit** for full activity feed. Each entry includes **activityTitle** and **activityDetail** for dashboard copy. Requires monitoring read permission.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 1; // int
$limit = 20; // int
$project_id = 'project_id_example'; // string | Filter to this project (must belong to org)
$user_id = 'user_id_example'; // string | Filter to this user's audit entries
$level = 'error'; // string | error|security|all|audit|low|medium|high|critical
$start_date = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$end_date = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$action = 'action_example'; // string
$resource = 'resource_example'; // string

try {
    $result = $apiInstance->getMonitoringLogs($page, $limit, $project_id, $user_id, $level, $start_date, $end_date, $action, $resource);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringLogs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page** | **int**|  | [optional] [default to 1] |
| **limit** | **int**|  | [optional] [default to 20] |
| **project_id** | **string**| Filter to this project (must belong to org) | [optional] |
| **user_id** | **string**| Filter to this user&#39;s audit entries | [optional] |
| **level** | **string**| error|security|all|audit|low|medium|high|critical | [optional] [default to &#39;error&#39;] |
| **start_date** | **\DateTime**|  | [optional] |
| **end_date** | **\DateTime**|  | [optional] |
| **action** | **string**|  | [optional] |
| **resource** | **string**|  | [optional] |

### Return type

[**\MudbaseSDK\Model\MonitoringLogsResponse**](../Model/MonitoringLogsResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringPerformance()`

```php
getMonitoringPerformance($project_id, $period): \MudbaseSDK\Model\MonitoringPerformanceResponse
```

Get performance metrics

Response time stats from AuditLog where available. With **projectId**, falls back to UsageStat latency averages when audit data is sparse (**latencySource** may be **usage_stat**).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$project_id = 'project_id_example'; // string
$period = 'hour'; // string

try {
    $result = $apiInstance->getMonitoringPerformance($project_id, $period);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringPerformance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **project_id** | **string**|  | [optional] |
| **period** | **string**|  | [optional] [default to &#39;hour&#39;] |

### Return type

[**\MudbaseSDK\Model\MonitoringPerformanceResponse**](../Model/MonitoringPerformanceResponse.md)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMonitoringQueueMetrics()`

```php
getMonitoringQueueMetrics()
```

Usage metering queue job counts

BullMQ **usage-events** queue counts when `USE_METERING_QUEUE` and `REDIS_URL` are set.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->getMonitoringQueueMetrics();
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->getMonitoringQueueMetrics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMonitoringAlerts()`

```php
listMonitoringAlerts()
```

List monitoring alerts

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (JWT) authorization: OrgBearerAuth
$config = MudbaseSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new MudbaseSDK\Api\MonitoringApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->listMonitoringAlerts();
} catch (Exception $e) {
    echo 'Exception when calling MonitoringApi->listMonitoringAlerts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../../README.md#OrgBearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
