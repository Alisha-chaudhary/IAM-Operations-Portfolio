# Joiner - Provisioning

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Provisioning Date:** 12 November 2026
**Provisioned By:** IAM Operations Analyst
**Local Lab Execution Time:** 2026-11-12T17:57:17Z (simulated chronological replay)

## Purpose

Create Maya's identity in the local IdentityGuard lab and record provisioning evidence. This is a controlled chronological replay in the isolated local lab. It is not an actual scheduled production lifecycle event.

## Pre-Provisioning State

- Validation: APPROVED (post-amendment)
- Approvals: Hiring manager endorsement and IAM Administrator approval obtained (simulated)
- SoD: No conflict
- Existing identity: None (EMP-1001 not in live inventory)

## Identity Creation

The IdentityGuard `POST /jml/users` endpoint creates an account with status ACTIVE immediately. It does not provide a future activation scheduler. The account was not created early and then claimed as scheduled for 17 November 2026.

### API Request

| Field | Value |
|---|---|
| Endpoint | POST /jml/users |
| Permission | IdentityGuard:user.create |
| actor | identityguard.admin (IAM Administrator) |
| employee_id | EMP-1001 |
| username | maya.rao |
| full_name | Maya Rao |
| email | maya.rao@example.test |
| department_id | 1 (Finance) |
| manager_id | 1 (Priya Nair) |
| password | Strong temporary lab credential (not recorded in plaintext) |

### API Response

Status: 201 Created

```json
{
  "id": 12,
  "employee_id": "EMP-1001",
  "username": "maya.rao",
  "full_name": "Maya Rao",
  "email": "maya.rao@example.test",
  "department_id": 1,
  "manager_id": 1,
  "status": "ACTIVE",
  "terminated_at": null
}
```

Resulting User ID: 12

## Access Requests and Provisioning

Maya's birth-right access (CRM: Relationship Manager, PMS: Portfolio Viewer) is proposed Asteron training data and is not implemented in IdentityGuard. No IdentityGuard access requests were submitted for these entitlements because they are target-application/manual controls, not IdentityGuard roles.

No access requests were created in IdentityGuard for Maya's joiner access. No provisioning events were generated beyond the USER_CREATED audit event.

## Audit Events

| Event ID | Timestamp | Actor | Event Type | Target | Action | Result | Reason |
|---|---|---|---|---|---|---|---|
| 4 | 2026-11-12T17:57:17.504936 | identityguard.admin | USER_CREATED | maya.rao | create_user | SUCCESS | JML joiner created user account |

## Password Handling

A strong temporary lab credential was used for account creation. The plaintext password was not written to portfolio evidence and was not committed to Git.

## Conclusion

Maya's identity was created in the local IdentityGuard lab with status ACTIVE, department Finance, manager Priya Nair. No IdentityGuard roles were assigned because the birth-right entitlements are proposed target-application controls. The USER_CREATED audit event was recorded.

**Evidence references:** JML-001-E11, JML-001-E12, JML-001-E13, JML-001-E14

**Classification:** Actual local lab execution (simulated chronological replay). Simulated stakeholder approvals.
