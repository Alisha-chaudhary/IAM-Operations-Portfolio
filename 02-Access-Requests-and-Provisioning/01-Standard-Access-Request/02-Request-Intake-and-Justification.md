# Standard Access Request - Request Intake and Justification

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Submitted:** 12 November 2026 18:35:53 UTC
**Submitter:** IAM Operations Analyst (identityguard.admin, user 8) on behalf of Rahul Mehta
**Evidence:** AR-001-E03

## Purpose

Record the access request intake, capture the business justification, and confirm the request is not duplicative.

## Request submitted

| Field | Value |
|---|---|
| Endpoint | POST /access-requests |
| Permission required | IdentityGuard:access.request |
| API requester | identityguard.admin (user 8) |
| Business requester / target | Rahul Mehta (EMP002, user 2) |
| Requested role | Finance Manager (role ID 3) |
| Justification | Temporary Finance Manager coverage to perform finance-ledger oversight and reporting duties during the Finance Manager absence. |
| Expires at | None (standing assignment) |
| Request ID | 1 |
| Status | REQUESTED |

## Duplication check

Rahul Mehta's existing roles were reviewed before submission:
- Finance Analyst (ACTIVE)
- Payment Initiator (ACTIVE)

Finance Manager is NOT already assigned. The request is not duplicative of an existing role assignment.

## API response

Status: 201 Created

```json
{
  "id": 1,
  "requester_id": 8,
  "target_user_id": 2,
  "role_id": 3,
  "justification": "Temporary Finance Manager coverage to perform finance-ledger oversight and reporting duties during the Finance Manager absence.",
  "status": "REQUESTED",
  "decision_by": null,
  "decision_reason": null,
  "requested_at": "2026-11-12T18:35:53.045577",
  "decided_at": null,
  "provisioned_at": null,
  "expires_at": null
}
```

## Conclusion

The access request was accepted and recorded with status REQUESTED. Request ID 1. The business justification is specific and related to Rahul's existing Finance responsibilities. The case is ready for approval.

**Evidence reference:** AR-001-E03

**Classification:** Actual lab execution. Simulated business justification.
