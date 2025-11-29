# ERC3-Dev API Endpoints

**Base URL Pattern**: `{base_url}/erc3/{task_id}`

The ERC3-Dev API is used by the ERC3 benchmark tasks. Endpoints are grouped by domain; see the linked documents for request/response details.

- Identity & system: `/whoami`
- Employee management: `/employees/list`, `/employees/search`, `/employees/get`, `/employees/update`
- Wiki management: `/wiki/list`, `/wiki/search`, `/wiki/load`, `/wiki/update`
- Customer management: `/customers/list`, `/customers/search`, `/customers/get`
- Project management: `/projects/list`, `/projects/search`, `/projects/get`, `/projects/team/update`, `/projects/status/update`
- Time tracking: `/time/log`, `/time/update`, `/time/get`, `/time/search`, `/time/summary/by-project`, `/time/summary/by-employee`
- Agent communication: `/respond`

Docs:
- [Identity & System](identity-system.md)
- [Agent Communication](agent-communication.md)
- [Data Types](data-types.md)
- [Time Tracking](time-tracking.md)
