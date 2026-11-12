# Scenario 4 — Post-Remediation Verification

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Verified at:** 12 November 2026 19:10:42 UTC
**Verifier:** IAM Operations Analyst
**Evidence:** ACR-001-E12 (post-remediation role assignments), ACR-001-E09 (SoD post-remediation), ACR-001-E14 (audit trail)

## Purpose

Verify the remediation results: confirm revoked roles are no longer active, retained roles are unchanged, no unauthorised access remains, and SoD requirements are satisfied.

## Role assignments after remediation (16 active, down from 18)

| User | Role | Status |
|---|---|---|
| priya.nair | Finance Manager | ACTIVE |
| priya.nair | Payment Approver | ACTIVE |
| rahul.mehta | Finance Analyst | ACTIVE |
| rahul.mehta | Finance Manager | ACTIVE |
| rahul.mehta | Payment Initiator | ACTIVE |
| sneha.rao | HR Analyst | ACTIVE |
| meera.iyer | HR Analyst | ACTIVE |
| lisa | System Administrator | ACTIVE |
| lisa | PAM Operator | ACTIVE |
| kiran.reddy | Database Administrator | ACTIVE |
| kiran.reddy | PAM Operator | ACTIVE |
| arjun.verma | SOC Analyst | ACTIVE |
| identityguard.admin | IAM Administrator | ACTIVE |
| identityguard.admin2 | IAM Administrator | ACTIVE |
| auditor | Security Auditor | ACTIVE |
| reviewer | Access Reviewer | ACTIVE |

## Verification results

| Check | Expected | Actual | Result |
|:---|:---|:---|:---|
| sneha.rao System Administrator revoked | Not present | Removed | PASS |
| meera.iyer Finance Analyst revoked | Not present | Removed | PASS |
| sneha.rao retains HR Analyst | Present | Present | PASS |
| meera.iyer retains HR Analyst | Present | Present | PASS |
| All other 14 roles retained | Present | Present | PASS |
| No additional roles removed | 16 active | 16 active | PASS |
| SoD violations | 0 | 0 | PASS |
| Audit evidence for revocations | ACCESS_REVOKED ×2 | Events 76, 77 | PASS |
| Audit evidence for completion | ACCESS_REVIEW_COMPLETED | Event 78 | PASS |
| Cycle status | COMPLETED | COMPLETED | PASS |

## Conclusion

Post-remediation verification passed. Both revoked roles (sneha.rao System Administrator, meera.iyer Finance Analyst) are no longer active. All other roles are unchanged. No unauthorised access remains. SoD requirements are satisfied (zero active conflicts). The review cycle is COMPLETED with full audit evidence.

## Limitations documented

- IdentityGuard does not support a separate "post-completion" verification endpoint; verification was performed by re-reading the role-assignment report and audit trail, which is the supported approach.
- The revoked roles are deleted (not expired), consistent with IdentityGuard's access review revocation behaviour. The historical assignment remains in the audit trail.
