# Secret Management

**Base URL Pattern**: `{base_url}/demo/{task_id}`

Demo-only endpoint for retrieving a task-specific secret.

### Get Secret
**POST** `/secret`

Retrieves a secret value for the current demo task.

**Request:**
```json
{
  "tool": "/secret"
}
```

**Response:**
```json
{
  "value": "secret-value-123"
}
```
