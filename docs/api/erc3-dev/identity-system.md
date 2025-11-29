# Identity & System

**Base URL Pattern**: `{base_url}/erc3-dev/{task_id}`

Endpoints in this section are part of the ERC3-Dev API used by the benchmark.

### Who Am I
**POST** `/whoami`

Retrieves the current user's identity and permissions.

**Request:**
```json
{
  "tool": "/whoami"
}
```

**Response:**
```json
{
  "current_user": "employee-123",
  "is_public": false,
  "location": "New York",
  "department": "Engineering",
  "today": "2024-01-01",
  "wiki_sha1": "abc123..."
}
```

## Employee Management

### List Employees
**POST** `/employees/list`

Retrieves a paginated list of employees.

**Request:**
```json
{
  "tool": "/employees/list",
  "offset": 0,
  "limit": 20
}
```

**Response:**
```json
{
  "next_offset": 20,
  "employees": [
    {
      "id": "emp-001",
      "name": "John Doe",
      "email": "john@example.com",
      "salary": 75000,
      "location": "New York",
      "department": "Engineering"
    }
  ]
}
```

### Search Employees
**POST** `/employees/search`

Searches employees with advanced filtering options.

**Request:**
```json
{
  "tool": "/employees/search",
  "query": "engineer",
  "offset": 0,
  "limit": 20,
  "location": "New York",
  "department": "Engineering",
  "manager": "mgr-001",
  "skills": [
    {
      "name": "Python",
      "min_level": 3,
      "max_level": 5
    }
  ],
  "wills": []
}
```

**Parameters:**
- `query` (optional): Text search query
- `offset` (required): Pagination offset
- `limit` (required): Maximum results to return
- `location` (optional): Filter by office location
- `department` (optional): Filter by department
- `manager` (optional): Filter by manager ID
- `skills` (optional): Array of skill filters
- `wills` (optional): Array of willingness filters

**Response:**
```json
{
  "next_offset": 20,
  "employees": [
    {
      "id": "emp-001",
      "name": "John Doe",
      "email": "john@example.com",
      "salary": 75000,
      "location": "New York",
      "department": "Engineering"
    }
  ]
}
```

### Get Employee
**POST** `/employees/get`

Retrieves detailed information about a specific employee.

**Request:**
```json
{
  "tool": "/employees/get",
  "id": "emp-001"
}
```

**Response:**
```json
{
  "employee": {
    "id": "emp-001",
    "name": "John Doe",
    "email": "john@example.com",
    "salary": 75000,
    "notes": "Senior engineer with Python expertise",
    "location": "New York",
    "department": "Engineering",
    "skills": [
      {
        "name": "Python",
        "level": 5
      },
      {
        "name": "JavaScript",
        "level": 4
      }
    ],
    "wills": [
      {
        "name": "Leadership",
        "level": 3
      }
    ]
  }
}
```

### Update Employee Info
**POST** `/employees/update`

Updates salary, skills, notes, and current assignment details.

**Request:**
```json
{
  "tool": "/employees/update",
  "employee": "emp-001",
  "notes": "Updated notes",
  "salary": 80000,
  "skills": [
    {
      "name": "Python",
      "level": 5
    }
  ],
  "wills": [],
  "location": "San Francisco",
  "department": "Engineering",
  "changed_by": "emp-002"
}
```

**Parameters:**
- `employee` (required): Employee ID
- `notes` (optional): Employee notes
- `salary` (optional): Updated salary
- `skills` (optional): Array of skill levels
- `wills` (optional): Array of willingness levels
- `location` (optional): New location
- `department` (optional): New department
- `changed_by` (optional): Employee ID of the user making the change

**Response:**
```json
{
  "employee": {
    "id": "emp-001",
    "name": "John Doe",
    "email": "john@example.com",
    "salary": 80000,
    "notes": "Updated notes",
    "location": "San Francisco",
    "department": "Engineering",
    "skills": [
      {
        "name": "Python",
        "level": 5
      }
    ],
    "wills": []
  }
}
```

## Wiki Management

### List Wiki Articles
**POST** `/wiki/list`

Retrieves a list of all wiki article paths.

**Request:**
```json
{
  "tool": "/wiki/list"
}
```

**Response:**
```json
{
  "paths": [
    "/company/handbook.md",
    "/engineering/onboarding.md",
    "/policies/vacation.md"
  ],
  "sha1": "abc123..."
}
```

### Load Wiki Article
**POST** `/wiki/load`

Retrieves the content of a specific wiki article.

**Request:**
```json
{
  "tool": "/wiki/load",
  "file": "/company/handbook.md"
}
```

**Response:**
```json
{
  "file": "/company/handbook.md",
  "content": "# Company Handbook\n\nWelcome to our company..."
}
```

### Search Wiki
**POST** `/wiki/search`

Searches wiki content using regular expressions.

**Request:**
```json
{
  "tool": "/wiki/search",
  "query_regex": "vacation.*policy"
}
```

**Response:**
```json
{
  "results": [
    {
      "content": "Our vacation policy allows 20 days per year...",
      "linum": 42,
      "path": "/policies/vacation.md"
    }
  ]
}
```

### Update Wiki Article
**POST** `/wiki/update`

Create or update a wiki article.

**Request:**
```json
{
  "tool": "/wiki/update",
  "file": "/policies/new-policy.md",
  "content": "# New Policy\n\nThis is the new policy content...",
  "changed_by": "emp-001"
}
```

**Response:**
```json
{}
```

## Customer Management

### List Customers
**POST** `/customers/list`

Retrieves a paginated list of customers.

**Request:**
```json
{
  "tool": "/customers/list",
  "offset": 0,
  "limit": 20
}
```

**Response:**
```json
{
  "next_offset": 20,
  "companies": [
    {
      "id": "cust-001",
      "name": "Acme Corp",
      "location": "Boston",
      "deal_phase": "active",
      "high_level_status": "In progress"
    }
  ]
}
```

### Search Customers
**POST** `/customers/search`

Searches customers with filtering options.

**Request:**
```json
{
  "tool": "/customers/search",
  "query": "tech",
  "deal_phase": ["active", "exploring"],
  "account_managers": ["emp-001"],
  "locations": ["Boston", "New York"],
  "offset": 0,
  "limit": 20
}
```

**Parameters:**
- `query` (optional): Text search query
- `deal_phase` (optional): Array of deal phases to filter by
- `account_managers` (optional): Array of account manager IDs
- `locations` (optional): Array of customer locations
- `offset` (required): Pagination offset
- `limit` (required): Maximum results to return

**Response:**
```json
{
  "companies": [
    {
      "id": "cust-001",
      "name": "TechCorp",
      "location": "Boston",
      "deal_phase": "active",
      "high_level_status": "In progress"
    }
  ],
  "next_offset": 20
}
```

### Get Customer
**POST** `/customers/get`

Retrieves detailed information about a specific customer.

**Request:**
```json
{
  "tool": "/customers/get",
  "id": "cust-001"
}
```

**Response:**
```json
{
  "company": {
    "id": "cust-001",
    "name": "Acme Corp",
    "brief": "Enterprise software company",
    "location": "Boston",
    "primary_contact_name": "Jane Smith",
    "primary_contact_email": "jane@acme.com",
    "deal_phase": "active",
    "high_level_status": "In progress",
    "account_manager": "emp-001"
  },
  "found": true
}
```

## Project Management

### List Projects
**POST** `/projects/list`

Retrieves a paginated list of projects.

**Request:**
```json
{
  "tool": "/projects/list",
  "offset": 0,
  "limit": 20
}
```

**Response:**
```json
{
  "next_offset": 20,
  "projects": [
    {
      "id": "proj-001",
      "name": "Website Redesign",
      "customer": "cust-001",
      "status": "active"
    }
  ]
}
```

### Search Projects
**POST** `/projects/search`

Searches projects with advanced filtering.

**Request:**
```json
{
  "tool": "/projects/search",
  "query": "website",
  "customer_id": "cust-001",
  "status": ["active", "exploring"],
  "team": {
    "employee_id": "emp-001",
    "role": "Lead",
    "min_time_slice": 0.5
  },
  "include_archived": false,
  "offset": 0,
  "limit": 20
}
```

**Parameters:**
- `query` (optional): Text search query
- `customer_id` (optional): Filter by customer ID
- `status` (optional): Array of project statuses
- `team` (optional): Filter by team member criteria
  - `employee_id` (optional): Specific employee ID
  - `role` (optional): Team role
  - `min_time_slice` (optional): Minimum time allocation
- `include_archived` (optional): Include archived projects (default: false)
- `offset` (required): Pagination offset
- `limit` (required): Maximum results to return

**Response:**
```json
{
  "projects": [
    {
      "id": "proj-001",
      "name": "Website Redesign",
      "customer": "cust-001",
      "status": "active"
    }
  ]
}
```

### Get Project
**POST** `/projects/get`

Retrieves detailed information about a specific project.

**Request:**
```json
{
  "tool": "/projects/get",
  "id": "proj-001"
}
```

**Response:**
```json
{
  "project": {
    "id": "proj-001",
    "name": "Website Redesign",
    "description": "Complete redesign of corporate website",
    "customer": "cust-001",
    "status": "active",
    "team": [
      {
        "employee": "emp-001",
        "time_slice": 0.75,
        "role": "Lead"
      },
      {
        "employee": "emp-002",
        "time_slice": 1.0,
        "role": "Engineer"
      }
    ]
  },
  "found": true
}
```

### Update Project Team
**POST** `/projects/team/update`

Replaces the team allocation for a project.

**Request:**
```json
{
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
}
```

**Response:**
```json
{}
```

### Update Project Status
**POST** `/projects/status/update`

Changes the project status/phase.

**Request:**
```json
{
  "tool": "/projects/status/update",
  "id": "proj-001",
  "status": "paused"
}
```

**Response:**
```json
{}
```

## Error Handling
