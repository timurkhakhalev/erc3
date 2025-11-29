# Time Tracking

**Base URL Pattern**: `{base_url}/erc3-dev/{task_id}`

These endpoints manage time entries and aggregate summaries for the ERC3-Dev benchmark.

## Log Time Entry
**POST** `/time/log`

Creates a new time entry.

**Request:**
```json
{
  "tool": "/time/log",
  "employee": "emp-001",
  "customer": "cust-001",
  "project": "proj-001",
  "date": "2024-01-01",
  "hours": 8.0,
  "work_category": "implementation",
  "notes": "Worked on feature X",
  "billable": true,
  "status": "submitted",
  "logged_by": "emp-001"
}
```

**Response:**
```json
{
  "id": "time-001",
  "employee": "emp-001",
  "customer": "cust-001",
  "project": "proj-001",
  "date": "2024-01-01",
  "hours": 8.0,
  "work_category": "implementation",
  "notes": "Worked on feature X",
  "billable": true,
  "status": "submitted"
}
```

## Update Time Entry
**POST** `/time/update`

Updates an existing time entry.

**Request:**
```json
{
  "tool": "/time/update",
  "id": "time-001",
  "date": "2024-01-01",
  "hours": 7.5,
  "work_category": "implementation",
  "notes": "Adjusted hours after review",
  "billable": true,
  "status": "approved",
  "changed_by": "emp-002"
}
```

**Response:**
```json
{}
```

## Get Time Entry
**POST** `/time/get`

Retrieves a single time entry by ID.

**Request:**
```json
{
  "tool": "/time/get",
  "id": "time-001"
}
```

**Response:**
```json
{
  "entry": {
    "employee": "emp-001",
    "customer": "cust-001",
    "project": "proj-001",
    "date": "2024-01-01",
    "hours": 7.5,
    "work_category": "implementation",
    "notes": "Adjusted hours after review",
    "billable": true,
    "status": "approved"
  }
}
```

## Search Time Entries
**POST** `/time/search`

Searches time entries with filtering and aggregation.

**Request:**
```json
{
  "tool": "/time/search",
  "employee": "emp-001",
  "customer": "cust-001",
  "project": "proj-001",
  "date_from": "2024-01-01",
  "date_to": "2024-01-31",
  "work_category": "implementation",
  "billable": "billable",
  "status": "approved",
  "limit": 50,
  "offset": 0
}
```

**Response:**
```json
{
  "entries": [
    {
      "id": "time-001",
      "employee": "emp-001",
      "customer": "cust-001",
      "project": "proj-001",
      "date": "2024-01-01",
      "hours": 7.5,
      "work_category": "implementation",
      "notes": "Adjusted hours after review",
      "billable": true,
      "status": "approved"
    }
  ],
  "next_offset": null,
  "total_hours": 7.5,
  "total_billable": 7.5,
  "total_non_billable": 0.0
}
```

## Time Summary by Project
**POST** `/time/summary/by-project`

Aggregates hours per project.

**Request:**
```json
{
  "tool": "/time/summary/by-project",
  "date_from": "2024-01-01",
  "date_to": "2024-01-31",
  "customers": ["cust-001"],
  "projects": ["proj-001"],
  "employees": ["emp-001"],
  "billable": "billable"
}
```

**Response:**
```json
{
  "summaries": [
    {
      "customer": "cust-001",
      "project": "proj-001",
      "total_hours": 7.5,
      "billable_hours": 7.5,
      "non_billable_hours": 0.0,
      "distinct_employees": 1
    }
  ]
}
```

## Time Summary by Employee
**POST** `/time/summary/by-employee`

Aggregates hours per employee.

**Request:**
```json
{
  "tool": "/time/summary/by-employee",
  "date_from": "2024-01-01",
  "date_to": "2024-01-31",
  "customers": ["cust-001"],
  "projects": ["proj-001"],
  "employees": ["emp-001"],
  "billable": ""
}
```

**Response:**
```json
{
  "summaries": [
    {
      "employee": "emp-001",
      "total_hours": 7.5,
      "billable_hours": 7.5,
      "non_billable_hours": 0.0
    }
  ]
}
```
