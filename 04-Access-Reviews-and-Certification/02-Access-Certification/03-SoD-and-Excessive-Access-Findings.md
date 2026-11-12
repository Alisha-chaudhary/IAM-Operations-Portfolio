# Scenario 4 — SoD and Excessive Access Findings

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026
**Evidence:** ACR-001-E09 (SoD violations report, pre and post remediation)

## Purpose

Review assignments for conflicting roles, unnecessary privileged access, inappropriate combinations, roles retained after a mover event, and access that no longer aligns with the employee's department or responsibilities. Assess against the implemented SoD policy.

## Implemented SoD rules (verified)

Source: `app/governance/sod.py` (SOD_CONFLICT_RULES) and `05-SoD-Policy-and-Rules-Register.docx` §10.1

| Rule ID | Conflicting roles | Implemented in IdentityGuard |
|---|---|---|
| SoD-01 | Payment Initiator + Payment Approver | Yes — enforced at provisioning |
| SoD-02 | System Administrator + SOC Analyst | Yes — enforced at provisioning |
| SoD-03 | Database Administrator + Security Auditor | Yes — enforced at provisioning |

Proposed rules (SoD-T-01 to SoD-T-04) are training data and not implemented. They were not applied.

## SoD assessment result

The SoD violations report (`GET /reports/sod-violations`) returned **total_count = 0, items = []** both before and after remediation. No active user holds both sides of any implemented SoD rule.

Cross-check performed per item:
- rahul.mehta holds Payment Initiator but NOT Payment Approver → no active SoD-01 conflict. (His pending-but-unprovisioned Payment Approver request, Scenario 3 Request ID 3, is SoD-blocked and cannot be provisioned.)
- sneha.rao held System Administrator but NOT SOC Analyst → no active SoD-02 conflict (now revoked).
- kiran.reddy holds Database Administrator but NOT Security Auditor → no active SoD-03 conflict.
- No user holds System Administrator + SOC Analyst, or Database Administrator + Security Auditor.

## Excessive / inappropriate access findings

| Finding | User | Role | Assessment | Decision |
|---|---|---|---|---|
| Stale cross-department access | meera.iyer (HR) | Finance Analyst | Meera moved Finance → HR but retained Finance Analyst. Cross-department access no longer required. Identified in seed data as the stale-access case. | REVOKE (item 8) |
| Privileged access without current justification | sneha.rao (HR) | System Administrator | Privileged emergency access (Scenario 2) concluded; time-limited. HR user should not hold server administration privileges. | REVOKE (item 7) |
| Sensitive access — watch item | rahul.mehta (Finance) | Payment Initiator | Payment creation access is sensitive but Finance-appropriate. No Payment Approver held → no active SoD conflict. Flagged for periodic manager re-confirmation. | RETAIN (item 5) |

## Important implementation limitation

The IdentityGuard access review process does **not** automatically block a RETAIN decision solely because of an SoD finding. The reviewer must identify and address relevant conflicts manually. In this review, no active SoD conflicts existed, so no RETAIN decision conflicted with an implemented SoD rule. The reviewer cross-checked every item against the SoD Rules Register before deciding.

## Access associated with terminated identities

Maya Rao (EMP-1001) is TERMINATED with zero active role assignments. Excluded from the active certification population. Her access was revoked at termination in Scenario 1. No terminated-identity access remains.
