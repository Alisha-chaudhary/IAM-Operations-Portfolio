# Scenario 4 — Final Access Certification Report

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Scenario:** Access Reviews and User Access Certification (Scenario 4)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Analyst:** IAM Operations Analyst
**Report date:** 12 November 2026
**Cycle status:** COMPLETED

## Executive summary

This scenario demonstrated an end-to-end user access certification review in IdentityGuard. Eighteen active role assignments across eleven active users were reviewed. Two roles were revoked (one stale cross-department assignment, one concluded privileged emergency access) and sixteen were retained. The review cycle was completed with full audit evidence. No SoD violations exist.

## Review population

| Category | Count |
|:---|---|
| Active users reviewed | 11 |
| Terminated users excluded | 1 (Maya Rao, EMP-1001 — access already revoked in Scenario 1) |
| Total review items | 18 |
| Standard business users | 7 |
| Privileged accounts | 3 |
| Administrative accounts | 2 |
| Auditor / reviewer accounts | 2 |

## Certification results

| Decision | Count | Percentage |
|:---|---:|---:|
| RETAIN | 16 | 89% |
| REVOKE | 2 | 11% |
| Escalate | 0 | 0% |
| Total | 18 | 100% |

## Revoked access

| User | Role | Reason |
|:---|:---|:---|
| sneha.rao (EMP003) | System Administrator | Privileged emergency access concluded; no current justification for an HR user |
| meera.iyer (EMP004) | Finance Analyst | Stale: retained Finance Analyst after Finance→HR department move |

## Retained access (summary)

Sixteen roles were retained as appropriate for the users' current departments and responsibilities. Notably:
- rahul.mehta retains Payment Initiator (sensitive but Finance-appropriate; no active SoD conflict since no Payment Approver held; flagged for periodic re-confirmation).
- Privileged roles retained for IT/platform administrators where department-appropriate (lisa System Administrator, kiran.reddy Database Administrator, identityguard.admin/admin2 IAM Administrator).

## SoD assessment

No active SoD conflicts exist (SoD violations report total_count = 0 before and after remediation). The reviewer cross-checked every item against the implemented SoD rules (SoD-01: Payment Initiator + Payment Approver; SoD-02: System Administrator + SOC Analyst; SoD-03: Database Administrator + Security Auditor). Rahul's Payment Initiator + his pending-but-unprovisioned Payment Approver request (Scenario 3) is a potential future conflict, not an active one.

## Reviewer independence

No user reviewed their own assignment:
- identityguard.admin (user 8) decided 17 items (all except their own IAM Administrator item).
- reviewer (user 11) decided identityguard.admin's IAM Administrator item (user_id=8).
- reviewer did not review their own Access Reviewer item (decided by identityguard.admin).

## Application limitations documented

1. IdentityGuard's review API supports only RETAIN and REVOKE — no MODIFY or ESCALATE decision values. Escalations and modifications are handled outside the API (documented manually or via the access request/provisioning workflow).
2. Recording a REVOKE decision does not immediately remove access; removal occurs at cycle completion.
3. IdentityGuard does not auto-assign reviewers by manager; the technical reviewer is the API caller. Business judgments were simulated per-department and recorded in justifications.
4. No user can review their own assignment (enforced as `AccessReviewSelfReviewError`).

## Evidence collected

Evidence items ACR-001-E01 to ACR-001-E14 (plus supporting ACR-ALL files). See `Evidence/Evidence-Register.md`.

## Classification

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder decisions are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only. Review dates are fictional training dates.
