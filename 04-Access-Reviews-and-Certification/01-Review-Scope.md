# Scenario 4 — Access Reviews and User Access Certification: Review Scope

**Case reference:** ACR-001
**Review cycle name:** Asteron Q4 2026 User Access Certification
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab (`http://127.0.0.1:8000`)
**Review date:** 12 November 2026
**Analyst:** IAM Operations Analyst

## Purpose

This scenario demonstrates an end-to-end user access certification review in IdentityGuard. The objective is to establish whether existing users still require their assigned roles based on their current job responsibilities, department, reporting relationship, and business requirements — and to remediate (retain or revoke) access accordingly.

## Review scope

| Scope element | Detail |
|---|---|
| Review cycle | Asteron Q4 2026 User Access Certification |
| Review period | Q4 2026 (October–December 2026), fictional training dates |
| Review date | 12 November 2026 |
| Review population | All active users with active (non-expired) role assignments in IdentityGuard |
| Excluded from population | Terminated users (Maya Rao, EMP-1001 — account terminated in Scenario 1, zero active assignments) |
| Review type | Periodic user access certification |
| Governing policy | Access Control Policy (Section 13 — Periodic access reviews) |
| Application capability | IdentityGuard access review cycles with RETAIN/REVOKE decisions |

## What this scenario demonstrates

1. Review cycle preparation and population selection
2. Identity inventory and role assignment validation
3. Reviewer identification with independence (no self-review)
4. Review cycle creation via the IdentityGuard API
5. Access certification decisions (RETAIN/REVOKE) with evidence-backed justifications
6. SoD and excessive/inappropriate access findings
7. Remediation (revocation) at cycle completion
8. Post-remediation verification
9. Review completion and audit trail

## Classification

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder decisions are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

Review dates and periods used in this scenario are fictional training dates.
