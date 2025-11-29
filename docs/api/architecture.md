# Tool-Based Routing

Store and Demo APIs use a tool-based dispatch system where the `tool` field in the request body specifies the actual endpoint path. This allows for a generic POST endpoint that routes to specific functionality based on the tool name.

## Session-Based Architecture

The API uses a session-based model where:
1. Sessions contain multiple tasks
2. Tasks represent individual evaluation units
3. Both sessions and tasks have lifecycle states
4. Tasks can be executed independently or as part of a session

## Resource Usage Tracking

The `/tasks/log` endpoint enables detailed resource usage tracking, including:
- Model usage (tokens, API calls)
- Execution duration
- Custom metrics

This data is typically used for cost analysis and performance optimization.

---

**Generated from ERC3 package version 1.0.7 source code analysis**
