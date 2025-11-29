# Complete Session Workflow

```bash
## 1. Get API key
curl -X POST https://erc.timetoact-group.at/get_key \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'

## 2. List available benchmarks
curl -X POST https://erc.timetoact-group.at/benchmarks/list \
  -H "Content-Type: application/json" \
  -d '{}'

## 3. Start a new session
curl -X POST https://erc.timetoact-group.at/sessions/start \
  -H "Content-Type: application/json" \
  -d '{
    "account_key": "key-abc123def456...",
    "benchmark": "benchmark-1",
    "workspace": "my-workspace",
    "name": "Test Session",
    "architecture": "x86_64"
  }'

## 4. Check session status
curl -X POST https://erc.timetoact-group.at/sessions/status \
  -H "Content-Type: application/json" \
  -d '{"session_id": "session-123"}'

## 5. Submit completed session
curl -X POST https://erc.timetoact-group.at/sessions/submit \
  -H "Content-Type: application/json" \
  -d '{"session_id": "session-123"}'
```
