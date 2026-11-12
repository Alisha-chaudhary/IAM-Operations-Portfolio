# Scenario 3 — Escalation Records

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Recorded at:** 12 November 2026
**Recorder:** IAM Operations Analyst

## Escalation path (from SOP)

The Exception Management SOP defines escalation paths per exception type. Generally: IAM Operations Analyst -> IAM Administrator -> Business head / IT Security. Escalation is required only if a case is unresolved within its SLA.

## Escalation decisions

| Exception ID | Escalation required? | Reason | Escalation performed | Label |
|---|---|---|---|---|
| IAM-EXC-2026-001 | No | Closed by circumstance same day (access already held). Within SLA. | None | Not applicable |
| IAM-EXC-2026-002 | No | Closed by preventive control same day (SoD blocked). Within SLA. | None | Not applicable |
| IAM-EXC-2026-003 | No | Self-expiring access; monitoring only. Within SLA. | None | Not applicable |

## Stakeholder coordination (simulated)

No stakeholder escalation was required for any exception. All three cases were resolved or placed in monitoring within the same business day, below their SLA thresholds. Where stakeholder awareness would be appropriate in a real operation (e.g., informing the requester that a duplicate or SoD-blocked request will not be provisioned), that communication is noted here as simulated and was not executed through any real system.

| Exception ID | Stakeholder | Would-coordinate | Action requested | Label |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Rahul Mehta (requester) | Inform that Finance Manager already held | N/A — no action needed | Simulated (not executed) |
| IAM-EXC-2026-002 | Rahul Mehta (requester), Priya Nair (manager) | Inform that Payment Approver blocked by SoD | N/A — no action needed | Simulated (not executed) |
| IAM-EXC-2026-003 | Sneha Rao (requester) | Inform that access auto-expires | N/A — no action needed | Simulated (not executed) |

## ServiceNow PDI

The Exception Management SOP references logging a ServiceNow PDI ticket or work item. IdentityGuard has no ServiceNow integration, and no ServiceNow environment was available or used in this lab. Ticket logging is therefore simulated/manual and not claimed as an actual system action.

## Evidence

- EXC-001-E09, EXC-002-E09, EXC-003-E09: Stakeholder escalation records
