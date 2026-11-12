# Joiner - RBAC and Entitlement Mapping

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Department:** Finance
**Manager:** Priya Nair
**Designation:** Relationship Manager
**Mapping Date:** 12 November 2026
**Mapped By:** IAM Operations Analyst

## Purpose

Determine Maya's birth-right access using the actual RBAC Matrix and Entitlement Catalogue from the IdentityGuard governance library. Do not infer role assignments from a job title alone.

## Source Documents

- RBAC Matrix: `00-Governance-Framework/02-RBAC-Matrix.xlsx` (IdentityGuard portfolio repo)
- Entitlement Catalogue: `00-Governance-Framework/03-Entitlement-Catalogue.xlsx` (IdentityGuard portfolio repo)

## Maya's Approved Scenario Attributes

| Attribute | Value |
|---|---|
| Employee ID | EMP-1001 |
| Name | Maya Rao |
| Department | Finance |
| Designation | Relationship Manager |
| Manager | Priya Nair |

## IdentityGuard Role Assessment

Maya's job title is "Relationship Manager" in the Wealth Management department (amended to Finance). IdentityGuard does not contain a "Relationship Manager" role. The RBAC Matrix does not map a Wealth Management or Finance "Relationship Manager" business role to an IdentityGuard technical role.

No IdentityGuard role was assigned based on the job title alone.

## Birth-Right Access Determination

Per the RBAC Matrix (Section A note) and Entitlement Catalogue, Maya's joiner birth-right access is defined as proposed Asteron training data:

| Entitlement | Application | Role | Entitlement | Implementation Status |
|---|---|---|---|---|
| CRM: Relationship Manager | CRM (proposed) | CRM: Relationship Manager | View and manage own client portfolio | No - proposed Asteron training data |
| PMS: Portfolio Viewer | PMS (proposed) | PMS: Portfolio Viewer | View client portfolio holdings | No - proposed Asteron training data |

## IdentityGuard-Configured Access

No IdentityGuard roles or entitlements were identified for Maya's birth-right access. The birth-right entitlements are proposed Asteron business application entitlements (CRM, PMS) and are NOT IdentityGuard records. They are not implemented in IdentityGuard.

## Target-Application / Manual Control

Because the CRM and PMS entitlements are not implemented in IdentityGuard, they are treated as target-application or manual controls. Provisioning to CRM and PMS would occur outside IdentityGuard (for example, recorded in ServiceNow PDI or Excel) and is not executed through the IdentityGuard access request/provision workflow.

No new role, entitlement, application, or department was created in IdentityGuard to make the scenario work.

## Approval Mapping

Per the Approval Matrix (Joiner birth-right access row):
- Hiring manager endorsement required
- IAM Administrator approval required
- Joiner cannot approve their own access
- SoD checked at provisioning

IdentityGuard supports one approver per access request. The hiring manager endorsement (Neha Kapoor originally, now simulated as Priya Nair after amendment) and IAM Administrator approval are recorded as separate simulated stakeholder approvals.

## SoD Assessment

The implemented IdentityGuard SoD rules are:
- SoD-01: Payment Initiator + Payment Approver
- SoD-02: System Administrator + SOC Analyst
- SoD-03: Database Administrator + Security Auditor

Maya's proposed birth-right entitlements (CRM, PMS) do not trigger any implemented IdentityGuard SoD rule. The proposed SoD-T-01 rule (Trade Analyst + Trade Approver) is proposed Asteron training data and is not implemented.

## Conclusion

Maya's birth-right access consists of proposed Asteron training-data entitlements in CRM and PMS. These are not implemented in IdentityGuard and are handled as manual/target-application controls. No IdentityGuard role assignment was made for birth-right access.

**Evidence reference:** JML-001-E07

**Classification:** Policy analysis. Simulated stakeholder context for manager endorsement.
