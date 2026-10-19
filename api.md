# CodeJackRabbit Rust API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImZlMGYyMjU1OGZiNDM0MTEwODJkZjVlMDc2MmEyM2U5ZWFmOTBhOWM3MTNmZTRlZTljZmQyNzM3OTIyMjgwM2QiLCJvcGVyYXRpb25fY291bnQiOjIyLCJyZW5kZXJlciI6InJ1c3QiLCJ2ZXJzaW9uIjoiMS40LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `fe0f22558fb43411082df5e0762a23e9eaf90a9c713fe4ee9cfd27379222803d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`ClientBuilder::hooks(RequestHooks::new()...)` registers four callbacks. Every attempt starts with `before_request` and ends with exactly one of `on_retry` (another attempt follows), `after_response` (the success the call returns) or `on_error` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every hook borrows an immutable `HookContext`: no hook can change the request.

`ClientBuilder::tracer(...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ComplianceGateRequest`
- `FileChange`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJhbmFseXplX2NvbnRyYWN0X2RyaWZ0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVDb250cmFjdERyaWZ0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9jb250cmFjdC1kcmlmdCIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImIzODNhMjY0ZmU1MzA5ZTlkMzdlODEzMTI4ZmY5MDY5NWQ2MWExN2FiMmIzM2Q3NmRlNTkzYTRmMTM2ZDFkMDAiLCJzaWduYXR1cmVfc2hhMjU2IjoiNDNiMGFjNmNjMzNlMDkzMjk1YTU3MDJjZmM3YzA4MzRhMDkyMzJlOWI0Y2IzNTA4Y2Y0MWIzYTU3NTZkNTQ4OSJ9 -->
### `client.analyze_contract_drift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

#### Signature

```rust
pub async fn analyze_contract_drift(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJhbmFseXplX3BlcmZfZmluX29wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiJjYmU5OTI3MTRjOTZmZTkwNGMwYjg3YjUwZWM5ZjgxYjNjYjRjZDZiZTVjMmMzY2JmNjZhZTE4Y2Q1NzBmMDgzIiwic2lnbmF0dXJlX3NoYTI1NiI6ImQxOGMyNWI4ODE2YTQ2NjczNTQ0YTM4MzQyOGU2YzhjMDQ3MWIyNzljZTk5YzAwNTk4MjkwYThhYjdlOTZiZGEifQ -->
### `client.analyze_perf_fin_ops`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

#### Signature

```rust
pub async fn analyze_perf_fin_ops(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJwbGFuX3N0YWNrZWRfcHJfc3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjljNjBhZTc1MDA3Y2JlMzYwYWQ1NmQxNmY5OTg5ZWEwMGYyZDMzOGY0MjMxNDE3YjI3N2ViNjQyOTE3YjkwODIiLCJzaWduYXR1cmVfc2hhMjU2IjoiOTI5MjI5ZmZiNzUwMzE4NThjNGNiOWYxMmE1NDk0MzI4ZjI0Y2Q2YWEzZmEwZGRlNzhkZDE4NTM3NDllMDY2ZSJ9 -->
### `client.plan_stacked_pr_split`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

#### Signature

```rust
pub async fn plan_stacked_pr_split(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfYW5hbHl0aWNzX3JvaSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFuYWx5dGljc1JvaSIsInBhdGgiOiIvdjEvYW5hbHl0aWNzL3JvaSIsInJlc291cmNlIjoiYW5hbHl0aWNzIiwic2VjdGlvbl9zaGEyNTYiOiI3YmFmNDRlMzZjN2IxZjIzMzdjMDIwNmM4OTljNzI0OTg0ZWEyZmE5NTYyYjgxMGNhNTFkNzlmYTk5MTBhOTg4Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjQyYWVkYjRkODAwZDQ0MGQyMDM3NGE4ZTZmMDg2NWZiZTk1Y2ZjOTg2NjU5ZjBhZmEyYzIyMGJkNTgyMWI5ZjMifQ -->
### `client.get_analytics_roi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

#### Signature

```rust
pub async fn get_analytics_roi(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfY2FwYWJpbGl0aWVzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiZGQ4MDNkYjExOThjMjQ3ODczMDA5Yzk5N2NkZjU2MGViZGFlYTcxNWZiOWM0ZmFmMjE4N2ZlYTEwYmExMWJhZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI4MWNhNTgwZmY2YjUyNjFkOGY4NDk3MzQwNWViMGY5ODJlMzNkN2FiYTJhZjQwZmJjNmRhNjEyYzg5NDdhZTYxIn0 -->
### `client.get_capabilities`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

#### Signature

```rust
pub async fn get_capabilities(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJldmFsdWF0ZV9jb21wbGlhbmNlX2dhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI2NGU4YjkxZmFhZTMyZWE5ZDVjZTQ2ZjA3YzM4YzBmM2EyZmY0NzQxZmU4YWNhNWU2MzRjYjU3ZDU1MTY4ZTQxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjUxYTY3ZjUwNGE1YmZjMTY3ODI5MjYyMDk0NjRhZGVkYzRjNWQwYTY0NTA0ZThhZDA4YTVlZGE1MjU2MGFjOGEifQ -->
### `client.evaluate_compliance_gate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

#### Signature

```rust
pub async fn evaluate_compliance_gate(&self, body: ComplianceGateRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJleHBvcnRfc2FyaWYiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXhwb3J0U2FyaWYiLCJwYXRoIjoiL3YxL2NvbXBsaWFuY2Uvc2FyaWYiLCJyZXNvdXJjZSI6ImNvbXBsaWFuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjA1MjY0MDk4NjYxMzFjMmIyZTdmYmEwY2FhYzlhZmViNTNiMDA3OGVlOTNjNzAyYjg4M2YyYzA4MDQ1YzhiMDIiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGYzNmFkY2VmMTY3OTU0YjdhZTZlYTg1NmNmNDI0NmQyZGQ4OTY3YTliYzE4MWUyYzIwYmM3MDE1NThkY2EwNyJ9 -->
### `client.export_sarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

#### Signature

```rust
pub async fn export_sarif(&self, body: std::collections::BTreeMap<String, serde_json::Value>, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfaGVhbHRoIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiZmVlNDVmZjZkMzRiODMxNWRlOGU4ZGZmZjNmNzY1MWJkZTIyNTllOGMzY2E4ZDU2YTlkZDYzNzk5ZmI1OWVjZCIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MzlmZDczZWNkYzczYWRkM2ZhNDRiNTI0OGY0ZjIzNzU4NGZkZmVjNzg0ZjgxNjYzMzJjZTcyOWUxNjZiMDJlIn0 -->
### `client.get_health`

Operation ID: `getHealth`  
Route: `GET` `/health`  

#### Signature

```rust
pub async fn get_health(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJidWlsZF9hdXRvZml4X2J1bmRsZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiZTRjMzY5YWI4ZTUxNGY1ZjMxN2M4MTY5NmZkYzBjMjY5N2MwMmVkM2FjYzkwNTk4ZWFiNzk5M2UzYjQ2ZDczNSIsInNpZ25hdHVyZV9zaGEyNTYiOiIwODA3NjY1YTYzNzdiNWNkMWJjYjA1OGExYWI0OWUwMmQ2NmMyYzdkOTEyMzkwZGQ2ZmY5NjViN2IyYTcyNTM3In0 -->
### `client.build_autofix_bundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

#### Signature

```rust
pub async fn build_autofix_bundle(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJjb21wdXRlX3Jpc2tfcmFkYXIiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiIwY2UzYmM0NGYxMGVjY2I4ZGY3NWMwNGI5OThiNjk3ZTEyMzI3OTZiOGY2NzYwOGNjYmNkMTVjNzJlMjZkMzNmIiwic2lnbmF0dXJlX3NoYTI1NiI6IjYxZDM1OTlmN2U3ZGUxNDVlNmExMDY0ZGRiYTM4ZmJmMDhiNGRlMGIxZGNiNmFmMTdmYWZhZDQ0Njc2MGJlZWYifQ -->
### `client.compute_risk_radar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

#### Signature

```rust
pub async fn compute_risk_radar(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJjcmVhdGVfcmV2aWV3IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZVJldmlldyIsInBhdGgiOiIvdjEvcmV2aWV3cyIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiZWZlMWM2YjYyNzgyM2Y2ZGViOThiNmY1YjhkZTJhOGMwOWViYzdiMTQ2NGE3ZDEyMjhjMjBkNWI3MmFlY2JjNyIsInNpZ25hdHVyZV9zaGEyNTYiOiIzYTM1NDdhYjlhYTUzZjdhZjdmYzQ0MzU5NjUwNjk5MzcyYTQyMjgxMTljZDNiMDgxYTg4ZjU1Y2Y1OWZiYmU2In0 -->
### `client.create_review`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

#### Signature

```rust
pub async fn create_review(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJmaW5hbGl6ZV9tZXRlcmluZ19xdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjI4YWNmYWMzODdlNjhkNzI5OGMzYjNmNzU1NjVhNjM3MWQ2NjU1MGU1MGViODU2Yzc0YzI5OTZjN2IwMzdlY2EiLCJzaWduYXR1cmVfc2hhMjU2IjoiNDJjMGI1NGMxNTRhNGMyNTFkMmJiZDM1NDExODRjMTQ0MzBjYzI0M2FlNTY4MDQ2Y2ZlYWZlY2NjYmQ1OTkyYSJ9 -->
### `client.finalize_metering_quota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

#### Signature

```rust
pub async fn finalize_metering_quota(&self, body: std::collections::BTreeMap<String, serde_json::Value>, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfc2Fhc19ibHVlcHJpbnQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiMjAyZGZkZTVmOTIxMTY0MTFmNmQ1Y2I5YWM0MzY3ODVhNGYzNzg4MzQ3NmIwMjdjYTYwYWY3ZDA1MzA4OWIxOSIsInNpZ25hdHVyZV9zaGEyNTYiOiI0MzEyYzRiYzI3NWJiNGM5OGZlNmZiN2E4YzY1YWJiYjZjOTlhYjkzNTdlN2U0NzFiOTdmMWFmY2YwYzQzODI0In0 -->
### `client.get_saas_blueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

#### Signature

```rust
pub async fn get_saas_blueprint(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJpc3N1ZV9zdXJmYWNlX2xlYXNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjNkNTQ0MWZkY2EzY2IxZDdmMWFiZGIyYjA0NTg5YjUxN2JiOTYzYmM1MTQwNWE0MDE1NTg1YjAzYzY0NWM4MjgiLCJzaWduYXR1cmVfc2hhMjU2IjoiYTM5ZDg2ODkyM2FjNGU3MmY2MzJlN2NjMjQzNzJhY2M2ZTc5NWU0MjU4YWQ2ZGZiNDUxMmYzZTMxZGViMzc4OCJ9 -->
### `client.issue_surface_lease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

#### Signature

```rust
pub async fn issue_surface_lease(&self, body: std::collections::BTreeMap<String, serde_json::Value>, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJyZXNlcnZlX21ldGVyaW5nX3F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjUwMGIxNTI5ZDI5OGFiZjA2NjMwZTYwMjFmZDI2ZTUxZTM5MTAwZmQyNDFlNjUxZmRkNTYzMTQ5MTY3NWNiZTUiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmFiZjhmMTgwZDRhMTUxZDRkNDA0ZDUyMTczNmZlYTY0MjgwMDRiZWI1NGIxNDBkZDQzZmQ3MWMyNDhiOWFhMyJ9 -->
### `client.reserve_metering_quota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

#### Signature

```rust
pub async fn reserve_metering_quota(&self, body: std::collections::BTreeMap<String, serde_json::Value>, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZW5lcmF0ZV9zYm9tIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiNDc4ZTkyZDE1YjIwYzJlOWJlOTJmNTgwOTY2YTVmZTg4NGQzNGU4MzI1MGZhMDQwNmI4NzRlODI2N2I5ZmM5MyIsInNpZ25hdHVyZV9zaGEyNTYiOiJlMTY1ZjZiZWQ2YTYzMjQ0ZWJmNjQzY2IxMzg4ZDU1NGZkYzgwNjJmYWU3ZTRjYmE0MGZmMjBjOGU4OWRmMzcwIn0 -->
### `client.generate_sbom`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

#### Signature

```rust
pub async fn generate_sbom(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supply_chain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJhbmFseXplX3N1cHBseV9jaGFpbiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4iLCJwYXRoIjoiL3YxL3N1cHBseS1jaGFpbi9hbmFseXplIiwicmVzb3VyY2UiOiJzdXBwbHlfY2hhaW4iLCJzZWN0aW9uX3NoYTI1NiI6IjgxY2VjYjk3MmU0YWExOTNhMjgwZGJhMjdmZmNlZWRjZjFlMDk0YjZhNGJkMmUwYTI2YzVjNjM5N2Q4ODYxNWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGNmOWQ3N2Y1YmVlYTRiNjI0Nzc5YjQ0YzgwZDNiZTZmNTU5M2ZiNjkyZTJiZDZkNWVhZjA2YjdlMzlhMmM5ZCJ9 -->
### `client.analyze_supply_chain`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

#### Signature

```rust
pub async fn analyze_supply_chain(&self, body: ReviewRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJjcmVhdGVfY29kaW5nX3Rhc2siLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiI4MDg0MDNlYThjMDlkYjJkOTJiMmFkZDIxM2FmMGM0YjA5NGYwMjRhMmZmNmZkNDY1YzZhZDRiMjVmYzczMjVhIiwic2lnbmF0dXJlX3NoYTI1NiI6Ijc5YWY5M2E2NWU3ZTZmYmRmMjA3ODUyNjczMmUzN2Q0ZjZkNTRjNDZlNDM3NDNkMTRlMGRiZmUzNGVhY2E1ZmMifQ -->
### `client.create_coding_task`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

#### Signature

```rust
pub async fn create_coding_task(&self, body: std::collections::BTreeMap<String, serde_json::Value>, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X2NvZGluZ190YXNrcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RDb2RpbmdUYXNrcyIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiJjMDkxNzc2YTgwYTAwM2E3YzNhZTUzODViZmE3MzY2ZjhlNjNlMWFiNTlhOWM1NDQzNjQ2Y2UwNjA3YTYxNmQyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjI1OWNkNGJlOTg3MDkxZjExMTQ2NGFlYWFkNjhjY2I0MmMyYTgyZDViOGIwZjg1NThhYmJkZmU4MmNiMWIxZjQifQ -->
### `client.list_coding_tasks`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

#### Signature

```rust
pub async fn list_coding_tasks(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfdHJpYWdlX3F1ZXVlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0VHJpYWdlUXVldWUiLCJwYXRoIjoiL3YxL3RyaWFnZSIsInJlc291cmNlIjoidHJpYWdlIiwic2VjdGlvbl9zaGEyNTYiOiJmNDMxYmNhMDdkMjkzYjZiYzI5OTE0OGUzNGFlYmRiZTc4MjI1ZDZhZjBmMWRlYjAxNzk0ODAxNzFhZGJmYjA2Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjI4NzZkZTY4OGRhMjRjODk3NmU4NzVlMTcyYmI2ZjkxNDgzMzA0NGRmY2JlMTM5N2MyODlmMjMxMjg0MTU4MzUifQ -->
### `client.get_triage_queue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

#### Signature

```rust
pub async fn get_triage_queue(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X3dhaXRsaXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6ImQwMTAyY2NhMDQ3N2NiODBkMWYwZTkzN2E2MDliNzg4ODU0MzAyMmRkMzAxZTA2ODhlMDEyMmFiM2ZkZWY4MDciLCJzaWduYXR1cmVfc2hhMjU2IjoiYjczMjQ5NjY4MzQ5YzQ2NzdjZTNlNzU1NWQ5ZDk0ODNhZmNjMGJkMjM0MTUyYTBhOGQ5ZmRmNWU3MWRhYzMwZCJ9 -->
### `client.list_waitlist`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

#### Signature

```rust
pub async fn list_waitlist(&self, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJyZWdpc3Rlcl93YWl0bGlzdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6Ijc4NGMzZjBiOWNiYmZmYWY1OGY2ODE4YmFjOTY1MTJjMjFjMjUxZmE5ZjlkYThkYWMwMWMzODgwMjNkN2EzMzIiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWZkOGVmMzY1MDA5ZWZiMGU1MTVhZTE0M2FhMWE4MTkxMTg2MDNkZGM2ZTlmNzNjOTMwNTUzY2M2Y2UzNTY5NCJ9 -->
### `client.register_waitlist`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

#### Signature

```rust
pub async fn register_waitlist(&self, body: WaitlistRequest, request_options: Option<RequestOptions>) -> Result<(), ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

