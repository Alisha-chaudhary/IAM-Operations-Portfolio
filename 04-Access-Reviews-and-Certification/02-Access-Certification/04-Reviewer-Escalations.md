# Scenario 4 — Reviewer Escalations

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026

## Purpose

Document any escalations arising from the access review. An escalation is used when a reviewer cannot make a decision without additional information or approval.

## Escalations required

| Escalation | Related item | Reason | Owner | Status |
|---|---|---|---|---|
| None | — | All 18 items were decided (16 RETAIN, 2 REVOKE). No reviewer lacked sufficient information. | — | Not required |

## Why no escalations were raised

- Every review item had sufficient information to reach a decision: user identity, department, manager, assigned role, entitlement, and business context were all available from the identity inventory and role assignment report.
- No item presented an unresolved SoD conflict (SoD violations report = 0).
- No item required application-owner clarification that could not be resolved from available data.
- Rahul's Payment Initiator (item 5) was flagged as a watch item for periodic re-confirmation, but this does not rise to an escalation: the access is Finance-appropriate and there is no active SoD conflict.

## Application limitation: no ESCALATE decision value

IdentityGuard's review API supports only RETAIN and REVOKE. There is no ESCALATE decision value. Therefore, even if an escalation had been warranted, it could not be recorded as an ESCALATE decision in IdentityGuard. Escalations are tracked manually in this documentation. In this review, none were needed.

## Watch item (not an escalation)

**rahul.mehta — Payment Initiator (item 5):** RETAIN, with a recommendation for periodic manager re-confirmation by Priya Nair. This is a monitoring/watch item, not an escalation. If Priya determines the access is no longer needed, a revocation would be processed through the governed access request/provisioning workflow or a future access review cycle.
