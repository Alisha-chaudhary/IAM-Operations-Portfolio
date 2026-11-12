# Scenario 3 — Scenario Closure Report

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Scenario:** Provisioning Exceptions and SLA Management (Scenario 3)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Closed at:** 12 November 2026
**Closed by:** IAM Operations Analyst

## Scenario summary

Scenario 3 demonstrated the operational handling of access provisioning exceptions using three real requests left in an unresolved state after Scenario 2. No new identities or duplicate access requests were created. All actions were executed against the local IdentityGuard lab (`http://127.0.0.1:8000`) and evidenced with sanitised API responses and audit events.

## Case outcomes

| Exception ID | Focus | Priority | Outcome | Status |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Approved-but-unprovisioned duplicate (Finance Manager) | P3 - Medium | Closed — entitlement already held via Request ID 1 | Closed |
| IAM-EXC-2026-002 | SoD-blocked provisioning (Payment Approver vs Payment Initiator) | P2 - High | Closed — conflict prevented, no access granted | Closed |
| IAM-EXC-2026-003 | Time-limited privileged access expiring (System Administrator) | P3 - Medium | Open — monitoring auto-expiry | Open (monitoring) |

## Completed work

1. **Exception identification:** Monitored the access request inventory and identified three genuine exceptions. Distinguished them from normal completed processing (Request ID 1).
2. **Request validation:** Confirmed identity, request status, role existence, target active status, and entitlement configuration for each case.
3. **Provisioning investigation:** Confirmed Request ID 4 is blocked by duplicate (409) and Request ID 3 is blocked by SoD-01 (409). Both are stuck APPROVED (reject also returns 409).
4. **Root cause analysis:** No control failed in any case. EXC-001 is a duplicate (operational); EXC-002 is a functioning SoD preventive control (policy); EXC-003 is expected time-limited behaviour (none).
5. **SoD assessment:** SoD-01 (Payment Initiator + Payment Approver) verified as implemented and enforced. No conflicting access granted. /reports/sod-violations = 0.
6. **Corrective actions:** Documented closure decisions for all three cases. No API mutation was possible or appropriate on the stuck APPROVED requests. No retries performed (evaluated and rejected).
7. **SLA tracking:** All cases within training SLA targets. No breaches.
8. **Escalation:** None required — all cases resolved or in monitoring within SLA.
9. **Post-resolution verification:** Confirmed no unauthorised access, no duplicate assignments, no active SoD conflicts, audit evidence present.

## Partially completed / open work

- IAM-EXC-2026-003 remains open for monitoring until Sneha Rao's System Administrator access auto-expires at 2026-11-12T19:37:23. Post-expiry verification is pending (cannot be performed within this session due to the ~44-minute expiry window). This is documented as an open monitoring item, not a failure.

## Application limitations documented

1. APPROVED requests that cannot be provisioned cannot be rejected through the API (reject requires REQUESTED status). Such requests remain stuck APPROVED; resolution is by documentation.
2. IdentityGuard does not implement server-side SLA tracking or automatic breach escalation. SLA monitoring is manual.
3. IdentityGuard has no ServiceNow integration. Ticket logging is simulated/manual.
4. Direct role assignment bypasses SoD and was not used.

## Simulated stakeholder actions

All stakeholder communications (informing requesters/managers of duplicate/SoD outcomes) are labelled as simulated and were not executed through any real system. No ServiceNow PDI ticket, email, or external notification was created.

## Evidence collected

13 evidence items across the three exceptions (EXC-001-E01 to EXC-003-E14, with shared files). See Evidence/Evidence-Register.md.

## Classification

This is a fictional training scenario. Asteron Financial Services is a fictional organisation. All simulated stakeholder actions are explicitly labelled. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

SLA targets are the training targets from the Exception Management SOP, labelled as simulated — not regulatory requirements or real commitments.

**Evidence reference:** EXC-003-E14 (closure record for EXC-003); scenario-level closure documented here.
