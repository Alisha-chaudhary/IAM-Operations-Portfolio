# Exceptions and Limitations Register

**Scenario:** Access Reviews and User Access Certification (Scenario 4)
**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Compiled:** 12 November 2026
**Compiled by:** IAM Operations Analyst

## Formal exceptions raised

No formal access exceptions (with compensating controls and expiry) were raised in this scenario. All review items were decided as RETAIN or REVOKE based on the evidence.

## Technical limitations and application behaviour

| # | Limitation | Component | Impact | Control decision |
|:--|:---|:---|:---|:---|
| L1 | Review API supports only RETAIN and REVOKE — no MODIFY or ESCALATE decision values | `POST /access-reviews/{id}/decisions` (decision must be in {RETAIN, REVOKE}) | Escalations and modifications cannot be recorded as decisions in IdentityGuard | Watch items and escalation needs tracked manually in documentation; changes processed via governed access request/provisioning workflow |
| L2 | REVOKE decision does not immediately remove access; removal occurs at cycle completion | `complete_access_review_cycle` (deletes UserRole at completion) | Decision and actual access change are separated by the completion step | Cycle was completed immediately after all decisions; revocations verified after |
| L3 | Revocation guard: completion refused if an assignment's assigned_at changed since cycle snapshot | `complete_access_review_cycle` | Could block completion if a role changed mid-review | No assignments changed during this review; guard passed |
| L4 | No auto-assignment of reviewers by manager; technical reviewer = API caller | Access review API | Business reviewer hierarchy not enforced by application | Reviewer identity split between identityguard.admin and reviewer (user 11) to preserve self-review independence; business judgments simulated per-department |
| L5 | Cannot selectively include/exclude items at cycle creation; all active assignments snapshotted | `create_access_review_cycle` | Cycle population fixed to all active assignments | Terminated users naturally excluded (zero active assignments); no manual exclusions needed |
| L6 | A user cannot review their own assignment (`AccessReviewSelfReviewError`) | `record_access_review_decision` | identityguard.admin could not review their own IAM Administrator item | reviewer (user 11) decided that item; reviewer's own item decided by identityguard.admin |
| L7 | No separate post-completion verification endpoint; verification via re-reading reports | N/A | Post-remediation verification done by re-reading role-assignment report and audit trail | Accepted as the supported verification approach |

## Items explicitly NOT treated as exceptions

- Rahul's Payment Initiator (item 5): retained as Finance-appropriate with no active SoD conflict; flagged as a watch item for periodic re-confirmation. Not an exception, not an escalation.
- Pending access requests (Scenario 3 IDs 3 and 4): not role assignments, not review items; tracked under Scenario 3.

## No manufacturing of findings

No findings were manufactured against users. All REVOKE decisions (sneha System Administrator, meera Finance Analyst) were backed by specific evidence (stale cross-department access; concluded privileged emergency access). All RETAIN decisions were backed by department/role appropriateness.

## Classification

All simulated stakeholder decisions and fictional review dates are labelled as simulated/training. This is not a real organisational event.
