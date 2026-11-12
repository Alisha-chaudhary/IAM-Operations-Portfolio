# Scenario 3 — Initial Triage Report

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Triaged at:** 12 November 2026, 18:52–18:53 UTC
**Triaged by:** IAM Operations Analyst

## Purpose

Perform initial validation of each exception: confirm identity, request completeness, entitlement validity, and whether the case is a genuine exception or normal processing.

## Triage — IAM-EXC-2026-001 (Request ID 4)

| Validation check | Result |
|---|---|
| Identity exists and is ACTIVE | Rahul Mehta (EMP002, user 2), ACTIVE — PASS |
| Request exists and is APPROVED | Request ID 4, APPROVED — PASS |
| Requested role exists in catalogue | Finance Manager (role 3), exists — PASS |
| Target user already holds the role | Yes — Finance Manager assigned via Request ID 1 — DUPLICATE |
| Provisioning possible | No — returns 409 "User already has this role" |
| Rejection possible | No — returns 409 "Access request has already been decided" (APPROVED state) |
| Triage outcome | Genuine exception — approved-but-unprovisioned duplicate, stuck |

## Triage — IAM-EXC-2026-002 (Request ID 3)

| Validation check | Result |
|---|---|
| Identity exists and is ACTIVE | Rahul Mehta (EMP002, user 2), ACTIVE — PASS |
| Request exists and is APPROVED | Request ID 3, APPROVED — PASS |
| Requested role exists in catalogue | Payment Approver (role 8), exists — PASS |
| SoD conflict applies | Yes — Rahul holds Payment Initiator; Payment Approver + Payment Initiator = SoD-01 |
| Provisioning possible | No — returns 409 SoD block |
| Rejection possible | No — returns 409 "Access request has already been decided" |
| Triage outcome | Genuine exception — SoD-blocked provisioning, stuck |

## Triage — IAM-EXC-2026-003 (Request ID 2)

| Validation check | Result |
|---|---|
| Identity exists and is ACTIVE | Sneha Rao (EMP003, user 3), ACTIVE — PASS |
| Request exists and is PROVISIONED | Request ID 2, PROVISIONED — PASS |
| Requested role exists in catalogue | System Administrator (role 5), exists, privileged — PASS |
| Access is time-limited | Yes — expires_at 2026-11-12T19:37:23 |
| Time remaining at triage | ~44 minutes |
| Renewal required | No — emergency access, time-bound by design |
| Triage outcome | Genuine exception — expiring privileged access, SLA monitoring |

## Triage conclusion

All three cases are genuine exceptions requiring operational handling. None are normal pending (REQUESTED) requests. Two (EXC-001, EXC-002) are APPROVED but stuck because IdentityGuard cannot provision (duplicate/SoD) and cannot reject (already decided). One (EXC-003) is provisioned but time-limited and self-expiring.

No ServiceNow PDI integration exists in IdentityGuard; ticket logging is simulated/manual per the Exception Management SOP.

## Evidence

- EXC-001-E02, EXC-002-E02, EXC-003-E02: Exception identification
- EXC-001-E03, EXC-002-E03, EXC-003-E03: Initial triage
