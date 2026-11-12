# Standard Access Request - Provisioning Execution

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Requested role:** Finance Manager (role ID 3)
**Request ID:** 1
**Provisioned:** 12 November 2026 18:36:21 UTC
**Provisioner:** identityguard.admin (user 8, IAM Administrator)
**Evidence:** AR-001-E07, AR-001-E08

## Purpose

Execute the supported provisioning endpoint for the approved access request. Do not use direct role assignment to bypass the access-request process.

## Provisioning request

| Field | Value |
|---|---|
| Endpoint | POST /access-requests/1/provision |
| Permission required | IdentityGuard:access.provision |
| Provisioner | identityguard.admin (user 8) |
| Provisioner is not target (user 2) | Yes |
| Role | Finance Manager (non-privileged) |
| Four-eyes required | No (non-privileged role; four-eyes applies only to privileged roles) |
| SoD check at provisioning | Performed automatically; no conflict |

## API response

Status: 200 OK

```json
{
  "id": 1,
  "requester_id": 8,
  "target_user_id": 2,
  "role_id": 3,
  "justification": "Temporary Finance Manager coverage to perform finance-ledger oversight and reporting duties during the Finance Manager absence.",
  "status": "PROVISIONED",
  "decision_by": "identityguard.admin2",
  "decision_reason": "Manager endorsed temporary Finance Manager coverage for finance-ledger oversight during manager absence.",
  "requested_at": "2026-11-12T18:35:53.045577",
  "decided_at": "2026-11-12T18:36:04.279672",
  "provisioned_at": "2026-11-12T18:36:21.906454",
  "expires_at": null
}
```

## Result

Request ID 1 moved from APPROVED to PROVISIONED. The Finance Manager role was assigned to Rahul Mehta via a UserRole record (expires_at = None, standing assignment). The SoD check passed at provisioning. ACCESS_PROVISIONED audit event was recorded.

## Controls observed

- Direct role assignment (app/iam/service.py assign_role) was NOT used. The governed access-request -> approve -> provision workflow was followed.
- SoD was checked at provisioning (evaluate_user_sod).
- The provisioner is not the target user.
- The role is non-privileged, so four-eyes (approver != provisioner) was not required.

**Evidence references:** AR-001-E07, AR-001-E08

**Classification:** Actual lab execution.
