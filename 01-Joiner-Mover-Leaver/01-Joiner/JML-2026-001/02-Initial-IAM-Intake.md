# Joiner - Initial IAM Intake

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**HR Event:** HR-JNR-2026-001
**HR Approval Reference:** HR-APP-2026-441
**Intake Date:** 12 November 2026
**Intake Performed By:** IAM Operations Analyst

## Purpose

Record receipt of the HR joiner event and perform initial intake checks before validation.

## Event Received

The original simulated HR joiner event HR-JNR-2026-001 was received by IAM Operations on 12 November 2026. The event was approved by HR with approval reference HR-APP-2026-441.

The event instructed IAM not to create or activate the account before the start date (17 November 2026) unless an approved exception exists.

## Intake Checks Performed

| Check | Result |
|---|---|
| HR event ID verified | HR-JNR-2026-001 - present |
| IAM case ID verified | JML-2026-001 - assigned |
| HR approval reference verified | HR-APP-2026-441 - present |
| Employee identifier verified | EMP-1001 - unique format |
| Existing identity check | No existing Maya Rao or EMP-1001 in live inventory |
| Department validation | Wealth Management - NOT configured in IdentityGuard |
| Manager validation | Neha Kapoor - NOT in live identity inventory |

## Initial Hold Decision

The case was placed ON HOLD. The department and manager could not be validated against the live IdentityGuard reference data, so role mapping and access approval remained pending. No account creation or access provisioning was performed.

## Missing or Inconsistent Data

- Department: Wealth Management not configured (configured: Finance 1, HR 2, IT 3, Security 4)
- Manager: Neha Kapoor not found in live identity inventory

**Evidence references:** JML-001-E01, JML-001-E02, JML-001-E03, JML-001-E04

**Classification:** Actual lab intake record. Simulated HR event.
