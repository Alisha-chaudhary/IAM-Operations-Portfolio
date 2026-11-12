# Scenario 4 — Reviewer Assignment

**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026
**Evidence:** ACR-ALL-E05 (user inventory), ACR-001-E02 (role assignments)

## Purpose

Identify suitable reviewers for each review item, applying the reviewer independence requirement (no user certifies their own access) and the actual IdentityGuard permissions.

## Reviewer independence requirement

The Access Control Policy (§13) and IdentityGuard both require that a user cannot review their own role assignment. IdentityGuard enforces this as `AccessReviewSelfReviewError`: if `reviewer.id == item.user_id`, the decision is rejected.

## IdentityGuard permissions relevant to reviews

| Permission | Held by | Use |
|---|---|---|
| `access_review.create` | identityguard.admin, identityguard.admin2 | Create the review cycle |
| `access_review.view` | identityguard.admin, identityguard.admin2, auditor, reviewer | View cycles and items |
| `access_review.decide` | identityguard.admin, reviewer | Record RETAIN/REVOKE decisions |
| `access_review.correct` | identityguard.admin | Correct decision reasons |
| `access_review.complete` | identityguard.admin | Complete the cycle |

## Reviewer assignment plan

IdentityGuard records the API caller as the technical `reviewer_id` on each decision. It does not auto-assign reviewers by manager. Business judgments are therefore simulated per-department and recorded by the IAM Operations Analyst acting through the IdentityGuard administrator account. All simulated business decisions are labelled as simulated.

To preserve reviewer independence (no self-review), decision-making is split between two identities:

| Decision-maker | IdentityGuard user | Permissions | Reviews |
|---|---|---|---|
| IAM Operations Analyst (technical reviewer) | identityguard.admin (user 8) | create, view, decide, correct, complete | All items EXCEPT identityguard.admin's own IAM Administrator item (user_id=8) |
| Simulated business reviewer (stand-in) | reviewer (user 11) | view, decide | identityguard.admin's IAM Administrator item (user_id=8) only |

**Why this split:** identityguard.admin cannot review their own IAM Administrator assignment (self-review blocked). The `reviewer` identity (user 11) is not user 8, so it can decide that item. Conversely, reviewer cannot review their own Access Reviewer assignment (user_id=11), so identityguard.admin decides that item. Independence is preserved in both directions.

## Simulated business reviewers per item (documented, not enforced by API)

The IdentityGuard API does not capture the business manager as a technical reviewer. The simulated business reviewer is recorded in each decision's justification:

| Item (user) | Department | Simulated business reviewer | Basis |
|---|---|---|---|
| priya.nair items | Finance | Finance department head (simulated) | priya.nair has no manager recorded; simulated reviewer = Finance head |
| rahul.mehta items | Finance | Priya Nair (simulated) | rahul.mehta.manager_id = 1 = priya.nair |
| sneha.rao items | HR | HR department head (simulated) | sneha.rao has no manager recorded |
| meera.iyer items | HR | Sneha Rao (simulated) | meera.iyer.manager_id = 3 = sneha.rao |
| lisa items | IT | IT department head (simulated) | lisa has no manager recorded |
| kiran.reddy items | IT | Lisa C (simulated) | kiran.reddy.manager_id = 5 = lisa |
| arjun.verma item | Security | Security department head (simulated) | arjun.verma has no manager recorded |
| identityguard.admin item | Security | IAM Administrator / security leadership (simulated) | Platform admin; reviewed by stand-in reviewer |
| identityguard.admin2 item | Security | IAM Administrator / security leadership (simulated) | Platform admin |
| auditor item | Security | IAM Administrator / security leadership (simulated) | Governance account |
| reviewer item | Security | IAM Administrator / security leadership (simulated) | Governance account |

## Application limitation documented

IdentityGuard does not enforce an organisational reviewer hierarchy (manager-based assignment). The reviewer is whoever calls the decide API. Business manager input is simulated and recorded in justifications. This limitation is disclosed in the Exceptions and Limitations register.
