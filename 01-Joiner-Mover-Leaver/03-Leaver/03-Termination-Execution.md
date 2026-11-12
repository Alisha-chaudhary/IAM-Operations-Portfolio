# Leaver - Termination Execution

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Execution Date:** 12 November 2026 (simulated chronological replay)
**Effective Date:** 30 June 2027
**Executed By:** IAM Operations Analyst

## Purpose

Execute the IdentityGuard termination endpoint against Maya's fictional identity only.

## Termination Request

| Field | Value |
|---|---|
| Endpoint | POST /jml/users/12/terminate |
| Permission | IdentityGuard:user.terminate |
| actor | identityguard.admin (IAM Administrator) |
| target user ID | 12 |
| target employee ID | EMP-1001 |

## API Response

Status: 200 OK

```json
{
  "id": 12,
  "employee_id": "EMP-1001",
  "username": "maya.rao",
  "full_name": "Maya Rao",
  "email": "maya.rao@example.test",
  "department_id": 1,
  "manager_id": 1,
  "status": "TERMINATED",
  "terminated_at": "2026-11-12T18:15:20.946679"
}
```

## Termination Behavior (IdentityGuard)

The `terminate_user` endpoint:
- Sets account status to TERMINATED
- Records `terminated_at`
- Expires all active role assignments (sets `expires_at` to termination time)
- Revokes all active PAM checkouts
- Cancels open PAM requests
- Auto-rejects open access requests where the user is requester or target
- Records a USER_TERMINATED audit event

## Limitations

- The endpoint does NOT disable the OpenLDAP account. LDAP disablement, if required, is a separate downstream action and was not performed in this scenario.
- The endpoint does not instantly revoke every existing authentication token or session. IdentityGuard uses short-lived JWTs (15 minutes) with no server-side token denylist. Logout is client-side.
- The account is terminated, not deleted. The account record remains in the database with status TERMINATED.

## Audit Event

| Event ID | Timestamp | Actor | Event Type | Target | Action | Result | Reason |
|---|---|---|---|---|---|---|---|
| 9 | 2026-11-12T18:15:20.950512 | identityguard.admin | USER_TERMINATED | maya.rao | terminate_user | SUCCESS | JML leaver terminated user account and expired active role assignments; revoked 0 PAM checkout(s), cancelled 0 PAM request(s), closed 0 access request(s) |

## Conclusion

Maya's account was terminated successfully. Status is TERMINATED. The USER_TERMINATED audit event was recorded.

**Evidence reference:** JML-001-E21

**Classification:** Actual local lab execution (simulated chronological replay).
