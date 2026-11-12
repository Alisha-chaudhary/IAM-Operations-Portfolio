# Joiner - Post-Amendment Validation

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Validation Date:** 12 November 2026
**Validation Performed By:** IAM Operations Analyst
**Amendment Evidence:** JML-001-E05 (Simulated HR amendment confirmation)

## Purpose

Perform a fresh IAM validation after the simulated HR attribute amendment corrected the department and manager to values that exist in the live IdentityGuard reference data.

## Revalidation Checks

| Check | Value | Result |
|---|---|---|
| Employee ID uniqueness | EMP-1001 | No existing EMP-1001 - PASS |
| Department existence | Finance (ID 1) | Configured in IdentityGuard - PASS |
| Manager existence | Priya Nair (user ID 1) | Present in live inventory - PASS |
| Manager relationship | Priya Nair, Finance, no manager | Valid manager record - PASS |
| Employment attributes | Full-time, Hyderabad, Finance | Recorded - PASS |
| HR event evidence | HR-JNR-2026-001, HR-APP-2026-441 | Present - PASS |
| Amendment evidence | Simulated HR amendment confirmation | Present - PASS |

## New Validation Verdict

**Verdict:** APPROVED (post-amendment)
**Case Status:** Ready for provisioning
**Remaining Blockers:** None for identity creation.

The amended attributes (Finance department, Priya Nair as manager) were validated against the live IdentityGuard reference data. The current live reference data matches the supplied snapshot. No differences were observed.

## Limitations

The amendment is a simulated HR stakeholder confirmation, not a real HR system confirmation. The original HR event remains unchanged.

**Evidence reference:** JML-001-E06

**Classification:** Actual lab revalidation. Simulated HR amendment context.
