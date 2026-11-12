# Exception and Failed Provisioning Analysis

**Case:** AR-2026-004
**Tested:** 12 November 2026
**Evidence:** AR-004-E01

## Purpose

Investigate how the IdentityGuard access-request workflow handles common exception and failure conditions. Each exception was tested safely against the live lab without modifying existing users or business access.

## Exception test results

| # | Scenario | Expected control | Actual result | API status | Impact | Resolution / next action |
|---|---|---|---|---|---|---|
| 1 | Missing justification (empty) | Request rejected; justification required (1-500 chars) | Rejected with validation error | 422 | Request not created | Resubmit with valid justification |
| 2 | Invalid target identity (user_id 999) | Request rejected; target not found | Rejected: "User 999 not found" | 404 | Request not created | Verify target employee ID |
| 3 | Inactive target account (Maya Rao, user 12, TERMINATED) | Request rejected; access only for active users | Rejected: "Access can only be requested for an active user" | 422 | Request not created | Do not request access for terminated accounts |
| 4 | Duplicate access request (Rahul already has Finance Manager) | Provisioning blocked; user already has role | Request created (201), approved (200), provisioning blocked: "User already has this role" | 409 at provision | No duplicate role assigned | Close request; no action needed |

## Notes

- Exceptions 1-3 are rejected at request intake (before any role assignment). No access is granted.
- Exception 4 is allowed through request and approval but blocked at provisioning because the target already holds the role. This confirms the duplicate-protection control works at provisioning time.
- No existing users were modified and no business access was altered during exception testing.
- Rejected approval and unauthorised provisioning attempts were not separately executed to avoid creating unnecessary request state; they are covered by the application's authorisation guards (documented in the limitations register).

**Classification:** Actual lab exception testing.
