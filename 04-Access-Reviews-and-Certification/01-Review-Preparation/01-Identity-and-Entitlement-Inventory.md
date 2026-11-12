# Scenario 4 — Identity and Entitlement Inventory

**Source:** IdentityGuard API (`GET /users`, `GET /reports/identity-inventory`, `GET /reports/role-access-assignments`, `GET /roles`), captured 12 November 2026 19:05 UTC
**Analyst:** IAM Operations Analyst
**Evidence:** ACR-001-E01, ACR-001-E02, ACR-ALL-E05, ACR-ALL-E07

## Purpose

Extract and document the identity inventory, role catalogue, and role assignments that form the basis of the access review population.

## Identity inventory (12 users)

| User ID | Employee ID | Username | Full name | Department | Manager ID | Status | Roles |
|---:|---|---|---|---|---|---|---|
| 1 | EMP001 | priya.nair | Priya Nair | Finance | — | ACTIVE | Finance Manager, Payment Approver |
| 2 | EMP002 | rahul.mehta | Rahul Mehta | Finance | 1 | ACTIVE | Finance Analyst, Finance Manager, Payment Initiator |
| 3 | EMP003 | sneha.rao | Sneha Rao | HR | — | ACTIVE | HR Analyst, System Administrator |
| 4 | EMP004 | meera.iyer | Meera Iyer | HR | 3 | ACTIVE | Finance Analyst, HR Analyst |
| 5 | EMP005 | lisa | Lisa C | IT | — | ACTIVE | System Administrator, PAM Operator |
| 6 | EMP006 | kiran.reddy | Kiran Reddy | IT | 5 | ACTIVE | Database Administrator, PAM Operator |
| 7 | EMP007 | arjun.verma | Arjun Verma | Security | — | ACTIVE | SOC Analyst |
| 8 | ADM001 | identityguard.admin | IdentityGuard Admin | Security | — | ACTIVE | IAM Administrator |
| 9 | ADM002 | identityguard.admin2 | IdentityGuard Admin Two | Security | — | ACTIVE | IAM Administrator |
| 10 | AUD001 | auditor | Security Auditor | Security | — | ACTIVE | Security Auditor |
| 11 | REV001 | reviewer | Access Reviewer | Security | — | ACTIVE | Access Reviewer |
| 12 | EMP-1001 | maya.rao | Maya Rao | Finance | 1 | TERMINATED | (none — 0 assignments) |

## Role catalogue (14 roles)

| Role ID | Role name | Privileged | Description |
|---:|---|---|---|
| 1 | SOC Analyst | No | Monitors and triages security alerts |
| 2 | Finance Analyst | No | Reads the general ledger |
| 3 | Finance Manager | No | Finance oversight and reporting |
| 4 | HR Analyst | No | Maintains employee records |
| 5 | System Administrator | Yes | Administers production servers |
| 6 | Database Administrator | Yes | Administers production databases |
| 7 | Payment Initiator | No | Can create payments |
| 8 | Payment Approver | No | Can approve payments |
| 9 | Vault Secret Access | No | Read access to synthetic Vault secrets (not assigned) |
| 10 | IAM Administrator | Yes | Administrates IdentityGuard users, roles, and access |
| 11 | Security Auditor | No | Reviews IdentityGuard audit information |
| 12 | Help Desk | No | Approved user and role support operations (not assigned) |
| 13 | Access Reviewer | No | Reviews and decides access review items |
| 14 | PAM Operator | No | Can request and check out approved privileged access |

## Active role assignments (18, pre-review)

Full detail in evidence file ACR-001-E02. Summary by user:

| User | Assignments | Privileged? |
|:---|:---|---|
| priya.nair | Finance Manager, Payment Approver | No |
| rahul.mehta | Finance Analyst, Finance Manager, Payment Initiator | No |
| sneha.rao | HR Analyst, System Administrator | Yes (System Administrator) |
| meera.iyer | Finance Analyst, HR Analyst | No |
| lisa | System Administrator, PAM Operator | Yes (System Administrator) |
| kiran.reddy | Database Administrator, PAM Operator | Yes (Database Administrator) |
| arjun.verma | SOC Analyst | No |
| identityguard.admin | IAM Administrator | Yes |
| identityguard.admin2 | IAM Administrator | Yes |
| auditor | Security Auditor | No |
| reviewer | Access Reviewer | No |

## Terminated user (excluded from review population)

Maya Rao (EMP-1001, maya.rao): TERMINATED 2026-11-12 18:15 UTC, zero active role assignments. Access revoked at termination in Scenario 1. Excluded from the active certification population.

## Entitlements referenced

Per the Entitlement Catalogue (`03-Entitlement-Catalogue.xlsx`), the assigned roles map to these permissions:
- Finance Manager / Finance Analyst: finance-ledger:read
- Payment Approver: payments-system:approve
- Payment Initiator: payments-system:initiate
- HR Analyst: hr-records:read, hr-records:update
- System Administrator: PROD-LINUX-01:admin, PROD-WIN-01:admin (privileged)
- Database Administrator: PROD-DB-01:admin (privileged)
- SOC Analyst: siem-console:read, siem-console:triage
- IAM Administrator: 21 IdentityGuard:* platform permissions (privileged)
- Security Auditor: IdentityGuard:user.read, audit.read, access_review.view, reports.read
- Access Reviewer: IdentityGuard:access_review.view, access_review.decide
- PAM Operator: IdentityGuard:pam.request, IdentityGuard:pam.checkout
