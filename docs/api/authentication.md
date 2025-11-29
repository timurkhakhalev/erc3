# Authentication

### Get API Key
**POST** `/get_key`

Retrieves an API key for a given email address.

**Request:**
```json
{
  "email": "user@example.com"
}
```

**Response:**
```json
{
  "key": "key-abc123def456...",
  "public_key": "public-key-string"
}
```

## SessionFlag Enum

When present, the `flags` value in session status responses is a single enum with these values:

- **`sgr`**: Session is part of the SGR (Store, Generalization, Reasoning) benchmark suite
- **`local`**: Session is running in local development/testing mode
- **`compete`**: Session is part of a competitive evaluation or leaderboard submission

Note: the HTTP request body for `/sessions/start` currently does **not** include `flags`. The server only returns a single `flags` value in `/sessions/status` responses.
