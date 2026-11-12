# Scenario 3 — Post-Resolution Verification

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Verified at:** 12 November 2026, 18:53 UTC
**Verifier:** IAM Operations Analyst

## Purpose

Verify the resolution of each exception using the supported IdentityGuard reports and endpoints. Confirm that no unauthorised access was provisioned and that SoD requirements are satisfied.

## Verification — IAM-EXC-2026-001 (Request ID 4, duplicate Finance Manager)

| Check | Expected | Actual | Result |
|---|---|---|---|
| Request ID 4 status | APPROVED (stuck, unprovisioned) | APPROVED | PASS |
| Finance Manager provisioned via Request 4 | No | Not provisioned | PASS |
| Rahul holds Finance Manager | Yes (via Request ID 1) | Yes | PASS |
| No duplicate Finance Manager assigned | No duplicate | Single assignment | PASS |
| SoD satisfied | Yes | No conflict | PASS |
| Audit evidence | ACCESS_REQUESTED, ACCESS_APPROVED | Present | PASS |

Rahul's Finance Manager assignment came from Request ID 1 (provisioned 18:36:21), not Request ID 4. No additional Finance Manager assignment was created.

## Verification — IAM-EXC-2026-002 (Request ID 3, SoD-blocked Payment Approver)

| Check | Expected | Actual | Result |
|---|---|---|---|
| Request ID 3 status | APPROVED (stuck, unprovisioned) | APPROVED | PASS |
| Payment Approver provisioned | No | Not provisioned | PASS |
| Rahul holds Payment Approver | No | Not assigned | PASS |
| SoD-01 conflict active | No | /reports/sod-violations total_count = 0 | PASS |
| SOD_VIOLATION audit recorded | Yes | Events 36 and 48 (DENIED) | PASS |
| No unauthorised access | No conflicting access | None granted | PASS |

## Verification — IAM-EXC-2026-003 (Request ID 2, time-limited System Administrator)

| Check | Expected | Actual | Result |
|---|---|---|---|
| Request ID 2 status | PROVISIONED | PROVISIONED | PASS |
| System Administrator assigned | Yes | Yes | PASS |
| Time-limited (expires_at set) | Yes | 2026-11-12T19:37:23 | PASS |
| Access will auto-expire | Yes | Time-limited control | PASS |
| No renewal required | No renewal | None performed | PASS |

## Overall SoD verification

/reports/sod-violations returned total_count = 0. No active SoD conflicts exist in the environment. No conflicting access was provisioned during this scenario.

## No unauthorised access

No role was assigned to any user solely to close an exception. No direct role assignment (assign_role/remove_role) was used. All access state matches the approved or blocked requests.

## Evidence

- EXC-001-E12, EXC-002-E12, EXC-003-E12: Post-resolution verification
- EXC-001-E13, EXC-002-E13, EXC-003-E13: Audit trail
