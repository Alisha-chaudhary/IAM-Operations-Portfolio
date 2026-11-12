# Privileged Access Request - Provisioning and Verification

**Case:** AR-2026-002
**Employee:** Sneha Rao (EMP003)
**Requested role:** System Administrator (role ID 5, privileged)
**Request ID:** 2
**Provisioned:** 12 November 2026 18:38:04 UTC
**Provisioner:** identityguard.admin (user 8, IAM Administrator)
**Evidence:** AR-002-E03, AR-002-E04

## Purpose

Execute four-eyes provisioning of the privileged access request (approver != provisioner) and verify the resulting time-limited role assignment.

## Provisioning request

| Field | Value |
|---|---|
| Endpoint | POST /access-requests/2/provision |
| Permission required | IdentityGuard:access.provision + role.assign_privileged |
| Provisioner | identityguard.admin (user 8) |
| Approver was | identityguard.admin2 (user 9) |
| Approver != provisioner | Yes (four-eyes satisfied) |
| Provisioner is not target (user 3) | Yes |
| Role | System Administrator (privileged) |
| Time-limited | expires_at 2026-11-12T19:37:23 |

## API response

Status: 200 OK

```json
{
  "id": 2,
  "requester_id": 8,
  "target_user_id": 3,
  "role_id": 5,
  "justification": "Temporary System Administrator access for emergency server investigation during production incident, time-limited to one hour.",
  "status": "PROVISIONED",
  "decision_by": "identityguard.admin2",
  "decision_reason": "Approved time-limited System Administrator access for emergency incident investigation.",
  "requested_at": "2026-11-12T18:37:37.701890",
  "decided_at": "2026-11-12T18:37:56.952264",
  "provisioned_at": "2026-11-12T18:38:04.515812",
  "expires_at": "2026-11-12T19:37:23"
}
```

## Verification results

| Check | Expected | Actual | Result |
|---|---|---|---|
| Request status | PROVISIONED | PROVISIONED | PASS |
| Provisioner != approver | identityguard.admin != identityguard.admin2 | Yes | PASS |
| Provisioner != target | user 8 != user 3 | Yes | PASS |
| Role assigned | System Administrator | System Administrator (ACTIVE) | PASS |
| Time-limited (expires_at) | Set | 2026-11-12T19:37:23 | PASS |
| SoD status | No conflict | 0 SoD violations | PASS |
| Approver did not provision | provisioner=admin, approver=admin2 | Confirmed | PASS |

## Sneha Rao's role assignments after provisioning

| Role | Status | Expires at | Privileged |
|---|---|---|---|
| HR Analyst | ACTIVE | None | No |
| System Administrator | ACTIVE | 2026-11-12T19:37:23 | Yes |

## Conclusion

Privileged access provisioned with four-eyes control (approver admin2 != provisioner admin). The System Administrator assignment is time-limited to one hour, avoiding permanent privileged access for an ordinary user. No SoD conflict. The privileged assignment will expire automatically.

**Evidence references:** AR-002-E03, AR-002-E04

**Classification:** Actual lab execution. Time-limited privileged access.
