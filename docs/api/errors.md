# Standard Error Response Format

All endpoints return errors in a consistent format:

```json
{
  "status": 400,
  "error": "Detailed error message",
  "code": "ERROR_TYPE"
}
```

## Common Error Codes

| Status Code | Error Code | Description |
|-------------|------------|-------------|
| 400 | BAD_REQUEST | Invalid request parameters or format |
| 401 | UNAUTHORIZED | Invalid or missing API key |
| 403 | FORBIDDEN | Insufficient permissions for requested action |
| 404 | NOT_FOUND | Requested resource does not exist |
| 429 | RATE_LIMITED | API rate limit exceeded |
| 500 | INTERNAL_ERROR | Server-side error occurred |

## Authentication Errors

API key validation errors:

```json
{
  "status": 401,
  "error": "Invalid API key format. Key must start with 'key-'",
  "code": "INVALID_KEY_FORMAT"
}
```

```json
{
  "status": 401,
  "error": "API key not found or expired",
  "code": "KEY_NOT_FOUND"
}
```

## Validation Errors

Request validation failures:

```json
{
  "status": 400,
  "error": "Missing required field: 'session_id'",
  "code": "MISSING_REQUIRED_FIELD"
}
```

```json
{
  "status": 400,
  "error": "Invalid status value. Must be one of: ['open', 'done', 'evaluated']",
  "code": "INVALID_ENUM_VALUE"
}
```

## Usage Examples
