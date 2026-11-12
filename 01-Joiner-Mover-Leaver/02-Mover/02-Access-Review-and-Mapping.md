# Mover - Access Review and Mapping

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Review Date:** 12 November 2026 (simulated chronological replay)
**Reviewed By:** IAM Operations Analyst

## Purpose

Compare Maya's current access with the access required for the Investment Operations Analyst role. Identify access to retain, remove, and request.

## Current Access (IdentityGuard)

Maya has no IdentityGuard roles assigned. Her current access consists of:
- Identity: Active, Finance department, manager Priya Nair
- IdentityGuard roles: None

Her joiner birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) are proposed Asteron training data and are not implemented in IdentityGuard.

## New Role Requirements (Investment Operations Analyst)

Per the RBAC Matrix (proposed Asteron training data):

| Application | Role | Entitlement | Implementation Status |
|---|---|---|---|
| Trade Operations Portal | Trade Ops: Trade Analyst | View and enter trades (no approval) | No - proposed Asteron training data |
| Portfolio Management System | PMS: Portfolio Manager (view) | View all portfolios | No - proposed Asteron training data |

Both entitlements are proposed Asteron training data and are NOT implemented in IdentityGuard.

## Access to Retain

No IdentityGuard roles are currently assigned, so there are no IdentityGuard roles to retain.

## Access to Remove

No IdentityGuard roles are currently assigned, so there are no IdentityGuard roles to remove.

The proposed Asteron birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) would be revoked through the target applications or manual process, not through IdentityGuard.

## Access to Request

| Entitlement | Application | Approval Required | Implementation Status |
|---|---|---|---|
| Trade Ops: Trade Analyst | Trade Operations Portal | Manager approval | No - proposed Asteron training data |
| PMS: Portfolio Manager (view) | Portfolio Management System | Manager approval | No - proposed Asteron training data |

Both are proposed target-application controls, not IdentityGuard roles. No IdentityGuard access requests were created.

## SoD Check

The proposed SoD-T-01 rule (Trade Analyst + Trade Approver) is proposed Asteron training data and is not implemented in IdentityGuard. Maya does not hold the Trade Approver role. No implemented IdentityGuard SoD conflict applies.

## Mover Endpoint Behavior

The IdentityGuard `move_user` endpoint:
- Updates `department_id` and/or `manager_id`
- Does NOT auto-add or auto-remove roles
- Movers retain their existing roles; the compensating control is the access review
- Does not execute the access-request/approval/provisioning workflow

Because the destination department is not configured, the mover endpoint could not be called successfully.

## Conclusion

No IdentityGuard access changes are required for the mover because Maya has no IdentityGuard roles. The proposed Asteron entitlements for both the joiner and mover roles are target-application/manual controls. The move itself is blocked by the missing Investment Operations department.

**Evidence reference:** JML-001-E16

**Classification:** Policy analysis. Simulated HR mover context.
