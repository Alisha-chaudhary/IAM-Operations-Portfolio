# Scenario 4 — Review Population

**Source:** IdentityGuard API (`GET /users`, `GET /reports/identity-inventory`, `GET /reports/role-access-assignments`, `GET /access-requests`), captured 12 November 2026 19:05 UTC
**Analyst:** IAM Operations Analyst
**Evidence:** ACR-001-E01, ACR-001-E02, ACR-ALL-E05, ACR-ALL-E06

## Purpose

Extract the current identity inventory and role assignment data, categorise the review population, and explain inclusions and exclusions.

## Identity inventory (all users)

| User ID | Employee ID | Username | Full name | Department | Manager ID | Status | Role count |
|---:|---|---|---|---|---|---|---:|
| 1 | EMP001 | priya.nair | Priya Nair | Finance | — | ACTIVE | 2 |
| 2 | EMP002 | rahul.mehta | Rahul Mehta | Finance | 1 | ACTIVE | 3 |
| 3 | EMP003 | sneha.rao | Sneha Rao | HR | — | ACTIVE | 2 |
| 4 | EMP004 | meera.iyer | Meera Iyer | HR | 3 | ACTIVE | 2 |
| 5 | EMP005 | lisa | Lisa C | IT | — | ACTIVE | 2 |
| 6 | EMP006 | kiran.reddy | Kiran Reddy | IT | 5 | ACTIVE | 2 |
| 7 | EMP007 | arjun.verma | Arjun Verma | Security | — | ACTIVE | 1 |
| 8 | ADM001 | identityguard.admin | IdentityGuard Admin | Security | — | ACTIVE | 1 |
| 9 | ADM002 | identityguard.admin2 | IdentityGuard Admin Two | Security | — | ACTIVE | 1 |
| 10 | AUD001 | auditor | Security Auditor | Security | — | ACTIVE | 1 |
| 11 | REV001 | reviewer | Access Reviewer | Security | — | ACTIVE | 1 |
| 12 | EMP-1001 | maya.rao | Maya Rao | Finance | 1 | TERMINATED | 0 |

Total users: 12. Active: 11. Terminated: 1 (Maya Rao).

## Review population categorisation

### Included in active certification population (11 users, 18 assignments)

| Category | Users | Rationale |
|---|---|---|
| Standard business users | priya.nair (Finance), rahul.mehta (Finance), sneha.rao (HR), meera.iyer (HR), lisa (IT), kiran.reddy (IT), arjun.verma (Security) | Business users with role assignments requiring certification |
| Privileged accounts | sneha.rao (System Administrator, time-limited), lisa (System Administrator), kiran.reddy (Database Administrator) | Privileged roles require heightened scrutiny |
| Administrative accounts | identityguard.admin, identityguard.admin2 (IAM Administrator) | Platform administration accounts; reviewed with care |
| Auditor / reviewer accounts | auditor (Security Auditor), reviewer (Access Reviewer) | Governance accounts; reviewed for appropriateness |

### Excluded from active certification population

| User | Reason |
|---|---|
| Maya Rao (EMP-1001, maya.rao) | Status TERMINATED (2026-11-12 18:15 UTC). Zero active role assignments. Access already revoked at termination in Scenario 1. Excluded per procedure (terminated identities are not part of the active-user certification population). |

## Role assignment inventory (18 active assignments)

| User | Role | Privileged | Department match? | Notes |
|---|---|---|---|---|
| priya.nair | Finance Manager | No | Yes (Finance) | Finance oversight, finance-ledger:read |
| priya.nair | Payment Approver | No | Yes (Finance) | Payment approval; no Payment Initiator → no SoD-01 conflict |
| rahul.mehta | Finance Analyst | No | Yes (Finance) | Reads general ledger |
| rahul.mehta | Finance Manager | No | Yes (Finance) | Overlaps with Finance Analyst (both finance-ledger:read) but adds oversight; not excessive |
| rahul.mehta | Payment Initiator | No | Yes (Finance) | Can create payments. Sensitive. No Payment Approver held → no active SoD-01 conflict. Flagged for periodic manager re-confirmation. |
| sneha.rao | HR Analyst | No | Yes (HR) | Maintains employee records |
| sneha.rao | System Administrator | Yes | No (HR user) | Privileged emergency access, time-limited (expires 2026-11-12 19:37:23). No current business justification for an HR user. → REVOKE |
| meera.iyer | Finance Analyst | No | No (HR user) | Stale: user moved Finance → HR but retained Finance Analyst (noted in seed as stale-access case). Cross-department access no longer required. → REVOKE |
| meera.iyer | HR Analyst | No | Yes (HR) | Appropriate for HR role |
| lisa | System Administrator | Yes | Yes (IT) | IT administrator; privileged but department-appropriate |
| lisa | PAM Operator | No | Yes (IT) | Privileged access management; appropriate for IT |
| kiran.reddy | Database Administrator | Yes | Yes (IT) | Database administration; privileged but department-appropriate |
| kiran.reddy | PAM Operator | No | Yes (IT) | Appropriate for IT |
| arjun.verma | SOC Analyst | No | Yes (Security) | Security monitoring; appropriate |
| identityguard.admin | IAM Administrator | Yes | Yes (Security) | Platform administration; required |
| identityguard.admin2 | IAM Administrator | Yes | Yes (Security) | Platform administration; required |
| auditor | Security Auditor | No | Yes (Security) | Audit support; appropriate |
| reviewer | Access Reviewer | No | Yes (Security) | Access certification; appropriate |

## Findings identified during population preparation

1. **meera.iyer — Finance Analyst (stale cross-department access):** Meera is in HR but retains Finance Analyst from a prior Finance→HR move. This is the classic stale-access case identified in the IdentityGuard seed data. Access is no longer required for her HR responsibilities. Decision: REVOKE.

2. **sneha.rao — System Administrator (privileged, time-limited):** Sneha is an HR user holding a privileged System Administrator role. It was granted as time-limited emergency access in Scenario 2 (expires 19:37:23 UTC). The emergency access need has concluded. Decision: REVOKE (remove privileged access as soon as it is no longer needed, rather than waiting for auto-expiry).

3. **rahul.mehta — Payment Initiator (sensitive, watch item):** Rahul can create payments. He does not hold Payment Approver, so there is no active SoD-01 conflict. However, he also holds Finance Manager (oversight). The combination is sensitive but not an SoD violation. Decision: RETAIN, with a recommendation for periodic manager re-confirmation. Noted as a watch item.

4. **Pending access requests not in scope:** Request ID 3 (rahul → Payment Approver, APPROVED but SoD-blocked) and Request ID 4 (rahul → Finance Manager, APPROVED but duplicate) are not role assignments and are not review items. They are tracked under Scenario 3. Noted for awareness: if Request ID 3 were ever provisioned, it would create an SoD-01 conflict with Rahul's existing Payment Initiator.

## SoD check at population preparation

The SoD violations report returned total_count = 0 (no active conflicts). Reviewer cross-checked each item against the SoD Rules Register; no item creates an implemented SoD conflict. Rahul's Payment Initiator + the pending (unprovisioned) Payment Approver request is a potential future conflict, not an active one.
