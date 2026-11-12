# Leaver - Post-Termination Verification

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Verification Date:** 12 November 2026
**Verified By:** IAM Operations Analyst

## Purpose

Verify the termination results using the supported IdentityGuard reports and endpoints.

## Verification Results

| Check | Expected | Actual | Result |
|---|---|---|---|
| Account status | TERMINATED | TERMINATED | PASS |
| terminated_at populated | Yes | 2026-11-12T18:15:20.946679 | PASS |
| Role assignments expired | Yes | None active | PASS |
| Outstanding access requests cancelled | Yes | None | PASS |
| PAM checkouts revoked | Yes | 0 revoked (none active) | PASS |
| PAM requests cancelled | Yes | 0 cancelled (none open) | PASS |
| Audit evidence | USER_TERMINATED event | Recorded (event ID 9) | PASS |

## Session / Token Limitation

IdentityGuard does not implement server-side token revocation. JWTs are short-lived (15 minutes) with no server-side denylist. Logout is client-side. Termination does not instantly revoke all existing tokens or sessions. This limitation is documented.

## LDAP Limitation

The IdentityGuard termination endpoint does not disable the OpenLDAP account. LDAP disablement was not performed. This is an outstanding downstream action. The IdentityGuard result alone does not establish LDAP deactivation.

## Remaining Access in Other Systems

IdentityGuard manages only its own local store. Connected or separate systems (CRM, PMS, Trade Ops, CCM, HRMS) are proposed Asteron training applications and are not integrated with IdentityGuard. Any access in those systems would require separate revocation outside IdentityGuard.

## Conclusion

Maya's IdentityGuard account is TERMINATED. Role assignments are expired. No outstanding access requests remain. Audit evidence exists. LDAP disablement and session/token revocation limitations are documented.

**Evidence reference:** JML-001-E22

**Classification:** Actual local lab verification.
