# Exceptions and Limitations Register

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Scenario:** Joiner-Mover-Leaver (Scenario 1)

## Exceptions

No formal exceptions were raised or approved in this scenario.

| Field | Value |
|---|---|
| SoD exceptions | None required - no SoD conflict identified |
| Access exceptions | None |
| Approval exceptions | None |
| Emergency access | None |

## Technical Limitations

### L1 - No future-dated activation

**Application:** IdentityGuard
**Component:** `POST /jml/users` (joiner)
**Description:** The joiner endpoint creates an account with status ACTIVE immediately. It does not provide a future activation scheduler.
**Impact:** Maya's account could not be scheduled for 17 November 2026. A controlled chronological replay was performed in the isolated local lab. This is not an actual scheduled production lifecycle event.
**Control Decision:** Documented as a simulated chronological replay. Account created ACTIVE immediately with validation and approvals in place.

### L2 - Destination department not configured (Mover blocked)

**Application:** IdentityGuard
**Component:** `PATCH /jml/users/{user_id}/move` (mover)
**Description:** The destination department Investment Operations is not configured in IdentityGuard reference data. Configured departments: Finance (1), HR (2), IT (3), Security (4).
**Impact:** The move could not be executed. The API returned 404 "Department 99 does not exist."
**Control Decision:** Recorded as a blocker, not a simulated success. No department was created to force the move. Outstanding reference-data dependency.

### L3 - No LDAP account disablement

**Application:** IdentityGuard
**Component:** `POST /jml/users/{user_id}/terminate` (leaver)
**Description:** The termination endpoint sets status TERMINATED and expires roles, but does not disable the OpenLDAP account.
**Impact:** LDAP disablement, if required, is a separate downstream action. It was not performed.
**Control Decision:** Documented as an outstanding downstream action. The IdentityGuard result alone does not establish LDAP deactivation.

### L4 - No server-side token revocation

**Application:** IdentityGuard
**Component:** Authentication (JWT)
**Description:** IdentityGuard uses short-lived JWTs (15 minutes) with no server-side token denylist. Logout is client-side.
**Impact:** Termination does not instantly revoke all existing authentication tokens or sessions.
**Control Decision:** Documented as a limitation. Existing tokens remain valid until expiry.

### L5 - Birth-right entitlements not implemented in IdentityGuard

**Application:** IdentityGuard
**Component:** RBAC / Entitlement Catalogue
**Description:** Maya's birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) are proposed Asteron training data and are not implemented in IdentityGuard.
**Impact:** These entitlements were not provisioned through IdentityGuard. They are handled as manual/target-application controls.
**Control Decision:** Documented as proposed target-application access. No new role, entitlement, application, or department was created in IdentityGuard.

### L6 - Single approver per access request

**Application:** IdentityGuard
**Component:** Access request workflow
**Description:** IdentityGuard supports one approver per access request. The organisational approval chain (hiring manager + IAM Administrator) requires more than one approval.
**Impact:** The second approval (IAM Administrator) is recorded separately as a simulated stakeholder approval. IdentityGuard does not natively enforce a multi-stage approval chain.
**Control Decision:** Additional approval documented as a separately simulated stakeholder approval. Not presented as an IdentityGuard feature.

### L7 - Direct role assignment bypasses SoD

**Application:** IdentityGuard
**Component:** `app/iam/service.py` (`assign_role`/`remove_role`)
**Description:** Direct role assignment does not itself perform an SoD check. SoD is enforced only in the provisioning path.
**Impact:** A privileged administrator could bypass SoD via direct assignment. This is a control gap managed by procedure.
**Control Decision:** The governed access-request and provisioning process was used. Direct assignment was not used to bypass SoD.

### L8 - Mover endpoint does not auto-remove roles

**Application:** IdentityGuard
**Component:** `PATCH /jml/users/{user_id}/move` (mover)
**Description:** The mover endpoint updates department and/or manager but does not auto-add or auto-remove roles. Movers retain existing roles; the compensating control is the access review.
**Impact:** Even if the move succeeded, stale roles would remain pending an access review.
**Control Decision:** Access review would be required after any successful move. Not executed because the move was blocked.

## SoD Rule Coverage

Implemented IdentityGuard SoD rules:
- SoD-01: Payment Initiator + Payment Approver
- SoD-02: System Administrator + SOC Analyst
- SoD-03: Database Administrator + Security Auditor

Proposed Asteron training rules (SoD-T-01 to SoD-T-04) are not implemented in IdentityGuard.

No SoD conflict was identified for Maya's access.
