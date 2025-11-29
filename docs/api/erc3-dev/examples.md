# ERC3-Dev API Example

```bash
## Check current user identity
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/whoami" \
  -H "Content-Type: application/json" \
  -d '{"tool": "/whoami"}'

## Search for employees with Python skills
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/employees/search" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/employees/search",
    "query": "engineer",
    "offset": 0,
    "limit": 20,
    "location": "New York",
    "skills": [
      {
        "name": "Python",
        "min_level": 3,
        "max_level": 5
      }
    ]
  }'

## Get employee details
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/employees/get" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/employees/get",
    "id": "emp-001"
  }'

## Update employee salary
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/employees/update" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/employees/update",
    "employee": "emp-001",
    "salary": 85000
  }'

## Search wiki articles
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/wiki/search" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/wiki/search",
    "query_regex": "vacation.*policy"
  }'

## Load wiki article
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/wiki/load" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/wiki/load",
    "file": "/policies/vacation.md"
  }'

## Update wiki article
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/wiki/update" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/wiki/update",
    "file": "/policies/vacation.md",
    "content": "# Vacation Policy\\n\\nUpdated policy content..."
  }'

## Search customers
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/customers/search" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/customers/search",
    "query": "tech",
    "deal_phase": ["active", "exploring"],
    "offset": 0,
    "limit": 20
  }'

## Get project details
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/projects/get" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/projects/get",
    "id": "proj-001"
  }'

## Update project team
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/projects/team/update" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/projects/team/update",
    "id": "proj-001",
    "team": [
      {
        "employee": "emp-001",
        "time_slice": 0.5,
        "role": "Lead"
      },
      {
        "employee": "emp-003",
        "time_slice": 1.0,
        "role": "Designer"
      }
    ]
  }'

## Submit agent response
curl -X POST "https://erc.timetoact-group.at/erc3/task-789/respond" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "/respond",
    "message": "Found 5 matching employees",
    "outcome": "ok_answer",
    "links": [
      {
        "kind": "employee",
        "id": "emp-001"
      }
    ]
  }'
```

## Implementation Notes
