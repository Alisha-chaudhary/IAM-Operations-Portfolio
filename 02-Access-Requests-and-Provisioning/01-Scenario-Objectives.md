# Scenario 2 - Access Requests and Provisioning: Objectives

**Case references:** AR-2026-001, AR-2026-002, AR-2026-003
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab

## Purpose

This scenario demonstrates the operational handling of employee access requests through the governed IdentityGuard access-request, approval and provisioning workflow. The objective is to demonstrate that access is not granted merely because someone requests it.

An IAM Operations Analyst must validate the request, understand the business requirement, confirm the requested access is appropriate, verify approvals, check segregation of duties, execute provisioning through the authorised workflow and verify the resulting access.

## What this scenario demonstrates

- Access request intake and validation
- Requester and target identity verification
- Business justification review
- Role and entitlement validation against the RBAC Matrix and Entitlement Catalogue
- Approval routing and approval evidence
- Segregation of Duties (SoD) validation at provisioning
- Provisioning through the authorised workflow (no direct role assignment)
- Post-provisioning verification
- Audit trail review
- Request closure
- Exception and failed provisioning handling
- Privileged access with four-eyes control (approver != provisioner)
- SoD conflict blocking

## Test cases

| Case | Reference | Focus | Outcome |
|---|---|---|---|
| Standard non-privileged access | AR-2026-001 | Rahul Mehta requests Finance Manager | Provisioned |
| Privileged access with four-eyes | AR-2026-002 | Time-limited System Administrator | Provisioned (time-limited) |
| SoD conflict | AR-2026-003 | Payment Initiator + Payment Approver | Blocked |
| Exception handling | AR-2026-004 | Missing justification, invalid target, inactive target, duplicate | Documented |

## Classification

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder actions (manager endorsements, IAM Administrator approvals) are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

## Evidence

Evidence files are stored in the Evidence/ folder and referenced by ID (AR-001-E01 to AR-004-E01). See Evidence/Evidence-Register.md.
