# Scenario 4 — Review Decisions

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026

## Purpose

Record the reasoning behind each review decision, grouped by decision outcome. All decisions are evidence-backed and tied to the user's current department, responsibilities, and the RBAC Matrix / Entitlement Catalogue.

## RETAIN decisions (16 items)

### Finance department
- **priya.nair — Finance Manager (item 1):** RETAIN. Priya is the Finance department head. Finance Manager provides finance-ledger:read oversight required for her role. Department-appropriate.
- **priya.nair — Payment Approver (item 2):** RETAIN. Payment approval is consistent with her Finance Manager responsibilities. She does not hold Payment Initiator, so there is no active SoD-01 conflict.
- **rahul.mehta — Finance Analyst (item 3):** RETAIN. Rahul is in Finance; reading the general ledger is part of his responsibilities.
- **rahul.mehta — Finance Manager (item 4):** RETAIN. Finance oversight role. Overlaps with Finance Analyst (both grant finance-ledger:read) but adds oversight responsibility; not excessive.
- **rahul.mehta — Payment Initiator (item 5):** RETAIN with watch item. Payment creation access is sensitive but Finance-appropriate. Rahul does not hold Payment Approver, so there is no active SoD-01 conflict. Flagged for periodic manager re-confirmation.

### HR department
- **sneha.rao — HR Analyst (item 6):** RETAIN. Maintains employee records; appropriate for HR.
- **meera.iyer — HR Analyst (item 9):** RETAIN. Appropriate for her HR role.

### IT department
- **lisa — System Administrator (item 10):** RETAIN. Privileged but department-appropriate for IT administration. Periodic re-confirmation recommended given privilege level.
- **lisa — PAM Operator (item 11):** RETAIN. Appropriate for IT privileged-access management.
- **kiran.reddy — Database Administrator (item 12):** RETAIN. Privileged but department-appropriate for database administration.
- **kiran.reddy — PAM Operator (item 13):** RETAIN. Appropriate for IT.

### Security department
- **arjun.verma — SOC Analyst (item 14):** RETAIN. Security monitoring; appropriate.
- **identityguard.admin2 — IAM Administrator (item 16):** RETAIN. Required for platform administration. Privileged; controlled via four-eyes in the access request/provisioning workflow.
- **auditor — Security Auditor (item 17):** RETAIN. Governance/audit function; read-only oversight.
- **reviewer — Access Reviewer (item 18):** RETAIN. Access certification function; appropriate.

### Platform administration (reviewed with independence)
- **identityguard.admin — IAM Administrator (item 15):** RETAIN. Required for platform administration. Reviewed by reviewer (user 11) to preserve independence, since identityguard.admin cannot self-review.

## REVOKE decisions (2 items)

- **sneha.rao — System Administrator (item 7):** REVOKE. Privileged emergency access granted for a production incident (Scenario 2), time-limited (expires 2026-11-12 19:37:23). The emergency need has concluded; there is no current business justification for an HR user to hold privileged server administration. Removed promptly rather than waiting for auto-expiry.
- **meera.iyer — Finance Analyst (item 8):** REVOKE. Meera moved from Finance to HR but retained Finance Analyst (stale cross-department access, identified in the IdentityGuard seed data). No longer required for her HR responsibilities. Least privilege.

## Why no MODIFY / ESCALATE decisions

IdentityGuard's review API supports only RETAIN and REVOKE. There is no MODIFY or ESCALATE decision value at the API level. Where an item warranted closer scrutiny (rahul's Payment Initiator), it was recorded as RETAIN with a watch-item note; any change would be processed through the governed access request/provisioning workflow, not through the review API.

## Evidence

- ACR-001-E07 (items 1-18): individual decision records
- ACR-001-E14: audit trail (ACCESS_REVIEW_DECISION_RECORDED events)
- ACR-001-E01/E02: pre-review inventory
