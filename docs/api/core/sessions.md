# Sessions

### Search Sessions
**POST** `/sessions/search`

Searches for sessions based on various criteria.

**Request:**
```json
{
  "account_key": "key-abc123def456...",
  "workspace": "workspace-name",
  "status": ["open", "done", "evaluated"],
  "benchmark": "benchmark-1"
}
```

**Response:**
```json
{
  "sessions": [
    {
      "id": "session-123",
      "benchmark_type": "benchmark-1",
      "status": "open",
      "created_at": "2024-01-01T00:00:00Z",
      "workspace": "workspace-name",
      "benchmark_description": "Detailed benchmark description",
      "total_tasks": 10,
      "completed_tasks": 5,
      "running_tasks": 3,
      "new_tasks": 2,
      "failed_tasks": 0,
      "score": 0.85
    }
  ]
}
```

### Start Session
**POST** `/sessions/start`

Creates and starts a new evaluation session.

**Request:**
```json
{
  "account_key": "key-abc123def456...",
  "benchmark": "benchmark-1",
  "workspace": "workspace-name",
  "name": "My Evaluation Session",
  "architecture": "x86_64"
}
```

**Parameters:**
- `account_key` (required): API authentication key
- `benchmark` (required): Benchmark ID to evaluate
- `workspace` (required): Workspace identifier
- `name` (optional): Session display name
- `architecture` (optional): System architecture identifier

**Response:**
```json
{
  "session_id": "session-123",
  "task_count": 10
}
```

### Get Session Status
**POST** `/sessions/status`

Retrieves the current status of a session.

**Request:**
```json
{
  "session_id": "session-123"
}
```

**Response:**
```json
{
  "status": "running",
  "benchmark": "benchmark-1",
  "failed": 0,
  "new": 2,
  "running": 5,
  "completed": 3,
  "tasks": [
    {
      "task_id": "task-1",
      "spec_id": "spec-1",
      "num": 1,
      "task_text": "Task description...",
      "status": "completed",
      "score": 0.95,
      "benchmark": "benchmark-1",
      "error_message": null
    }
  ],
  "name": "My Evaluation Session",
  "architecture": "x86_64",
  "flags": "sgr",
  "score": 0.95
}
```

**Response Fields:**
- `status`: Current session status
- `benchmark`: Benchmark ID
- `failed`, `new`, `running`, `completed`: Task counts by status
- `tasks`: Array of task objects with `task_id`, `spec_id`, `num`, `task_text`, `status`, `score`, `benchmark`, `error_message`
- `name`: Session display name
- `architecture`: System architecture
- `flags` (optional): Single SessionFlag value
- `score` (optional): Overall session score

### Submit Session
**POST** `/sessions/submit`

Submits a completed session for evaluation.

**Request:**
```json
{
  "session_id": "session-123"
}
```

**Response:**
```json
{
  "status": "submitted"
}
```
