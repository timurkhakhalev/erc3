# Store API Example

```bash
## View shopping basket
curl -X POST "https://erc.timetoact-group.at/store/task-123/basket/view" \
  -H "Content-Type: application/json" \
  -d '{"tool": "/basket/view"}'

## Add item to basket
curl -X POST "https://erc.timetoact-group.at/store/task-123/basket/add" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/basket/add",
    "sku": "PROD-001",
    "quantity": 2
  }'
```
