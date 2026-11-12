# Scenario 2 - Identity and Role Reference

**Source:** Live IdentityGuard local environment (`http://127.0.0.1:8000`), queried 12 November 2026
**Classification:** Actual lab execution evidence

## Live users (re-validated)

| User ID | Employee ID | Username | Full name | Department | Status | Manager ID |
|---:|---|---|---|---|---|---|
| 1 | EMP001 | priya.nair | Priya Nair | Finance | ACTIVE | - |
| 2 | EMP002 | rahul.mehta | Rahul Mehta | Finance | ACTIVE | 1 |
| 3 | EMP003 | sneha.rao | Sneha Rao | HR | ACTIVE | - |
| 4 | EMP004 | meera.iyer | Meera Iyer | HR | ACTIVE | 3 |
| 5 | EMP005 | lisa | Lisa C | IT | ACTIVE | - |
| 6 | EMP006 | kiran.reddy | Kiran Reddy | IT | ACTIVE | 5 |
| 7 | EMP007 | arjun.verma | Arjun Verma | Security | ACTIVE | - |
| 8 | ADM001 | identityguard.admin | IdentityGuard Admin | Security | ACTIVE | - |
| 9 | ADM002 | identityguard.admin2 | IdentityGuard Admin Two | Security | ACTIVE | - |
| 10 | AUD001 | auditor | Security Auditor | Security | ACTIVE | - |
| 11 | REV001 | reviewer | Access Reviewer | Security | ACTIVE | - |
| 12 | EMP-1001 | maya.rao | Maya Rao | Finance | TERMINATED | 1 |

Rahul Mehta's manager relationship was re-validated against the live database: manager_id 1 = Priya Nair. Validated.

## Departments

| Department ID | Department |
|---|---|
| 1 | Finance |
| 2 | HR |
| 3 | IT |
| 4 | Security |

## Roles (live catalogue)

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
| 9 | Vault Secret Access | No | Read access to synthetic Vault secrets |
| 10 | IAM Administrator | Yes | Administrates IdentityGuard users, roles, and access |
| 11 | Security Auditor | No | Reviews IdentityGuard audit information |
| 12 | Help Desk | No | Approved user and role support operations |
| 13 | Access Reviewer | No | Reviews and decides access review items |
| 14 | PAM Operator | No | Can request and check out approved privileged access |

## Privileged roles

System Administrator, Database Administrator and IAM Administrator are privileged. Privileged role assignment requires `IdentityGuard:role.assign_privileged` and is subject to four-eyes control at provisioning (approver != provisioner).

## Existing role assignments relevant to the test cases

- Rahul Mehta (user 2): Finance Analyst, Payment Initiator (both ACTIVE)
- Priya Nair (user 1): Finance Manager, Payment Approver (both ACTIVE)
- Sneha Rao (user 3): HR Analyst (ACTIVE)
- identityguard.admin (user 8): IAM Administrator (ACTIVE, privileged)
- identityguard.admin2 (user 9): IAM Administrator (ACTIVE, privileged)

## Access requests before scenario

No outstanding access requests existed before this scenario began.

## Source

`GET /users`, `GET /roles`, `GET /reports/role-access-assignments`, `GET /reports/sod-violations`, live IdentityGuard API.
