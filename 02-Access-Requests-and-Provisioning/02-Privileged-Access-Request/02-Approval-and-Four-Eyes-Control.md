# Privileged Access Request - Approval and Four-Eyes Control

**Case:** AR-2026-002
**Employee:** Sneha Rao (EMP003)
**Requested role:** System Administrator (role ID 5, privileged)
**Request ID:** 2
**Approved:** 12 November 2026 18:37:56 UTC
**Approver:** identityguard.admin2 (user 9, IAM Administrator)
**Evidence:** AR-002-E02

## Purpose

Record the privileged access approval and confirm the four-eyes control (approver != provisioner) is satisfiable with the available IAM Administrator identities.

## IAM Administrator identities verified

| User ID | Employee ID | Username | Full name | Role | Privileged |
|---:|---|---|---|---|---|
| 8 | ADM001 | identityguard.admin | IdentityGuard Admin | IAM Administrator | Yes |
| 9 | ADM002 | identityguard.admin2 | IdentityGuard Admin Two | IAM Administrator | Yes |

Both identities hold IAM Administrator, which includes `IdentityGuard:access.approve`, `IdentityGuard:access.provision`, and `IdentityGuard:role.assign_privileged`. Both are authorised to approve and provision privileged roles.

## Four-eyes constraint

Privileged role provisioning requires the approver and provisioner to be different people. With only two IAM Administrator identities available, the roles are assigned as follows:

| Workflow step | Identity | User ID |
|---|---|---|
| Requester (submits) | identityguard.admin | 8 |
| Approver | identityguard.admin2 | 9 |
| Provisioner | identityguard.admin | 8 |

The approver (user 9) is different from the provisioner (user 8), satisfying four-eyes. The requester and provisioner are the same identity, which the system permits for privileged roles (the system only blocks approver == provisioner and provisioner == target). This is a limitation of having only two IAM Administrator identities in the lab.

## Approval

| Field | Value |
|---|---|
| Endpoint | POST /access-requests/2/approve |
| Approver | identityguard.admin2 (user 9) |
| Approver is not requester (user 8) | Yes |
| Approver is not target (user 3) | Yes |
| Decision | Approved |
| Reason | Approved time-limited System Administrator access for emergency incident investigation. |
| Decision recorded | 2026-11-12T18:37:56 UTC |
| Request status after approval | APPROVED |

## Conclusion

Privileged access approved by identityguard.admin2. Four-eyes satisfiable: provisioner will be identityguard.admin (different from approver). Ready for provisioning.

**Evidence reference:** AR-002-E02

**Classification:** Actual lab approval. Limitation documented (only two IAM Administrator identities).
