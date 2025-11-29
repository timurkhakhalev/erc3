# Answer Submission

**Base URL Pattern**: `{base_url}/demo/{task_id}`

Demo-only endpoint for submitting answers.

### Submit Answer
**POST** `/answer`

Submits an answer for the current demo task.

**Request:**
```json
{
  "tool": "/answer",
  "answer": "The answer to the demo question"
}
```

**Response:**
```json
{}
```
