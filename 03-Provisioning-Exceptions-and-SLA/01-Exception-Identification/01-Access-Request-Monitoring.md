# Scenario 3 — Access Request Monitoring Record

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Monitored at:** 12 November 2026, 18:52–18:53 UTC
**Monitored by:** IAM Operations Analyst (identityguard.admin)
**Evidence:** EXC-001-E01, EXC-002-E01, EXC-003-E01

## Purpose

Monitor the access request inventory in IdentityGuard and identify requests that represent genuine exceptions, distinguishing them from normal pending requests.

## Access request inventory (as monitored)

| Request ID | Employee | Role | Requested | Status | Approved by | Provisioned at | Exception? |
|---|---|---|---|---|---|---|---|
| 1 | Rahul Mehta (EMP002) | Finance Manager | 18:35:53 | PROVISIONED | identityguard.admin2 | 18:36:21 | No — completed |
| 2 | Sneha Rao (EMP003) | System Administrator | 18:37:37 | PROVISIONED | identityguard.admin2 | 18:38:04 | Yes — time-limited, expiring |
| 3 | Rahul Mehta (EMP002) | Payment Approver | 18:38:22 | APPROVED | identityguard.admin2 | null | Yes — SoD-blocked |
| 4 | Rahul Mehta (EMP002) | Finance Manager | 18:38:46 | APPROVED | identityguard.admin2 | null | Yes — duplicate (already held) |

Source: GET /access-requests, live IdentityGuard API.

## Distinguishing pending requests from genuine exceptions

Request ID 1 is PROVISIONED and complete — not an exception. It is included for context only.

Requests ID 2, 3, and 4 represent genuine exceptions:
- Request ID 2: provisioned but time-limited privileged access approaching expiry (SLA monitoring).
- Request ID 3: APPROVED but provisioning blocked by SoD-01 (provisioning failure).
- Request ID 4: APPROVED but provisioning blocked because the entitlement is already held (duplicate/provisioning failure).

No legitimately pending (REQUESTED) requests were present in the inventory at monitoring time. All four requests are either PROVISIONED or APPROVED. There were no REQUESTED-state requests awaiting approval.

## How exceptions were identified

Exceptions were identified by comparing each access request against:
- The target user's current role assignments (GET /reports/role-access-assignments)
- The SoD violations report (GET /reports/sod-violations)
- The requested role's existence in the role catalogue (GET /roles)
- The request's status and provisioned_at field

A request was flagged as an exception where provisioning could not complete normally (duplicate, SoD-blocked) or where provisioned access was time-limited and approaching expiry.

## Evidence

- EXC-001-E01: Initial access request inventory (Request ID 4 before-state)
- EXC-002-E01: Initial access request inventory (Request ID 3 before-state)
- EXC-003-E01: Initial access request inventory (Request ID 2 before-state)
