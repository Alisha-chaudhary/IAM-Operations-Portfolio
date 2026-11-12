# Joiner - Approval and SoD Validation

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Validation Date:** 12 November 2026
**Validated By:** IAM Operations Analyst

## Purpose

Record the approvals required for Maya's joiner access and the SoD validation performed before provisioning. IdentityGuard supports one approver per access request; additional organisational approval steps are recorded as separate simulated stakeholder approvals.

## Required Approvals

Per the Approval Matrix (Joiner birth-right access row):
1. Hiring manager endorsement
2. IAM Administrator approval

The joiner cannot approve their own access. Maya Rao (EMP-1001) did not approve any access.

## Approval Records

### Approval 1 - Hiring Manager Endorsement (Simulated)

| Field | Value |
|---|---|
| Approver | Priya Nair (simulated hiring manager, Finance) |
| Employee ID | EMP001 |
| Username | priya.nair |
| Decision | Endorsed |
| Justification | Manager endorsement for joiner birth-right access per Approval Matrix |
| Timestamp | Simulated - 12 November 2026 |
| Approval Reference | SIM-HR-MGR-2026-001 |

**Classification:** SIMULATED stakeholder approval. Not an IdentityGuard system approval.

### Approval 2 - IAM Administrator Approval (Simulated)

| Field | Value |
|---|---|
| Approver | IAM Administrator (IdentityGuard platform) |
| Username | identityguard.admin |
| Decision | Approved |
| Justification | IAM Administrator approval for joiner access provisioning |
| Timestamp | Simulated - 12 November 2026 |
| Approval Reference | SIM-IAM-APP-2026-001 |

**Classification:** SIMULATED stakeholder approval. Not an IdentityGuard system approval.

## Approval Chain Note

The organisational approval chain requires two approvals (hiring manager + IAM Administrator). IdentityGuard supports one approver per access request. The second approval is recorded separately as a simulated stakeholder approval. IdentityGuard does not natively enforce a multi-stage approval chain.

The same person was not used as both requester and approver. The IAM Operations Analyst performed the requester/provisioner role; approvals were recorded separately.

## SoD Validation

### Applicable Implemented SoD Rules

| Rule ID | Conflicting Roles | Applies to Maya? |
|---|---|---|
| SoD-01 | Payment Initiator + Payment Approver | No |
| SoD-02 | System Administrator + SOC Analyst | No |
| SoD-03 | Database Administrator + Security Auditor | No |

Maya's proposed birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) are proposed Asteron training data and do not trigger any implemented IdentityGuard SoD rule.

### SoD Check Result

No SoD conflict was identified. No conflicting access was provisioned.

The SoD check is performed through the IdentityGuard access-request and provision workflow. Direct role assignment does not itself perform the SoD check. The governed workflow was used.

## Exceptions

No SoD exception was required. No conflict was identified.

## Conclusion

Both required approvals were obtained as separate simulated stakeholder records. No SoD conflict exists. The case is ready to proceed to provisioning through the governed access-request and provisioning workflow.

**Evidence references:** JML-001-E08, JML-001-E09, JML-001-E10

**Classification:** Simulated stakeholder approvals. Policy analysis for SoD.
