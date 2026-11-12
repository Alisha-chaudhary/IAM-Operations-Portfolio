# Scenario 4 — Review Policy and Criteria

**Source documents:** `00-Governance-Framework/01-Access-Control-Policy.docx`, `00-Governance-Framework/02-RBAC-Matrix.xlsx`, `00-Governance-Framework/03-Entitlement-Catalogue.xlsx`, `00-Governance-Framework/05-SoD-Policy-and-Rules-Register.docx` (IdentityGuard portfolio repository)
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026

## Purpose

Record the governance policy and decision criteria used to evaluate each access review item. All criteria are taken from the actual governance library; nothing is invented.

## Governing policy requirements

The Access Control Policy (Section 13, Periodic access reviews) requires:

| Policy requirement | Source | How applied in this review |
|---|---|---|
| Access reviewed periodically (at least annually, and on role change) | Access Control Policy §13 [Policy requirement] | This Q4 2026 certification cycle is the periodic review |
| Reviewers make retain/revoke decisions with documented reasons | Access Control Policy §13 [Policy requirement] | Every item receives RETAIN or REVOKE with a written justification |
| Users cannot review their own access | Access Control Policy §13 [Policy requirement]; IdentityGuard `AccessReviewSelfReviewError` | Reviewer independence enforced (see Reviewer Assignment) |
| Completed revocations must be actioned | Access Control Policy §13 [Policy requirement] | REVOKE decisions executed at cycle completion; verified after |
| SoD considered during certification | SoD Policy §5 | Reviewer cross-checks items against SoD Rules Register |

## Decision criteria applied to each item

For every review item, the analyst evaluated:

| Criterion | Question |
|---|---|
| User identity | Is the user active and correctly identified? |
| Department | Does the role match the user's current department? |
| Manager | Is the reporting relationship current and valid? |
| Job responsibilities | Is the role appropriate for the user's current responsibilities? |
| Assigned role / entitlement | Is the role configured in IdentityGuard and mapped in the RBAC Matrix? |
| Business justification | Is there a current business need for the access? |
| Still required | Is the access still required, or is it stale (e.g., retained after a department move)? |
| Excessive access | Is the access more than the user needs (least privilege)? |
| SoD conflict | Does the role create or maintain an implemented SoD conflict? |
| Privileged access | Is the role privileged? If so, is the privilege still justified? |
| Termination status | Is the user terminated? (Terminated users are excluded from the active population; their access is already revoked.) |

## Decision values

The IdentityGuard access review API supports exactly two decision values:

| Decision | Meaning |
|---|---|
| RETAIN | Access is appropriate and still required. No change. |
| REVOKE | Access is no longer required or inappropriate. Removed at cycle completion. |

**Application limitation:** The API does not support MODIFY or ESCALATE decision values. Items judged to need modification (remove one role, add another) are handled through the governed access request/provisioning workflow, not through the review API. No ESCALATE decision is recorded in IdentityGuard; escalations are tracked manually in this documentation.

## SoD rules applied (implemented)

Source: `app/governance/sod.py` (SOD_CONFLICT_RULES) and SoD Policy and Rules Register §10.1

| Rule ID | Conflicting roles | Implemented in IdentityGuard |
|---|---|---|
| SoD-01 | Payment Initiator + Payment Approver | Yes — enforced at provisioning |
| SoD-02 | System Administrator + SOC Analyst | Yes — enforced at provisioning |
| SoD-03 | Database Administrator + Security Auditor | Yes — enforced at provisioning |

**Important limitation:** The access review process does not automatically block a RETAIN decision solely because of an SoD finding. The reviewer must identify and address relevant conflicts manually. No active SoD conflicts existed at review time (SoD violations report total_count = 0).

## Exclusions

- **Terminated users:** Maya Rao (EMP-1001) is TERMINATED with zero active role assignments. She is excluded from the active certification population. Her access was already revoked at termination in Scenario 1.
- **Provisioning requests:** Pending access requests (IDs 3 and 4, APPROVED but unprovisioned) are not role assignments and are not review items. They are handled separately under Scenario 3 (exceptions). They are noted here for awareness but not included in the certification population.
