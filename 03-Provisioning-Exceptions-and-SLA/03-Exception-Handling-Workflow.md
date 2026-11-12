# Scenario 3 — Exception Handling Workflow

**Source:** Exception Management SOP (`00-Governance-Framework/07-Exception-Management-SOP.docx`), Section 3 — General exception handling process
**Classification:** Governance policy requirement (procedural), not an IdentityGuard application feature

## General exception handling process

The Exception Management SOP defines the following process, which this scenario follows:

| Step | Action | IdentityGuard support |
|---|---|---|
| 1. Log | Identify the exception type and log a ServiceNow PDI ticket or work item | Manual / simulated (no IdentityGuard-ServiceNow integration) |
| 2. Validate | Perform initial validation (identity, request completeness, entitlement validity) | Supported via GET /users, GET /roles, GET /access-requests |
| 3. Investigate | Investigate root cause using IdentityGuard audit events and reports | Supported via GET /audit/events, GET /reports/* |
| 4. Prioritise | Assign priority and SLA per the SLA table | Manual (training classification) |
| 5. Temporary control | Apply temporary controls where appropriate | Manual; IdentityGuard does not auto-apply temporary controls for exceptions |
| 6. Escalate | Escalate per the escalation path if unresolved within SLA | Manual / simulated |
| 7. Resolve and verify | Resolve and verify; confirm with audit evidence | Supported via provisioning/reject/audit endpoints |
| 8. Close | Close the ticket with evidence and closure criteria met | Manual / documented |

## Exception categories (from SOP Section 4)

The SOP defines these exception types, of which this scenario demonstrates:

| Category | SOP reference | Demonstrated in this scenario |
|---|---|---|
| Provisioning failures | 4.3 | Yes — EXC-001 (duplicate) and EXC-002 (SoD-blocked) |
| SoD conflicts | 4.6 | Yes — EXC-002 |
| Delayed requests | 4.8 | No natural case identified; covered in limitations |
| Missing or invalid approval | 4.1 | No natural case identified; covered in limitations |

## Exception categories NOT demonstrated

The following SOP exception types were not observed in the live environment and are not manufactured for this scenario:
- Invalid or incomplete requests (4.2)
- Deprovisioning failures (4.4)
- Incorrect entitlement assignment (4.5)
- Urgent leaver requests (4.7)
- SLA breaches (4.9)
- Directory synchronisation failures (4.10)
- Application and directory mismatches (4.11)
- Unavailable approvers (4.12)
- Emergency access (4.13)

These are listed in the Exceptions and Limitations register as untested/not observed.

## Application limitations relevant to exceptions

- IdentityGuard supports a single approver per access request; additional organisational approvals are manual.
- An APPROVED request that cannot be provisioned (e.g., duplicate or SoD-blocked) cannot also be rejected through the API (reject requires REQUESTED status). Such requests remain APPROVED and unprovisioned; resolution is by documentation and closure decision, not API mutation.
- IdentityGuard does not implement server-side SLA tracking or automatic breach escalation. SLA monitoring is manual.
- Direct role assignment (assign_role/remove_role) bypasses SoD and was not used to resolve any exception.

## Evidence handling

Every exception has a unique reference (IAM-EXC-2026-001 to IAM-EXC-2026-003) and supporting evidence. Closure requires verification evidence (audit events, assignment state) recorded in the exception register.
