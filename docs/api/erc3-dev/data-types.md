# Data Types

### Enumerations

**Outcome** (used by `/respond`)
- `"ok_answer"` - Correct, confident answer.
- `"ok_not_found"` - No matching result, but the search was performed correctly.
- `"denied_security"` - Request rejected for security or privacy reasons.
- `"none_clarification_needed"` - Need clarification from the user before proceeding.
- `"none_unsupported"` - Task is out of scope or unsupported.
- `"error_internal"` - Internal error when fulfilling the request.

**LinkKind** (used in `links` for `/respond`)
- `"employee"` - Reference to an employee entity.
- `"customer"` - Reference to a customer/company.
- `"project"` - Reference to a project.
- `"wiki"` - Reference to a wiki article.
- `"location"` - Reference to a location/office.

**DealPhase**
- `"idea"` - Initial idea phase.
- `"exploring"` - Exploration/research phase.
- `"active"` - Active/in-progress phase.
- `"paused"` - Temporarily paused.
- `"archived"` - Completed or archived.

**TeamRole**
- `"Lead"` - Team lead.
- `"Engineer"` - Software engineer.
- `"Designer"` - Designer.
- `"QA"` - Quality assurance.
- `"Ops"` - Operations.
- `"Other"` - Other role.

**TimeEntryStatus**
- `""` - Unspecified status.
- `"draft"` - Draft, not yet submitted.
- `"submitted"` - Submitted for approval.
- `"approved"` - Approved for invoicing.
- `"invoiced"` - Invoiced/billed.
- `"voided"` - Voided/cancelled.

**BillableFilter**
- `""` - No filter, include all time.
- `"billable"` - Only billable entries.
- `"non_billable"` - Only non-billable entries.

### Complex Types

**SkillLevel**
```json
{
  "name": "string",
  "level": "integer"
}
```

**SkillFilter**
```json
{
  "name": "string",
  "min_level": "integer",
  "max_level": "integer (default: 0)"
}
```

**Workload**
```json
{
  "employee": "EmployeeID",
  "time_slice": "float",
  "role": "TeamRole"
}
```

**TimeEntry**
```json
{
  "employee": "EmployeeID",
  "customer": "CompanyID or null",
  "project": "ProjectID or null",
  "date": "YYYY-MM-DD",
  "hours": "float",
  "work_category": "string",
  "notes": "string",
  "billable": "boolean",
  "status": "TimeEntryStatus"
}
```

**TimeEntryWithID**
```json
{
  "id": "TimeEntryID",
  "employee": "EmployeeID",
  "customer": "CompanyID or null",
  "project": "ProjectID or null",
  "date": "YYYY-MM-DD",
  "hours": "float",
  "work_category": "string",
  "notes": "string",
  "billable": "boolean",
  "status": "TimeEntryStatus"
}
```

**TimeSummaryByProject**
```json
{
  "customer": "CompanyID",
  "project": "ProjectID",
  "total_hours": "float",
  "billable_hours": "float",
  "non_billable_hours": "float",
  "distinct_employees": "integer"
}
```

**TimeSummaryByEmployee**
```json
{
  "employee": "EmployeeID",
  "total_hours": "float",
  "billable_hours": "float",
  "non_billable_hours": "float"
}
```
