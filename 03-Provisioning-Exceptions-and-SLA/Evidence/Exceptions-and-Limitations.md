# Exceptions and Limitations Register

**Scenario:** Provisioning Exceptions and SLA Management (Scenario 3)
**Compiled:** 12 November 2026
**Compiled by:** IAM Operations Analyst

## Formal exceptions raised

No formal access exceptions (with compensating controls and expiry) were raised or approved in this scenario. All three cases were resolved by documentation decision:
- EXC-001: closed — entitlement already held
- EXC-002: closed — SoD conflict prevented
- EXC-003: open — monitoring auto-expiry

## Technical limitations and application behaviour

| # | Limitation | Component | Impact | Control decision |
|---|---|---|---|---|
| L1 | APPROVED requests cannot be rejected through the API (reject requires REQUESTED status; APPROVED returns 409 "already decided") | `POST /access-requests/{id}/reject` | Requests ID 3 and 4 remain APPROVED and unprovisioned; cannot be closed via API | Resolution by documentation and closure decision, not API mutation |
| L2 | Provisioning blocked for duplicate entitlement (409 "User already has this role") | `POST /access-requests/{id}/provision` | Request ID 4 cannot be provisioned | Closed as superseded — access already held via Request ID 1 |
| L3 | Provisioning blocked by SoD (409 "Provisioning blocked by SoD policy") | `POST /access-requests/{id}/provision` (evaluate_user_sod) | Request ID 3 cannot be provisioned | Closed as conflict prevented — no conflicting access granted |
| L4 | No server-side SLA tracking or automatic breach escalation | IdentityGuard application | SLA monitoring is manual; no automated SLA clock | SLA tracked manually using training targets from Exception Management SOP |
| L5 | No ServiceNow integration | IdentityGuard application | Exception ticket logging cannot be performed in-system | Ticket logging simulated/manual; not claimed as actual system action |
| L6 | Direct role assignment (assign_role/remove_role) bypasses SoD | `app/iam/service.py` | Not a supported exception-resolution path | Not used; governed workflow respected |

## Untested controls (not executed, documented as analysis only)

The following SOP exception types were not observed in the live environment and were not manufactured for this scenario:
- Invalid or incomplete requests (SOP 4.2)
- Deprovisioning failures (SOP 4.4)
- Incorrect entitlement assignment (SOP 4.5)
- Urgent leaver requests (SOP 4.7)
- SLA breaches (SOP 4.9)
- Directory synchronisation failures (SOP 4.10)
- Application and directory mismatches (SOP 4.11)
- Unavailable approvers (SOP 4.12)
- Emergency access (SOP 4.13)

These are recorded as untested/not observed, not as resolved cases.

## No manufacturing of failures

No database corruption, code modification, or artificial failure was introduced to create exceptions. All three cases are real requests from Scenario 2 left in a genuine unresolved state.

## Classification

All simulated stakeholder actions and SLA targets are labelled as simulated/training. This is not a real organisational event.
