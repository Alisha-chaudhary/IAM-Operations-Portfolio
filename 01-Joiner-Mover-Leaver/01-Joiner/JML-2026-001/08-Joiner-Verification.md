# Joiner - Post-Provisioning Verification

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Verification Date:** 12 November 2026
**Verified By:** IAM Operations Analyst

## Purpose

Verify the resulting identity and access using the supported IdentityGuard reports and endpoints.

## Verification Results

| Check | Expected | Actual | Result |
|---|---|---|---|
| Identity exists | Yes | User ID 12, maya.rao | PASS |
| Employee ID correct | EMP-1001 | EMP-1001 | PASS |
| Full name correct | Maya Rao | Maya Rao | PASS |
| Email correct | maya.rao@example.test | maya.rao@example.test | PASS |
| Department correct | Finance (ID 1) | department_id 1 | PASS |
| Manager correct | Priya Nair (user ID 1) | manager_id 1 | PASS |
| Account status | ACTIVE | ACTIVE | PASS |
| Only approved access present | No IdentityGuard roles | None assigned | PASS |
| No prohibited SoD combination | None | None | PASS |
| Audit evidence exists | USER_CREATED event | Recorded (event ID 4) | PASS |
| No outstanding access request | None | None | PASS |

## Limitations

- Maya's birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) are proposed Asteron training data and are not implemented in IdentityGuard. They were not provisioned through IdentityGuard and are handled as manual/target-application controls.
- IdentityGuard does not support future-dated account activation. The account was created ACTIVE immediately as part of a controlled chronological replay, not scheduled for 17 November 2026.

## Audit Trail

The USER_CREATED audit event (event ID 4) was verified in the audit log. The hash chain was not separately verified at this point but the event is present.

## Conclusion

Maya's identity was verified: ACTIVE, Finance department, manager Priya Nair, correct attributes, no roles assigned, no outstanding access requests, audit evidence present.

**Evidence references:** JML-001-E14

**Classification:** Actual local lab verification.
