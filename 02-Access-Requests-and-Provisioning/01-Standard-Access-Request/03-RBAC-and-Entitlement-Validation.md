# Standard Access Request - RBAC and Entitlement Validation

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Requested role:** Finance Manager (role ID 3)
**Validated:** 12 November 2026
**Validator:** IAM Operations Analyst
**Evidence:** AR-001-E04 (governance mapping analysis)

## Purpose

Validate the requested Finance Manager role against the RBAC Matrix and Entitlement Catalogue. Confirm the role is configured in IdentityGuard, appropriate for the employee's business role, and not already assigned.

## RBAC Matrix validation

Source: `00-Governance-Framework/02-RBAC-Matrix.xlsx` (IdentityGuard portfolio repo)

| Attribute | Value |
|---|---|
| Department | Finance |
| Business job role | Finance Manager (aligned to Rahul's Finance department) |
| Application | IdentityGuard (platform) |
| Application role | Finance Manager |
| Permission or entitlement | finance-ledger:read |
| Access level | Read-only |
| Access classification | Confidential |
| Approval requirement | IAM Administrator approval |
| SoD restrictions | None |
| Supported by IdentityGuard | Yes - implemented (IdentityGuard) |

## Entitlement Catalogue validation

Source: `00-Governance-Framework/03-Entitlement-Catalogue.xlsx`

| Field | Value |
|---|---|
| Entitlement ID | ENT-007 |
| Application or resource | IdentityGuard (platform) |
| Entitlement name | Finance Manager - finance-ledger:read |
| Description | Read the general ledger (oversight) |
| Associated permission | finance-ledger:read |
| Associated application role | Finance Manager |
| Required approval | IAM Administrator approval |
| SoD restrictions | None |
| Provisioning method | Access request -> approve -> provision (IdentityGuard) |
| IdentityGuard implementation status | Yes - implemented (IdentityGuard) |

## Role configured in IdentityGuard

The Finance Manager role (role ID 3) is present in the live role catalogue:
- Name: Finance Manager
- Privileged: No
- Permissions: finance-ledger:read

## Appropriateness for employee's business role

Rahul Mehta is a Finance department employee (Relationship Manager / Finance Analyst). Finance Manager (finance-ledger:read oversight) is appropriate for his Finance responsibilities. The role is non-privileged and is not already assigned to Rahul (he holds Finance Analyst and Payment Initiator).

## Approval requirement

Per the RBAC Matrix and Entitlement Catalogue, Finance Manager requires IAM Administrator approval. Per the Approval Matrix (standard role request row), a single approval is required; the business manager or IAM Administrator may approve. Because Priya Nair (the business manager) has no IdentityGuard platform access permission, she cannot use the API. Her endorsement is recorded as a simulated stakeholder record, and the IdentityGuard system approver is an IAM Administrator (identityguard.admin2). This is consistent with the single-approver limitation: IdentityGuard enforces one approver per request; the manager endorsement is a separate organisational step.

## Conclusion

The Finance Manager role is validated: configured in IdentityGuard, appropriate for Rahul's Finance role, not already assigned, governed by the RBAC Matrix and Entitlement Catalogue, and requires IAM Administrator approval. Ready for approval.

**Classification:** Policy analysis. Simulated stakeholder context for manager endorsement.
