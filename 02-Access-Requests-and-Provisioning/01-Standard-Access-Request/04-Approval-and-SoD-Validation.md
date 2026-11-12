# Standard Access Request - Approval and SoD Validation

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Requested role:** Finance Manager (role ID 3)
**Request ID:** 1
**Validated:** 12 November 2026
**Evidence:** AR-001-E05, AR-001-E06

## Purpose

Record the approval decision and the SoD evaluation before provisioning. Confirm the joiner is not approving their own access and that IdentityGuard's single-approver limitation is respected.

## Approval

| Field | Value |
|---|---|
| Endpoint | POST /access-requests/1/approve |
| Permission required | IdentityGuard:access.approve |
| Approver | identityguard.admin2 (user 9, IAM Administrator) |
| Approver is not requester (user 8) | Yes |
| Approver is not target (user 2) | Yes |
| Decision | Approved |
| Reason | Manager endorsed temporary Finance Manager coverage for finance-ledger oversight during manager absence. |
| Decision recorded | 2026-11-12T18:36:04 UTC |
| Request status after approval | APPROVED |

## Manager endorsement (simulated stakeholder)

| Field | Value |
|---|---|
| Endorser | Priya Nair (EMP001, user 1), Rahul's manager |
| Decision | Endorsed |
| Justification | Manager endorsement for temporary Finance Manager coverage per Approval Matrix |
| Classification | SIMULATED stakeholder endorsement |
| Approval reference | SIM-MGR-2026-001 |

Priya Nair has no IdentityGuard platform access permission and cannot use the API. Her endorsement is recorded separately as a simulated stakeholder record, consistent with the Approval Matrix note that additional organisational approval steps are manual.

## Approval chain note

The organisational approval chain requires manager endorsement plus IAM Administrator approval. IdentityGuard supports one approver per access request. The IAM Administrator approval is the system approver (identityguard.admin2). The manager endorsement is recorded separately. IdentityGuard does not natively enforce a multi-stage approval chain. The same person was not used as requester and approver.

## SoD evaluation

| Check | Result |
|---|---|
| Target existing roles | Finance Analyst, Payment Initiator |
| Proposed role | Finance Manager |
| SoD-01 (Payment Initiator + Payment Approver) | No conflict - Finance Manager is not Payment Approver |
| SoD-02 (System Administrator + SOC Analyst) | No conflict |
| SoD-03 (Database Administrator + Security Auditor) | No conflict |
| Implemented rules checked | 3 rules (from /reports/sod-violations) |
| SoD conflict identified | No |

The SoD evaluation confirms no conflict. Provisioning may proceed. The SoD check is performed through the governed provisioning workflow (evaluate_user_sod at provision_access_request), not through direct role assignment.

## Conclusion

Approval obtained (IAM Administrator identityguard.admin2, with simulated manager endorsement by Priya Nair). No SoD conflict. The case is ready for provisioning.

**Evidence references:** AR-001-E05 (approval), AR-001-E06 (SoD evaluation)

**Classification:** Simulated stakeholder endorsement. Actual lab approval and SoD evaluation.
