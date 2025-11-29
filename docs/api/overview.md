# Overview

The ERC3 REST API provides endpoints for benchmark evaluation management, task execution, and specialized store/demo operations. This document describes the actual HTTP endpoints used by the ERC3 Python client under the hood.

**Base URL**: Configurable (defaults to `https://erc.timetoact-group.at`)

## HTTP Patterns

### Authentication
- **Method**: API key passed in request body (not HTTP headers)
- **Format**: Keys must start with `key-` prefix
- **Example**: `{"account_key": "key-abc123def456..."}`

### Request Format
- **Method**: All endpoints use `POST` requests
- **Content-Type**: `application/json`
- **Body**: JSON payload with endpoint-specific fields

### Response Format
- **Success**: JSON response with 200 status code
- **Error**: Structured error format
  ```json
  {
    "status": 400,
    "error": "Error description",
    "code": "ERROR_CODE"
  }
  ```

### URL Structure
- **Core API**: `{base_url}/{endpoint}`
- **Store API**: `{base_url}/store/{task_id}/{endpoint}`
- **Demo API**: `{base_url}/demo/{task_id}/{endpoint}`
- **ERC3-Dev API**: `{base_url}/erc3/{task_id}/{endpoint}`
