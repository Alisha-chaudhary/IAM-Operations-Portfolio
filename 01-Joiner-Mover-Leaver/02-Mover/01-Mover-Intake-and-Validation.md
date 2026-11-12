# Mover - Intake and Validation

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Mover Event Date:** Simulated - 1 February 2027 effective
**Intake Date:** 12 November 2026 (simulated chronological replay)
**Intake Performed By:** IAM Operations Analyst

## Purpose

Receive and validate the simulated HR mover event for Maya Rao's transfer from Finance to Investment Operations.

## Mover Event Details

| Field | Value |
|---|---|
| Employee ID | EMP-1001 |
| Full Name | Maya Rao |
| Previous Department | Finance |
| Previous Designation | Relationship Manager |
| Previous Manager | Priya Nair |
| New Department | Investment Operations |
| New Designation | Investment Operations Analyst |
| New Manager | Arjun Mehta (proposed) |
| Effective Date | 1 February 2027 |

## Identity Validation

Maya's identity exists in IdentityGuard:
- User ID: 12
- Username: maya.rao
- Employee ID: EMP-1001
- Status: ACTIVE
- Current department: Finance (ID 1)
- Current manager: Priya Nair (user ID 1)

## Department Validation

The destination department, Investment Operations, is NOT configured in the local IdentityGuard reference data. Configured departments are:
- 1: Finance
- 2: HR
- 3: IT
- 4: Security

No department was created to force the move. This is a controlled reference-data dependency.

## Manager Validation

The proposed new manager, Arjun Mehta, is not present in the live identity inventory. This must be confirmed before the move can proceed.

## Validation Outcome

**Status:** BLOCKED - destination department not configured

The move cannot be executed in IdentityGuard until:
1. The Investment Operations department is added to IdentityGuard reference data, OR
2. A controlled reference-data dependency is recorded and the move is executed once the department exists.

## Operational Impact

- The mover endpoint (`PATCH /jml/users/{user_id}/move`) requires a valid `department_id`.
- Attempting to move to a non-existent department returns a 404 error ("Department does not exist").
- No move was performed. Maya remains in Finance with manager Priya Nair.

## Approval Requirements (Pending)

Per the Approval Matrix (Mover access modification row):
- New manager endorsement required
- IAM Administrator approval required
- SoD check at provisioning for any new access
- Mover cannot self-approve

These approvals are pending because the move is blocked.

**Evidence references:** JML-001-E15

**Classification:** Simulated HR mover event. Actual lab validation (department not found).
