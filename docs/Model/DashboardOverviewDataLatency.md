# # DashboardOverviewDataLatency

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**scope** | **string** |  | [optional]
**avg_ms_today** | **int** |  | [optional]
**avg_ms7d** | **int** |  | [optional]
**latency_samples_today** | **int** | Count of openapi-docs–scoped latency samples for this project (UTC today) | [optional]
**latency_needs_traffic** | **bool** |  | [optional]
**interpretation** | **string** | Why mean can differ from typical latency; points to latency-insights | [optional]
**instance_rollup** | [**\OpenAPI\Client\Model\DashboardOverviewDataLatencyInstanceRollup**](DashboardOverviewDataLatencyInstanceRollup.md) |  | [optional]
**top_routes_by_impact_hint** | [**\OpenAPI\Client\Model\DashboardOverviewDataLatencyTopRoutesByImpactHintInner[]**](DashboardOverviewDataLatencyTopRoutesByImpactHintInner.md) | Top route templates by impact score on this instance (debugging hint) | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
