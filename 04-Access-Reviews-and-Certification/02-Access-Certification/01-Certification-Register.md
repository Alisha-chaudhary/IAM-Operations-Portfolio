# Scenario 4 — Certification Register

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Cycle status:** COMPLETED
**Decisions recorded:** 18 (16 RETAIN, 2 REVOKE)
**Analyst:** IAM Operations Analyst
**Decision date:** 12 November 2026
**Evidence:** ACR-001-E07 (items 1-18), ACR-001-E13 (completion), ACR-001-E14 (audit trail)

## Certification decision register

| Item | User | Employee ID | Role | Privileged | Decision | Technical reviewer | Simulated business reviewer | Justification summary |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| 1 | priya.nair | EMP001 | Finance Manager | No | RETAIN | identityguard.admin | Finance dept head (simulated) | Finance oversight role, department-appropriate |
| 2 | priya.nair | EMP001 | Payment Approver | No | RETAIN | identityguard.admin | Finance dept head (simulated) | No Payment Initiator → no SoD-01 conflict |
| 3 | rahul.mehta | EMP002 | Finance Analyst | No | RETAIN | identityguard.admin | Priya Nair (manager, simulated) | Reads general ledger, Finance dept |
| 4 | rahul.mehta | EMP002 | Finance Manager | No | RETAIN | identityguard.admin | Priya Nair (manager, simulated) | Oversight role; overlaps Analyst but adds oversight |
| 5 | rahul.mehta | EMP002 | Payment Initiator | No | RETAIN | identityguard.admin | Priya Nair (manager, simulated) | Sensitive; watch item for re-confirmation; no active SoD conflict |
| 6 | sneha.rao | EMP003 | HR Analyst | No | RETAIN | identityguard.admin | HR dept head (simulated) | Maintains employee records, HR dept |
| 7 | sneha.rao | EMP003 | System Administrator | Yes | REVOKE | identityguard.admin | HR dept head (simulated) | Privileged emergency access concluded; no current justification |
| 8 | meera.iyer | EMP004 | Finance Analyst | No | REVOKE | identityguard.admin | Sneha Rao (manager, simulated) | Stale: HR dept, retained Finance Analyst after Finance→HR move |
| 9 | meera.iyer | EMP004 | HR Analyst | No | RETAIN | identityguard.admin | Sneha Rao (manager, simulated) | Appropriate for HR role |
| 10 | lisa | EMP005 | System Administrator | Yes | RETAIN | identityguard.admin | IT dept head (simulated) | IT admin, privileged but department-appropriate |
| 11 | lisa | EMP005 | PAM Operator | No | RETAIN | identityguard.admin | IT dept head (simulated) | Appropriate for IT |
| 12 | kiran.reddy | EMP006 | Database Administrator | Yes | RETAIN | identityguard.admin | Lisa C (manager, simulated) | DB admin, privileged but department-appropriate |
| 13 | kiran.reddy | EMP006 | PAM Operator | No | RETAIN | identityguard.admin | Lisa C (manager, simulated) | Appropriate for IT |
| 14 | arjun.verma | EMP007 | SOC Analyst | No | RETAIN | identityguard.admin | Security dept head (simulated) | Security monitoring, appropriate |
| 15 | identityguard.admin | ADM001 | IAM Administrator | Yes | RETAIN | reviewer (user 11) | IAM / security leadership (simulated) | Platform admin; reviewed by stand-in for independence |
| 16 | identityguard.admin2 | ADM002 | IAM Administrator | Yes | RETAIN | identityguard.admin | IAM / security leadership (simulated) | Platform admin, required |
| 17 | auditor | AUD001 | Security Auditor | No | RETAIN | identityguard.admin | IAM / security leadership (simulated) | Governance/audit, read-only oversight |
| 18 | reviewer | REV001 | Access Reviewer | No | RETAIN | identityguard.admin | IAM / security leadership (simulated) | Access certification function |

## Decision summary

| Decision | Count | Items |
|---|---|---|
| RETAIN | 16 | 1, 2, 3, 4, 5, 6, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18 |
| REVOKE | 2 | 7 (sneha System Administrator), 8 (meera Finance Analyst) |
| Escalate | 0 | — |
| Total | 18 | — |

## Reviewer independence verification

| Item | User being reviewed | Technical reviewer | Reviewer == user? | Independence preserved? |
|:---|:---|:---|:---|:---|
| 1-14 | priya, rahul, sneha, meera, lisa, kiran, arjun | identityguard.admin (user 8) | No | Yes |
| 15 | identityguard.admin (user 8) | reviewer (user 11) | No | Yes |
| 16-18 | admin2, auditor, reviewer | identityguard.admin (user 8) | No | Yes |

No user reviewed their own assignment. identityguard.admin did not review item 15 (their own IAM Administrator assignment); reviewer (user 11) decided it. reviewer did not review item 18 (their own Access Reviewer assignment); identityguard.admin decided it.

## Application limitation documented

IdentityGuard's review API supports only RETAIN and REVOKE decisions. MODIFY and ESCALATE are not supported decision values. Where a reviewer might have wanted to escalate (e.g., rahul's sensitive Payment Initiator), the decision was recorded as RETAIN with a watch-item note, and the escalation need is tracked manually in this documentation rather than in IdentityGuard.
