# Privileged Access Request - Request and Eligibility Validation

**Case:** AR-2026-002
**Employee:** Sneha Rao (EMP003)
**Requested role:** System Administrator (role ID 5, privileged)
**Submitted:** 12 November 2026 18:37:37 UTC
**Submitter:** IAM Operations Analyst (identityguard.admin, user 8) on behalf of Sneha Rao
**Evidence:** AR-002-E01

## Purpose

Document the privileged access request intake and eligibility validation. Privileged access requires IAM Administrator approval, `role.assign_privileged`, and four-eyes control (approver != provisioner).

## Identity validation

| Check | Value | Result |
|---|---|---|
| Target employee ID | EMP003 | Exists once - PASS |
| Target username | sneha.rao | PASS |
| Full name | Sneha Rao | PASS |
| Department | HR (ID 2) | PASS |
| Account status | ACTIVE | PASS |

## Existing role assignments (Sneha Rao)

| Role | Status | Privileged |
|---|---|---|
| HR Analyst | ACTIVE | No |

Sneha Rao holds only HR Analyst. She does not hold System Administrator. The request is not duplicative.

## Requested role validation

| Attribute | Value |
|---|---|
| Role | System Administrator (role ID 5) |
| Privileged | Yes |
| Permissions | PROD-LINUX-01:admin, PROD-WIN-01:admin |
| Approval required | IAM Administrator approval + role.assign_privileged |
| Four-eyes required | Yes (approver != provisioner) |
| Supported by IdentityGuard | Yes - implemented |

## Business justification (simulated)

"Temporary System Administrator access for emergency server investigation during production incident, time-limited to one hour."

This is a fictional training justification. No real production incident is represented.

## Time-limiting (least privilege)

The request includes `expires_at` of 2026-11-12T19:37:23 (approximately one hour from submission). This avoids creating permanent privileged access for an ordinary user. The role assignment will expire automatically.

## Eligibility conclusion

Sneha Rao is an active HR employee with no existing privileged roles. System Administrator is a configured privileged role. The request is time-limited. The case is eligible for privileged access processing, subject to IAM Administrator approval and four-eyes provisioning.

**Evidence reference:** AR-002-E01

**Classification:** Actual lab validation. Simulated business justification. Time-limited to avoid permanent privileged access.
