# Benchmarks

### List Benchmarks
**POST** `/benchmarks/list`

Retrieves a list of available benchmarks.

**Request:**
```json
{}
```

**Response:**
```json
{
  "benchmarks": [
    {
      "id": "benchmark-1",
      "short_description": "Description of benchmark 1",
      "status": "active",
      "tasks": 10
    },
    {
      "id": "benchmark-2",
      "short_description": "Description of benchmark 2",
      "status": "active",
      "tasks": 15
    }
  ]
}
```

### View Benchmark Details
**POST** `/benchmarks/view`

Retrieves detailed information about a specific benchmark.

**Request:**
```json
{
  "benchmark": "benchmark-1"
}
```

**Response:**
```json
{
  "id": "benchmark-1",
  "description": "Detailed description of the benchmark",
  "status": "active",
  "specs": [
    {
      "id": "spec-1",
      "task": "Specification task description",
      "gotcha": "Optional hint or gotcha about this spec"
    }
  ],
  "routes": [
    {
      "path": "/api/v1/route1",
      "description": "Route description",
      "sample_request": {"key": "example request body"},
      "sample_response": {"key": "example response body"}
    }
  ]
}
```
