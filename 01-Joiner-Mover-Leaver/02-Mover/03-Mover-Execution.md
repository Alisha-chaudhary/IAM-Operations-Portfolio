# Mover - Execution

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Execution Date:** 12 November 2026 (simulated chronological replay)
**Effective Date:** 1 February 2027
**Executed By:** IAM Operations Analyst

## Purpose

Execute the supported mover operation in the local IdentityGuard lab.

## Move Attempt

The mover endpoint was called with the destination department Investment Operations. The department is not configured in IdentityGuard (configured departments: Finance 1, HR 2, IT 3, Security 4).

### API Request

| Field | Value |
|---|---|
| Endpoint | PATCH /jml/users/12/move |
| Permission | IdentityGuard:user.move |
| actor | identityguard.admin (IAM Administrator) |
| department_id | 99 (Investment Operations - does not exist) |

### API Response

Status: 404 Not Found

```json
{
  "detail": "Department 99 does not exist."
}
```

## Execution Outcome

**Status:** BLOCKED - not executed

The move could not be executed because the destination department Investment Operations is not configured in IdentityGuard. No department was created to force the move.

## Recorded Blocker

| Blocker | Detail | Impact |
|---|---|---|
| Destination department not configured | Investment Operations not in IdentityGuard reference data | Move cannot proceed; Maya remains in Finance |
| New manager not validated | Arjun Mehta not in live identity inventory | Manager relationship cannot be set |
| No role auto-migration | Mover endpoint does not auto-add/remove roles | Even if move succeeded, access review would be needed separately |

## Operational Impact

- Maya remains in Finance department with manager Priya Nair.
- No IdentityGuard role changes were made.
- No access requests were created for the mover role.
- The mover remains pending until the reference-data dependency is resolved.

## Next Action

Record the Investment Operations department as a controlled reference-data dependency. Once the department is added to IdentityGuard and the new manager is validated, the move can be executed through the `PATCH /jml/users/{user_id}/move` endpoint, followed by an access review to determine retain/remove/request decisions.

**Evidence reference:** JML-001-E17 (blocked execution evidence)

**Classification:** Actual local lab attempt (blocked). Simulated HR mover context.
