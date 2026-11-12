# SoD Conflict Handling - Validation and Outcome

**Case:** AR-2026-003
**Employee:** Rahul Mehta (EMP002)
**Request ID:** 3
**Validated:** 12 November 2026
**Evidence:** AR-003-E01, AR-003-E02, AR-003-E03, AR-003-E04

## Purpose

Execute the SoD conflict test end to end and record the outcome. Confirm the provisioning block and the audit evidence.

## Test execution

| Step | Action | Actor | Result |
|---|---|---|---|
| 1 | Submit access request (Rahul -> Payment Approver) | identityguard.admin (user 8) | 201 Created, REQUESTED |
| 2 | Approve request | identityguard.admin2 (user 9) | 200 OK, APPROVED |
| 3 | Attempt provisioning | identityguard.admin (user 8) | 409 Conflict - BLOCKED |

## Provisioning block evidence

Status: 409 Conflict

```json
{
  "detail": "Provisioning blocked by SoD policy: User holds incompatible roles: Payment Approver and Payment Initiator"
}
```

The provisioning was blocked by `evaluate_user_sod` at `provision_access_request`. A `SOD_VIOLATION` audit event was recorded with result DENIED.

## SOD_VIOLATION audit event

| Event ID | Timestamp | Actor | Event Type | Target | Result | Reason |
|---:|---|---|---|---|---|---|
| 36 | 2026-11-12T18:38:29 | identityguard.admin | SOD_VIOLATION | rahul.mehta | DENIED | User holds incompatible roles: Payment Approver and Payment Initiator |

## Post-test state verification

Rahul Mehta's role assignments after the blocked test:
- Finance Analyst (ACTIVE, pre-existing)
- Finance Manager (ACTIVE, from AR-2026-001)
- Payment Initiator (ACTIVE, pre-existing)

Payment Approver is NOT present. The SoD conflict prevented the conflicting grant. Rahul's access is unchanged except for the pre-existing roles.

## SoD violations report

The `/reports/sod-violations` report shows total_count: 0 (no active SoD conflicts among users, because the conflicting grant was never made).

## Conclusion

The SoD preventive control works as designed. Provisioning of Payment Approver for Rahul (who holds Payment Initiator) was blocked by SoD-01. No conflicting access was granted. A SOD_VIOLATION audit event provides evidence of the block. The control decision is: do not provision conflicting access; no exception was requested.

**Classification:** Actual lab test. SoD-01 is an implemented IdentityGuard rule.
