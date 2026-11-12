# Scenario 3 — Corrective Actions

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Recorded at:** 12 November 2026
**Recorded by:** IAM Operations Analyst

## Corrective actions taken

| Exception ID | Corrective action | Supported by API? | Action performed | Result |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Close as superseded — Finance Manager already held via Request ID 1 | No API mutation needed | Documented that Request ID 4 is moot; entitlement already assigned | Exception closed |
| IAM-EXC-2026-002 | Close as conflict prevented — SoD-01 blocks Payment Approver | No API mutation needed | Documented SoD-01 block; Payment Approver not granted | Exception closed |
| IAM-EXC-2026-003 | Monitor auto-expiry of time-limited System Administrator | No API mutation needed | Documented expiry at 19:37:23; no renewal required | Exception open (monitoring) |

## Why no API mutation was performed

For EXC-001 and EXC-002, the requests are APPROVED and stuck:
- Provisioning is blocked (duplicate / SoD)
- Rejection is blocked (reject requires REQUESTED status; APPROVED returns 409 "already decided")

No API action could resolve the stuck state. The corrective action is therefore the operational decision to document the circumstance and close the exception. This is consistent with the Exception Management SOP, which allows closure when the underlying need is already met (EXC-001) or when a preventive control has blocked the access (EXC-002).

No direct role assignment (assign_role/remove_role) was used, because that would bypass SoD and is not a supported exception-resolution path.

## Retry evaluation

| Exception | Retry considered? | Retry performed? | Reason |
|---|---|---|---|
| IAM-EXC-2026-001 | Yes | No | Rahul already holds Finance Manager; retrying would create duplicate access with no business need. |
| IAM-EXC-2026-002 | Yes | No | SoD-01 blocks Payment Approver; retrying would repeatedly fail and no conflicting access should be granted. |
| IAM-EXC-2026-003 | No | No | Access self-expires; no retry needed. |

Retries were evaluated and determined inappropriate for all three cases. This demonstrates operational judgement: access was not granted merely to close an SLA case.

## Stakeholder coordination (simulated)

| Exception | Stakeholder | Coordination | Label |
|---|---|---|---|
| IAM-EXC-2026-001 | Rahul Mehta (requester), Priya Nair (manager) | No stakeholder action needed — access already held | Simulated (not required) |
| IAM-EXC-2026-002 | Rahul Mehta (requester), Priya Nair (manager), IAM Administrator | No stakeholder action needed — SoD block is preventive | Simulated (not required) |
| IAM-EXC-2026-003 | Sneha Rao (requester) | No stakeholder action needed — self-expiring emergency access | Simulated (not required) |

No ServiceNow PDI ticket, email, or external notification was created or claimed. IdentityGuard has no ServiceNow integration.

## Evidence

- EXC-001-E10, EXC-002-E10, EXC-003-E10: Corrective action records
- EXC-001-E11, EXC-002-E11, EXC-003-E11: Retry evaluation (documented as not performed)
