# Mover - Verification

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Verification Date:** 12 November 2026
**Verified By:** IAM Operations Analyst

## Purpose

Verify Maya's department, manager, and role assignments after the mover attempt.

## Verification Results

The mover was not executed because the destination department Investment Operations is not configured in IdentityGuard.

| Check | Expected | Actual | Result |
|---|---|---|---|
| Identity exists | Yes | User ID 12, maya.rao | PASS |
| Department | Investment Operations (blocked) | Finance (ID 1) - unchanged | BLOCKED |
| Manager | Arjun Mehta (proposed) | Priya Nair (user ID 1) - unchanged | BLOCKED |
| Role assignments | To be determined by access review | None assigned | PASS (no change) |
| Access requests | None | None | PASS |

## Conclusion

No changes were made to Maya's identity. She remains in Finance department with manager Priya Nair. The mover is pending resolution of the reference-data dependency (Investment Operations department) and manager validation (Arjun Mehta).

## Outstanding Actions

1. Add Investment Operations department to IdentityGuard reference data (or record as controlled dependency).
2. Validate Arjun Mehta as manager in the live identity inventory.
3. Execute the mover operation through `PATCH /jml/users/12/move`.
4. Perform access review to determine retain/remove/request for the new role.
5. Submit access requests for new entitlements through the governed workflow.

**Evidence reference:** JML-001-E18

**Classification:** Actual local lab verification. Simulated HR mover context.
