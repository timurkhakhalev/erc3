# Tasks

### Start Task
**POST** `/tasks/start`

Starts execution of a specific task. This endpoint operates in two modes:

1. **Session-based mode**: Provide `task_id` to start a specific task within an existing session
2. **Ad-hoc mode**: Provide `benchmark` and `spec_id` to start a standalone task outside a session

**Request:**
```json
{
  "task_id": "task-1",
  "benchmark": "benchmark-1",
  "spec_id": "spec-1"
}
```

**Parameters:**
- `task_id` (optional): Task ID from an existing session (session-based mode)
- `benchmark` (optional): Benchmark ID for ad-hoc task creation
- `spec_id` (optional): Specification ID for ad-hoc task creation

**Note:** Either `task_id` alone OR both `benchmark` and `spec_id` must be provided.

**Response:**
```json
{
  "task_id": "task-1",
  "session_id": "session-123",
  "status": "in_progress"
}
```

### Complete Task
**POST** `/tasks/complete`

Marks a task as completed and retrieves evaluation results.

**Request:**
```json
{
  "task_id": "task-1"
}
```

**Response:**
```json
{
  "status": "completed",
  "eval": {
    "score": 0.95,
    "logs": "Task completed successfully"
  }
}
```

### View Task Details
**POST** `/tasks/view`

Retrieves detailed information about a task, including logs since a specific time.

**Request:**
```json
{
  "task_id": "task-1",
  "since": 1640995200
}
```

**Response:**
```json
{
  "task_id": "task-1",
  "text": "Task description and content",
  "session_id": "session-123",
  "spec": "spec-1",
  "status": "completed",
  "logs": [
    {
      "type": "stdout",
      "text": "Task started",
      "time": "2024-01-01T12:00:00Z",
      "unix": 1704100800,
      "body": {}
    }
  ],
  "score": 0.95,
  "benchmark": "benchmark-1",
  "error_message": null
}
```

### Log Task Usage
**POST** `/tasks/log`

Logs resource usage and duration for a task.

**Request:**
```json
{
  "task_id": "task-1",
  "model": "gpt-4",
  "usage": {
    "prompt_tokens": 1000,
    "completion_tokens": 500,
    "total_tokens": 1500
  },
  "duration_sec": 45.5
}
```

**Notes:**
- The client flattens nested usage structures into a dotted dictionary and drops zero values (see `normalize_usage`).
- Accepted keys therefore look like `prompt_tokens`, `completion_tokens`, or nested forms like `model.openai.total_tokens` when provided.

**Response:**
```json
{}
```
