# Scenario 3 — Root Cause Analysis

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Analyst:** IAM Operations Analyst
**Date:** 12 November 2026

## Format

For each exception: what happened, when, expected vs actual outcome, failed control/process, cause category, evidence, corrective action, responsible party, and whether resolvable within IAM.

## IAM-EXC-2026-001 — Duplicate Finance Manager request

**1. What happened.** Request ID 4 was submitted and approved for Rahul Mehta to receive Finance Manager. Provisioning was never completed because Rahul already holds Finance Manager (assigned via Request ID 1 at 18:36:21).

**2. When it happened.** Request submitted 18:38:46; approved 18:39:17; exception identified 18:52 on 12 November 2026.

**3. Expected outcome.** The request would be provisioned and Rahul would receive Finance Manager.

**4. Actual outcome.** Provisioning blocked (409 duplicate). Request remains APPROVED and unprovisioned. Rahul already holds Finance Manager.

**5. Failed control/process.** No control failed. This is a duplicate request — the entitlement was already delivered through Request ID 1. The approval of a duplicate request is an operational redundancy, not a control failure.

**6. Cause category.** Data-related / operational (duplicate request for an already-assigned entitlement). Not technical, not approval-related, not policy-related.

**7. Evidence.** GET /access-requests (Request ID 4 APPROVED, provisioned_at null); GET /reports/role-access-assignments (Rahul holds Finance Manager ACTIVE); POST /access-requests/4/provision (409).

**8. Corrective action.** Document that Finance Manager is already held; close the exception as resolved by circumstance. Request ID 4 is moot — no further provisioning required.

**9. Responsible party.** IAM Operations Analyst (within IAM; no other team required).

**10. Resolvable within IAM?** Yes — closed by documentation decision.

## IAM-EXC-2026-002 — SoD-blocked Payment Approver request

**1. What happened.** Request ID 3 was submitted and approved for Rahul Mehta to receive Payment Approver. Provisioning was blocked by SoD-01 because Rahul already holds Payment Initiator. No conflicting access was granted.

**2. When it happened.** Request submitted 18:38:22; approved 18:38:29; provisioning blocked 18:38:29 and re-confirmed 18:53; exception identified 18:53 on 12 November 2026.

**3. Expected outcome.** The request would be provisioned and Rahul would receive Payment Approver.

**4. Actual outcome.** Provisioning blocked (409 SoD). SOD_VIOLATION audit events recorded (DENIED). Request remains APPROVED and unprovisioned. Payment Approver not assigned.

**5. Failed control/process.** No control failed. The SoD preventive control worked as intended — conflicting access was blocked. The approval of a request that later fails SoD at provisioning is an operational sequencing issue (approval occurs before SoD is evaluated at provisioning).

**6. Cause category.** Policy-related (SoD rule) — the conflict is a legitimate, functioning preventive control. Not technical, not approval-related (the approval itself was valid; the conflict is only evaluated at provisioning).

**7. Evidence.** GET /access-requests (Request ID 3 APPROVED); role assignments (Rahul holds Payment Initiator); POST /access-requests/3/provision (409 SoD); SOD_VIOLATION audit events (IDs 36, 48); GET /reports/sod-violations (0 active conflicts — none granted).

**8. Corrective action.** Document the SoD-01 block; do not grant Payment Approver. Close as conflict prevented. If business needs Payment Approver coverage, Rahul's Payment Initiator role would need to be reviewed first (outside this scenario).

**9. Responsible party.** IAM Operations Analyst (within IAN; escalation to IAM Administrator not required as the control functioned).

**10. Resolvable within IAM?** Yes — closed by documentation decision. Granting Payment Approver would require removing Payment Initiator first, which is a separate access-change decision outside this scenario.

## IAM-EXC-2026-003 — Expiring time-limited privileged access

**1. What happened.** Request ID 2 was provisioned for Sneha Rao to receive System Administrator, time-limited to one hour (expires 2026-11-12T19:37:23). This is emergency access designed to self-expire.

**2. When it happened.** Provisioned 18:38:04; exception identified 18:53 on 12 November 2026 (~44 minutes remaining).

**3. Expected outcome.** Access expires automatically at 19:37:23.

**4. Actual outcome.** Access is active and will auto-expire. No renewal required.

**5. Failed control/process.** No control failed. The time-limited provisioning control is functioning as designed.

**6. Cause category.** None — expected behaviour. This is an SLA-monitoring case, not a failure.

**7. Evidence.** GET /access-requests (Request ID 2 PROVISIONED, expires_at 19:37:23); role assignments (Sneha holds System Administrator ACTIVE with expires_at).

**8. Corrective action.** Monitor until auto-expiry; verify post-expiry that the assignment is expired. No renewal.

**9. Responsible party.** IAM Operations Analyst (within IAM; no other team required).

**10. Resolvable within IAM?** Yes — self-resolving at expiry; monitoring and post-expiry verification within IAM.

## Cause category summary

| Exception | Cause category | Control failed? |
|---|---|---|
| IAM-EXC-2026-001 | Data-related / operational (duplicate) | No |
| IAM-EXC-2026-002 | Policy-related (SoD preventive control) | No — control functioned |
| IAM-EXC-2026-003 | None (expected behaviour) | No |

No root cause was inferred beyond what the evidence supports.
