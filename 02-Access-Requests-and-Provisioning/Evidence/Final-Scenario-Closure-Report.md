# Final Scenario Closure Report

**Case references:** AR-2026-001, AR-2026-002, AR-2026-003, AR-2026-004
**Scenario:** Access Requests and Provisioning (Scenario 2)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Closure date:** 12 November 2026
**Closed by:** IAM Operations Analyst

## Scenario summary

Scenario 2 demonstrates the operational handling of employee access requests through the governed IdentityGuard access-request, approval and provisioning workflow. Four cases were executed: one standard access request, one privileged access request with four-eyes control, one SoD conflict test, and one exception/failure analysis.

## Case outcome summary

| Case | Focus | Request | Approve | Provision | Outcome |
|---|---|---|---|---|---|
| AR-2026-001 | Standard non-privileged access (Rahul -> Finance Manager) | 201 REQUESTED | 200 APPROVED (admin2) | 200 PROVISIONED (admin) | Completed - access granted |
| AR-2026-002 | Privileged access with four-eyes (sneha -> System Administrator, time-limited) | 201 REQUESTED | 200 APPROVED (admin2) | 200 PROVISIONED (admin, four-eyes) | Completed - time-limited access granted |
| AR-2026-003 | SoD conflict (Rahul -> Payment Approver, conflicts with Payment Initiator) | 201 REQUESTED | 200 APPROVED (admin2) | 409 BLOCKED | Completed - conflict blocked, no access granted |
| AR-2026-004 | Exception handling (missing justification, invalid target, inactive target, duplicate) | 422/404/422 | - | 409 dup | Completed - all exceptions handled as expected |

## Completed work

### AR-2026-001: Standard access request
Rahul Mehta (EMP002) requested Finance Manager (finance-ledger:read). Request ID 1 was submitted, approved by IAM Administrator identityguard.admin2 (with simulated manager endorsement by Priya Nair), and provisioned by identityguard.admin. SoD evaluation found no conflict. Post-provisioning verification confirmed Rahul holds Finance Manager in addition to Finance Analyst and Payment Initiator. Audit trail shows REQUESTED -> APPROVED -> PROVISIONED.

### AR-2026-002: Privileged access with four-eyes
Sneha Rao (EMP003) requested System Administrator (privileged), time-limited to one hour. Request ID 2 was approved by identityguard.admin2 and provisioned by identityguard.admin (approver != provisioner, four-eyes satisfied). The assignment expires at 2026-11-12T19:37:23 UTC, avoiding permanent privileged access for an ordinary user. Verification confirmed the time-limited role and 0 SoD violations.

### AR-2026-003: SoD conflict test
Rahul Mehta (who holds Payment Initiator) requested Payment Approver. Request ID 3 was approved but provisioning was blocked with 409 (SoD-01 conflict). A SOD_VIOLATION audit event (ID 36, DENIED) was recorded. Rahul's access is unchanged; Payment Approver was not granted.

### AR-2026-004: Exception handling
Four exception conditions tested safely: missing justification (422), invalid target identity (404), inactive target account / terminated user (422), duplicate role request (provisioning blocked 409 "User already has this role"). All controls behaved as expected.

## Evidence collected

13 evidence items collected (AR-001-E01 to AR-004-E01, with some IDs combined). See Evidence/Evidence-Register.md.

## Application limitations documented

1. Single approver per access request (no native multi-stage chain)
2. Manager cannot use the IdentityGuard API (no platform permission)
3. Only two IAM Administrator identities exist (requester == provisioner for privileged case)
4. Time-limited privileged access used to avoid permanent privileged access
5. Direct role assignment bypasses SoD (control gap managed by procedure)
6. `/users` endpoint does not expose manager_id

## Simulated stakeholder actions

The following actions were simulated for the fictional training scenario and are NOT real organisational activity:
- Manager endorsement by Priya Nair for AR-2026-001 (recorded separately because she cannot use the API)
- Business justifications for all requests (fictional training content)

## Actual local lab operations performed

All operations executed against the local IdentityGuard API (`http://127.0.0.1:8000`):
- User and role reads (`GET /users`, `GET /roles`)
- Role assignment report (`GET /reports/role-access-assignments`)
- SoD violations report (`GET /reports/sod-violations`)
- Access request submission (`POST /access-requests`) x4
- Access request approval (`POST /access-requests/{id}/approve`) x3
- Access request provisioning (`POST /access-requests/{id}/provision`) x5 (including 2 blocks)
- Audit events read (`GET /audit/events`)
- Direct database query for manager relationship validation

## Classification

This is a fictional training scenario. Asteron Financial Services is a fictional organisation. All simulated stakeholder actions are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

**Evidence reference:** Final-Scenario-Closure-Report.md
