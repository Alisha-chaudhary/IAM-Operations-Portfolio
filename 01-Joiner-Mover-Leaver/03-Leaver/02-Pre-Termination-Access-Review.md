# Leaver - Pre-Termination Access Review

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Review Date:** 12 November 2026 (simulated chronological replay)
**Reviewed By:** IAM Operations Analyst

## Purpose

Record Maya's complete access inventory before termination, as required by the leaver lifecycle.

## Pre-Termination Access Inventory

| Access Type | Item | Status |
|---|---|---|
| IdentityGuard account | User ID 12, maya.rao, EMP-1001 | ACTIVE |
| Department | Finance (ID 1) | Assigned |
| Manager | Priya Nair (user ID 1) | Assigned |
| IdentityGuard roles | None | None assigned |
| Outstanding access requests | None | None |
| PAM checkouts | None | None |

## Audit Events Before Termination

| Event ID | Timestamp | Actor | Event Type | Target | Action | Result | Reason |
|---|---|---|---|---|---|---|---|
| 4 | 2026-11-12T17:57:17.504936 | identityguard.admin | USER_CREATED | maya.rao | create_user | SUCCESS | JML joiner created user account |

## Outstanding Requests

No outstanding access requests exist for Maya (requester or target).

## Termination Authorization

HR authorisation verified (simulated). The IdentityGuard `terminate_user` endpoint requires:
- `IdentityGuard:user.terminate` permission
- Actor cannot be the target user (self-termination blocked)
- Cannot terminate the last active privileged administrator

Maya is not a privileged administrator, so the LastAdministratorError does not apply.

## Conclusion

Maya's pre-termination access inventory is recorded. She has no IdentityGuard roles, no outstanding access requests, and no PAM checkouts. The account is ACTIVE and ready for termination.

**Evidence reference:** JML-001-E20

**Classification:** Actual lab pre-termination inventory. Simulated HR leaver context.
