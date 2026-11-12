# Scenario 4 — Revocation and Modification

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Analyst:** IAM Operations Analyst
**Remediation date:** 12 November 2026 (at cycle completion, 19:09:35 UTC)
**Evidence:** ACR-001-E12 (post-remediation role assignments), ACR-001-E14 (audit trail), ACR-001-E13 (completion)

## Purpose

Record the remediation actions taken for every REVOKE decision, and confirm how the application behaves when a review cycle is completed.

## How IdentityGuard handles REVOKE decisions

Important implementation finding: Recording a REVOKE decision at the decision stage does **not** immediately remove the role. The UserRole assignment is removed only when the review cycle is **completed** (`POST /access-reviews/{cycle_id}/complete`). At completion, IdentityGuard:

1. Verifies all items are decided (no PENDING items).
2. For each REVOKE item, loads the matching UserRole assignment.
3. Applies a revocation guard: if the assignment's `assigned_at` no longer matches the snapshot taken at cycle creation, completion is refused (prevents revoking a role that changed mid-review).
4. Deletes the UserRole assignment and records an `ACCESS_REVOKED` audit event per revocation.
5. Marks the cycle COMPLETED and records an `ACCESS_REVIEW_COMPLETED` event.

This means the decision and the actual access change are separated by the completion step.

## Revocations performed

| Item | User | Role revoked | Reason | Decision recorded | Revocation executed |
|:---|:---|:---|:---|:---|:---|
| 7 | sneha.rao (EMP003) | System Administrator | Privileged emergency access concluded; no current justification for HR user | 19:08:43 UTC | 19:09:35 UTC (at completion) |
| 8 | meera.iyer (EMP004) | Finance Analyst | Stale cross-department access after Finance→HR move | 19:08:43 UTC | 19:09:35 UTC (at completion) |

Both revocations succeeded. The revocation guard did not block either (the `assigned_at` values still matched the cycle-creation snapshots).

## Audit events recorded at completion

| Event ID | Time | Actor | Event type | Target | Reason |
|:---|:---|:---|:---|:---|:---|
| 76 | 19:09:35 | identityguard.admin | ACCESS_REVOKED | sneha.rao | REVOKE reason (System Administrator) |
| 77 | 19:09:35 | identityguard.admin | ACCESS_REVOKED | meera.iyer | REVOKE reason (Finance Analyst) |
| 78 | 19:09:35 | identityguard.admin | ACCESS_REVIEW_COMPLETED | access_review:1 | Cycle completed |

## No MODIFY decisions

No MODIFY decisions were recorded (IdentityGuard does not support a MODIFY decision value). Where modification might have been considered (e.g., swapping one role for another), the change would be processed through the governed access request/provisioning workflow. No such change was needed in this review.

## Verification after remediation

Confirmed in `GET /reports/role-access-assignments` after completion:
- sneha.rao System Administrator: REMOVED (sneha now holds only HR Analyst)
- meera.iyer Finance Analyst: REMOVED (meera now holds only HR Analyst)
- Total active assignments: 16 (down from 18)
- SoD violations: 0
