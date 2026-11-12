# Scenario 3 — Provisioning Investigation

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002
**Investigated at:** 12 November 2026, 18:52–18:53 UTC
**Investigator:** IAM Operations Analyst

## Purpose

Investigate the two approved-but-unprovisioned requests (Request ID 4 and Request ID 3) to determine why provisioning could not complete, whether the requests are eligible for provisioning, and what corrective action is appropriate.

## Investigation — IAM-EXC-2026-001 (Request ID 4: Finance Manager duplicate)

| Investigation question | Finding | Evidence |
|---|---|---|
| Was the request approved? | Yes — APPROVED by identityguard.admin2 at 18:39:17 | GET /access-requests |
| Was the approver authorised? | Yes — identityguard.admin2 holds IdentityGuard:access.approve | Role catalogue |
| Does the role exist? | Yes — Finance Manager (role 3) | GET /roles |
| Does the target identity exist and is it active? | Yes — Rahul Mehta (EMP002, user 2), ACTIVE | GET /users |
| Is the entitlement configured? | Yes — finance-ledger:read via Finance Manager role | Entitlement Catalogue (ENT-007) |
| Is the request eligible for provisioning? | No — Rahul already holds Finance Manager (assigned via Request ID 1 at 18:36:21) | Role-access-assignments report |
| Does provisioning return an error? | Yes — 409 "User already has this role" | POST /access-requests/4/provision (re-attempted) |
| Is the failure recorded in audit? | ACCESS_REQUESTED and ACCESS_APPROVED events exist; no ACCESS_PROVISIONED event | GET /audit/events |
| Root cause | Duplicate entitlement — access already assigned | — |

## Investigation — IAM-EXC-2026-002 (Request ID 3: Payment Approver SoD-blocked)

| Investigation question | Finding | Evidence |
|---|---|---|
| Was the request approved? | Yes — APPROVED by identityguard.admin2 at 18:38:29 | GET /access-requests |
| Was the approver authorised? | Yes — identityguard.admin2 holds IdentityGuard:access.approve | Role catalogue |
| Does the role exist? | Yes — Payment Approver (role 8) | GET /roles |
| Does the target identity exist and is it active? | Yes — Rahul Mehta (EMP002, user 2), ACTIVE | GET /users |
| Is the entitlement configured? | Yes — payments-system:approve via Payment Approver role | Entitlement Catalogue (ENT-011) |
| Is the request eligible for provisioning? | No — SoD-01 blocks Payment Approver + Payment Initiator | GET /reports/sod-violations, role assignments |
| Does provisioning return an error? | Yes — 409 "Provisioning blocked by SoD policy" | POST /access-requests/3/provision (re-attempted) |
| Is the failure recorded in audit? | Yes — SOD_VIOLATION events (IDs 36 and 48), result DENIED | GET /audit/events |
| Root cause | SoD-01 conflict — Rahul already holds Payment Initiator | Role assignments + SOD_CONFLICT_RULES |

## Common observation: stuck APPROVED state

Both Request ID 4 and Request ID 3 are APPROVED and cannot be resolved through the API:
- Provisioning is blocked (duplicate / SoD)
- Rejection is blocked — the reject endpoint requires REQUESTED status; APPROVED requests return 409 "Access request has already been decided"

This is an application limitation, not a data corruption. The requests remain APPROVED and unprovisioned. Resolution is by operational documentation and closure decision, not API mutation.

## Investigation conclusion

- EXC-001: Provisioning cannot complete because the entitlement is already held. No further provisioning is required or possible. The request is moot.
- EXC-002: Provisioning cannot complete because of an SoD conflict. Conflicting access must not be granted. The request is blocked by a functioning preventive control.

No data was corrupted, no code was modified, and no unrelated users or access were affected.

## Evidence

- EXC-001-E05: Provisioning investigation (Request ID 4 before/after state)
- EXC-002-E05: Provisioning investigation (Request ID 3 before/after state, provisioning 409, reject 409)
