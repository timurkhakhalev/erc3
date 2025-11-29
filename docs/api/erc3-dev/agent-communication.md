# Agent Communication

**Base URL Pattern**: `{base_url}/erc3/{task_id}`

Part of the ERC3-Dev API used by the benchmark.

### Provide Agent Response
**POST** `/respond`

Submit an agent-formatted reply with optional reference links and a structured outcome.

**Request:**
```json
{
  "tool": "/respond",
  "message": "Response message",
  "outcome": "ok_answer",
  "links": [
    {
      "kind": "employee",
      "id": "emp-001"
    },
    {
      "kind": "project",
      "id": "proj-123"
    }
  ]
}
```

**Fields:**
- `message` (required): Human-readable agent reply text.
- `outcome` (required): High-level result classification (see `Outcome` enum in `data-types.md`).
- `links` (optional): Array of structured reference links pointing at employees, customers, projects, wiki pages, or locations.

**Response:**
```json
{}
```
