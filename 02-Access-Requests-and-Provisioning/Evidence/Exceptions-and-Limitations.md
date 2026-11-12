# Exceptions and Limitations Register

**Case references:** AR-2026-001 to AR-2026-004
**Scenario:** Access Requests and Provisioning (Scenario 2)

## Exceptions

No formal access exceptions were raised or approved in this scenario.

| Field | Value |
|---|---|
| SoD exceptions | None required - no approved conflicting access |
| Access exceptions | None |
| Approval exceptions | None |

## Technical limitations

### L1 - Single approver per access request

**Application:** IdentityGuard
**Component:** Access request workflow
**Description:** IdentityGuard supports one approver per access request. The organisational approval chain (manager endorsement + IAM Administrator approval) requires more than one approval.
**Impact:** The manager endorsement (Priya Nair) is recorded as a separate simulated stakeholder record. The IdentityGuard system approver is the IAM Administrator. IdentityGuard does not natively enforce a multi-stage approval chain.
**Control Decision:** Additional approval documented as a separately simulated stakeholder approval. Not presented as an IdentityGuard feature.

### L2 - Manager cannot use the IdentityGuard API

**Application:** IdentityGuard
**Component:** Authentication / platform permissions
**Description:** Priya Nair (Rahul's manager) holds Finance Manager and Payment Approver roles, neither of which grants an IdentityGuard platform permission. She cannot log in or approve via the API.
**Impact:** Manager endorsement is recorded as a simulated stakeholder record rather than an IdentityGuard system approval.
**Control Decision:** Documented. The IAM Administrator performs the system approval.

### L3 - Only two IAM Administrator identities exist

**Application:** IdentityGuard
**Component:** Seed data
**Description:** Only identityguard.admin (user 8) and identityguard.admin2 (user 9) hold IAM Administrator. For privileged four-eyes provisioning (approver != provisioner), the requester and provisioner must be the same identity (user 8) while the approver is the other (user 9).
**Impact:** Requester and provisioner are the same person for the privileged case. The system permits this (it only blocks approver == provisioner). The key four-eyes rule (approver != provisioner) is satisfied.
**Control Decision:** Documented as a lab limitation. Approver != provisioner confirmed.

### L4 - Time-limited privileged access

**Application:** IdentityGuard
**Component:** Access request expires_at
**Description:** Privileged access to an ordinary user was made time-limited (expires_at set) to avoid creating permanent privileged access. The assignment expires automatically.
**Impact:** Sneha Rao's System Administrator role expires at 2026-11-12T19:37:23 UTC. After expiry, the role remains assigned but expired.
**Control Decision:** Time-limited provisioning used to respect least privilege. Noted that the expired assignment remains in the record (not deleted).

### L5 - Direct role assignment bypasses SoD

**Application:** IdentityGuard
**Component:** app/iam/service.py (assign_role/remove_role)
**Description:** Direct role assignment does not itself perform an SoD check. SoD is enforced only in the provisioning path.
**Impact:** A privileged administrator could bypass SoD via direct assignment. This is a control gap managed by procedure.
**Control Decision:** The governed access-request and provisioning process was used. Direct assignment was not used.

### L6 - `/users` endpoint does not expose manager_id

**Application:** IdentityGuard
**Component:** app/api/users.py
**Description:** The GET /users response does not include manager_id. Manager relationships had to be validated directly against the database.
**Impact:** Manager validation required direct DB query rather than API.
**Control Decision:** Documented. Manager relationship validated against live database.

## SoD rule coverage

Implemented IdentityGuard SoD rules:
- SoD-01: Payment Initiator + Payment Approver
- SoD-02: System Administrator + SOC Analyst
- SoD-03: Database Administrator + Security Auditor

Proposed Asteron training rules are not implemented in IdentityGuard and were not represented as implemented.

## Untested controls

- Rejected approval (submit then reject) - not separately executed to avoid unnecessary request state; covered by authorisation guards.
- Unauthorised provisioning attempt (target user provisioning their own request) - not separately executed; blocked by provisioner == target guard.
- Missing approver permissions - not separately executed; covered by require_permission guard.

These are documented as untested control analysis rather than fabricated results.
