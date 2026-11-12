# Standard Access Request - Requester and Identity Validation

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Validated:** 12 November 2026
**Validator:** IAM Operations Analyst (acting via identityguard.admin)
**Evidence:** AR-001-E01

## Purpose

Verify the requester and target identity before any access request is submitted. Confirm account status, employee ID uniqueness, and the manager relationship.

## Identity validation results

| Check | Value | Result |
|---|---|---|
| Requester / target employee ID | EMP002 | Exists once in live inventory - PASS |
| Requester / target username | rahul.mehta | PASS |
| Full name | Rahul Mehta | PASS |
| Department | Finance (ID 1) | PASS |
| Account status | ACTIVE | PASS |
| Employee ID uniqueness | EMP002 appears once | PASS |
| Existing identity check | No duplicate Rahul Mehta identity | PASS |

## Manager relationship validation

The live database was queried directly (the `/users` endpoint does not expose `manager_id`).

| Attribute | Value |
|---|---|
| Rahul Mehta user ID | 2 |
| Rahul Mehta manager_id | 1 |
| Manager (user ID 1) | Priya Nair (EMP001) |
| Manager department | Finance |
| Manager status | ACTIVE |
| Manager relationship valid | Yes - PASS |

Priya Nair is a valid, active Finance manager and is Rahul's recorded manager. She is eligible to provide manager endorsement.

## Requester authorisation

Rahul Mehta holds Finance Analyst and Payment Initiator roles. Neither role includes an IdentityGuard platform permission (e.g. `IdentityGuard:access.request`). Rahul cannot log in to IdentityGuard or submit a request directly.

The access request was therefore submitted by the IAM Operations Analyst (authenticated as identityguard.admin, who holds `IdentityGuard:access.request`) on Rahul's behalf. Rahul is recorded as the business requester and target. This is an authorised requester submission, consistent with the Approval Matrix ("request can be submitted by an employee or another authorised requester").

## Conclusion

Rahul Mehta's identity and account status are valid. The manager relationship is confirmed. Rahul cannot self-submit via the API, so an authorised requester submits on his behalf. The case is ready for request intake.

**Evidence reference:** AR-001-E01

**Classification:** Actual lab validation. Simulated business context.
