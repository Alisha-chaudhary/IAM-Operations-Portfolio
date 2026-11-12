# Scenario 3 — SoD Exception Assessment

**Case reference:** IAM-EXC-2026-002
**Assessed at:** 12 November 2026, 18:53 UTC
**Assessor:** IAM Operations Analyst

## Purpose

Assess the SoD conflict for Request ID 3 (Payment Approver) using the implemented SoD policy and rules. Confirm whether conflicting access exists, whether it was granted, and what the correct outcome is.

## Implemented SoD rules (verified)

Source: `app/governance/sod.py` (SOD_CONFLICT_RULES) and `05-SoD-Policy-and-Rules-Register.docx`, Section 10.1

| Rule ID | Conflicting roles | Implemented in IdentityGuard |
|---|---|---|
| SoD-01 | Payment Initiator + Payment Approver | Yes — enforced at provisioning |
| SoD-02 | System Administrator + SOC Analyst | Yes — enforced at provisioning |
| SoD-03 | Database Administrator + Security Auditor | Yes — enforced at provisioning |

Proposed rules (SoD-T-01 to SoD-T-04) are training data and not implemented. They were not applied.

## Rahul Mehta's relevant roles

| Role | Status | Privileged |
|---|---|---|
| Finance Analyst | ACTIVE | No |
| Finance Manager | ACTIVE | No |
| Payment Initiator | ACTIVE | No |

Rahul holds Payment Initiator. Payment Approver (requested in Request ID 3) would create the SoD-01 combination.

## SoD evaluation result

| Check | Result |
|---|---|
| Does Rahul hold Payment Initiator? | Yes |
| Would Payment Approver create SoD-01? | Yes |
| Was Payment Approver provisioned? | No |
| Was provisioning blocked? | Yes — 409 SoD block |
| Is there an active SoD conflict? | No — /reports/sod-violations total_count = 0 |
| Was a SOD_VIOLATION audit event recorded? | Yes — events 36 and 48 (DENIED) |

## Correct outcome

The SoD preventive control functioned correctly. Payment Approver was not granted to Rahul. No conflicting access exists in production. The exception is closed as "conflict prevented."

## Exception handling (per SOP Section 4.6)

The SOP states: "Do not provision conflicting access; if already present, temporarily remove one role pending decision." In this case, conflicting access was never present (blocked at provisioning), so no removal was required. The corrective action is to document the block and close.

No SoD exception (formal exception with compensating controls) was requested or approved. Granting Payment Approver to Rahul would violate SoD-01 and is not permitted.

## Evidence

- EXC-002-E06: SoD validation (roles, rules, block confirmation)
- EXC-002-E13: Audit trail (SOD_VIOLATION events)
