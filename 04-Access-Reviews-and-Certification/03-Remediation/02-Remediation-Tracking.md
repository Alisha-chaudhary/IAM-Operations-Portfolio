# Scenario 4 — Remediation Tracking

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026

## Remediation tracking table

| Item | User | Role | Decision | Decision time | Revocation time | Revocation verified? | Status |
|:---|:---|:---|:---|:---|:---|:---|:---|
| 7 | sneha.rao | System Administrator | REVOKE | 19:08:43 | 19:09:35 | Yes | Complete |
| 8 | meera.iyer | Finance Analyst | REVOKE | 19:08:43 | 19:09:35 | Yes | Complete |

## Watch item (no remediation action)

| Item | User | Role | Decision | Action |
|:---|:---|:---|:---|:---|
| 5 | rahul.mehta | Payment Initiator | RETAIN | Periodic manager re-confirmation recommended (Priya Nair). No revocation performed. |

## Remediation method

All revocations were performed through the IdentityGuard access review completion workflow (`POST /access-reviews/1/complete`), not through direct database modification or direct role removal (`remove_role`). This ensures the revocation is audited as `ACCESS_REVOKED` and tied to the review cycle.

## No bypass of controls

- Direct role assignment/removal (`assign_role`/`remove_role` in `app/iam/service.py`) bypasses SoD and was **not** used.
- The governed review → complete workflow was used, which records audit events and respects the revocation guard.
- No SoD conflict was introduced by the revocations (SoD violations report = 0 after remediation).

## Escalation for remediation

No remediation escalation was required. Both revocations were straightforward and authorised by the review decisions. The reviewer (identityguard.admin) held `access_review.complete`, so completion was authorised.
