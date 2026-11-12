# IdentityGuard Reference Data Snapshot

**Case:** `JML-2026-001`  
**Snapshot date:** 12 November 2026  
**Environment:** Local IdentityGuard IAM lab  
**Classification:** Actual lab execution evidence

## 1. Source Endpoints

| Endpoint | Purpose |
|---|---|
| `GET /users` | Retrieve configured user identities |
| `GET /roles` | Retrieve configured IAM roles |
| `GET /reports/identity-inventory` | Retrieve identity inventory and manager relationships |

## 2. Department Reference Data

| Department ID | Department Name |
|---:|---|
| 1 | Finance |
| 2 | HR |
| 3 | IT |
| 4 | Security |

The requested Wealth Management department was not present in the retrieved identity inventory.

## 3. Identity Inventory

| User ID | Employee ID | Username | Full Name | Department | Manager ID | Status |
|---:|---|---|---|---|---:|---|
| 1 | EMP001 | `priya.nair` | Priya Nair | Finance | - | ACTIVE |
| 2 | EMP002 | `rahul.mehta` | Rahul Mehta | Finance | 1 | ACTIVE |
| 3 | EMP003 | `sneha.rao` | Sneha Rao | HR | - | ACTIVE |
| 4 | EMP004 | `meera.iyer` | Meera Iyer | HR | 3 | ACTIVE |
| 5 | EMP005 | `lisa` | Lisa C | IT | - | ACTIVE |
| 6 | EMP006 | `kiran.reddy` | Kiran Reddy | IT | 5 | ACTIVE |
| 7 | EMP007 | `arjun.verma` | Arjun Verma | Security | - | ACTIVE |
| 8 | ADM001 | `identityguard.admin` | IdentityGuard Admin | Security | - | ACTIVE |
| 9 | ADM002 | `identityguard.admin2` | IdentityGuard Admin Two | Security | - | ACTIVE |
| 10 | AUD001 | `auditor` | Security Auditor | Security | - | ACTIVE |
| 11 | REV001 | `reviewer` | Access Reviewer | Security | - | ACTIVE |
| 12 | DEMO001 | `demo.users` | Demo User | Security | - | ACTIVE |

**Total identities returned:** 12

## 4. Manager Relationship Observations

The identity inventory exposes `manager_id` as the manager relationship reference.

| Employee | Department | Manager |
|---|---|---|
| Rahul Mehta | Finance | Priya Nair (`user_id: 1`) |
| Meera Iyer | HR | Sneha Rao (`user_id: 3`) |
| Kiran Reddy | IT | Lisa C (`user_id: 5`) |

For this case, Priya Nair is selected as the proposed reporting manager because she is an existing Finance identity and is already referenced as a manager by another Finance employee.

## 5. Configured Role Catalogue

| Role ID | Role Name | Privileged |
|---:|---|---|
| 1 | SOC Analyst | No |
| 2 | Finance Analyst | No |
| 3 | Finance Manager | No |
| 4 | HR Analyst | No |
| 5 | System Administrator | Yes |
| 6 | Database Administrator | Yes |
| 7 | Payment Initiator | No |
| 8 | Payment Approver | No |
| 9 | IAM Administrator | Yes |
| 10 | Security Auditor | No |
| 11 | Help Desk | No |
| 12 | Access Reviewer | No |
| 13 | PAM Operator | No |

## 6. Validation Notes and Limitations

- No existing identity matching `EMP-1001` or Maya Rao was returned.
- Finance is an existing configured department.
- Priya Nair is an existing Finance identity.
- A manager relationship to Priya is supported by the existing identity inventory structure.
- The role catalogue confirms available roles, not the roles Maya is entitled to receive.
- Individual role assignments have not yet been retrieved for this case.
- The original Wealth Management and Neha Kapoor attributes were not present in the supplied identity inventory.

## 7. Evidence Classification

| Evidence | Classification |
|---|---|
| `GET /users` response | Actual lab execution |
| `GET /roles` response | Actual lab execution |
| `GET /reports/identity-inventory` response | Actual lab execution |
| HR amendment | Simulated upstream event |

This snapshot records the data returned by the local IdentityGuard environment at the time of retrieval. It is not a claim about a production organisation or production identity directory.
