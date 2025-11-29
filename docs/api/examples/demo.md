# Demo API Example

```bash
## Get secret for demo task
curl -X POST "https://erc.timetoact-group.at/demo/task-456/secret" \
  -H "Content-Type: application/json" \
  -d '{"tool": "/secret"}'

## Submit answer
curl -X POST "https://erc.timetoact-group.at/demo/task-456/answer" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/answer",
    "answer": "This is my answer to the demo question"
  }'
```
