# Leaver - Intake and Validation

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Leaver Event Date:** Simulated - 30 June 2027 effective
**Intake Date:** 12 November 2026 (simulated chronological replay)
**Intake Performed By:** IAM Operations Analyst

## Purpose

Receive and validate the simulated HR leaver event for Maya Rao's termination.

## Leaver Event Details

| Field | Value |
|---|---|
| Employee ID | EMP-1001 |
| Full Name | Maya Rao |
| Department | Finance |
| Designation | Relationship Manager |
| Manager | Priya Nair |
| Effective Date | 30 June 2027 |

## Identity Validation

Maya's identity exists in IdentityGuard:
- User ID: 12
- Username: maya.rao
- Employee ID: EMP-1001
- Status: ACTIVE
- Department: Finance (ID 1)
- Manager: Priya Nair (user ID 1)

## HR Authorisation

Termination authorised by simulated HR. Manager notified per process. The original HR approval reference HR-APP-2026-441 remains associated with the case.

## Effective Date Validation

The leaver effective date is 30 June 2027. IdentityGuard does not support future-dated termination scheduling. The termination is executed when the leaver event is processed.

## Current Access Review

Maya has no IdentityGuard roles assigned. No outstanding access requests exist for Maya.

## Pre-Termination Access Inventory

Recorded before termination (see E20):
- User status: ACTIVE
- Role assignments: None
- Outstanding access requests: None
- Audit events: USER_CREATED only

## Validation Outcome

**Status:** VALIDATED - ready for termination

Maya's identity and HR authorisation were validated. The case is ready to proceed to termination through the IdentityGuard `terminate_user` endpoint.

**Evidence reference:** JML-001-E19

**Classification:** Simulated HR leaver event. Actual lab validation.
