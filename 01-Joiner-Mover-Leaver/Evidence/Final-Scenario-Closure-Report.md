# Final Scenario Closure Report

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Scenario:** Joiner-Mover-Leaver (Scenario 1)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Closure Date:** 12 November 2026
**Closed By:** IAM Operations Analyst

## Scenario Summary

This scenario documented the complete Joiner-Mover-Leaver lifecycle for Maya Rao (EMP-1001) in a fictional IAM Operations training environment using the IdentityGuard lab application.

## Lifecycle Status Summary

| Phase | Status | Detail |
|---|---|---|
| Joiner intake and validation | Completed | Initial hold (NOT APPROVED), then APPROVED after amendment |
| HR master-data clarification | Completed | Simulated HR amendment: Finance (1), Priya Nair (user 1) |
| Identity creation | Completed | User ID 12 created, ACTIVE, Finance, manager Priya Nair |
| Birth-right access analysis | Completed | CRM + PMS entitlements = proposed training data, not in IdentityGuard |
| Approval validation | Completed | Hiring manager + IAM Administrator approvals (simulated) |
| SoD validation | Completed | No conflict identified |
| Access provisioning | Completed (IdentityGuard) | No IdentityGuard roles assigned; birth-right = target-app controls |
| Post-provisioning verification | Completed | Identity verified, ACTIVE, correct attributes |
| Mover intake and validation | Completed | BLOCKED - destination department not configured |
| Access review following move | Completed | No IdentityGuard roles to retain/remove/request |
| Removal/retention of old access | Completed | No IdentityGuard roles assigned |
| New access approval/provisioning | Not executed | Mover blocked |
| Leaver intake and validation | Completed | Validated, ready for termination |
| Access revocation and termination | Completed | Status TERMINATED, roles expired |
| Post-termination verification | Completed | TERMINATED verified, audit evidence present |
| Audit evidence collection and closure | Completed | This report |

## Completed Work

1. **Joiner:** Maya Rao's identity was created in the local IdentityGuard lab (user ID 12), ACTIVE, Finance department, manager Priya Nair. The USER_CREATED audit event was recorded. Post-provisioning verification confirmed correct attributes and no roles assigned.

2. **Birth-right access:** Maya's birth-right entitlements (CRM: Relationship Manager, PMS: Portfolio Viewer) were identified as proposed Asteron training data, not implemented in IdentityGuard. They were handled as manual/target-application controls.

3. **Approvals:** Hiring manager endorsement and IAM Administrator approval were recorded as separate simulated stakeholder records. IdentityGuard's single-approver limitation was documented.

4. **SoD:** No SoD conflict was identified. The implemented SoD rules (SoD-01, SoD-02, SoD-03) do not apply to Maya's access.

5. **Leaver:** Maya's account was terminated successfully. Status is TERMINATED. Role assignments expired. The USER_TERMINATED audit event was recorded. Post-termination verification confirmed termination.

## Partially Completed Work

**Mover:** The mover to Investment Operations (effective 1 February 2027) could not be executed because the destination department is not configured in IdentityGuard. The API returned 404. This is a documented blocker, not a simulated success.

Outstanding mover actions:
1. Add Investment Operations department to IdentityGuard reference data (or record as controlled dependency).
2. Validate Arjun Mehta as manager in the live identity inventory.
3. Execute the mover operation through `PATCH /jml/users/12/move`.
4. Perform access review and submit access requests for new entitlements.

## Outstanding Actions

| # | Action | Owner | Dependency |
|---|---|---|---|
| 1 | Add Investment Operations department to IdentityGuard | IAM Administrator | Reference data |
| 2 | Validate Arjun Mehta as manager | IAM Operations Analyst | Live identity inventory |
| 3 | Execute mover operation | IAM Operations Analyst | Item 1 and 2 |
| 4 | Mover access review and new access requests | IAM Operations Analyst | Item 3 |
| 5 | LDAP disablement (if required) | Directory team | Separate from IdentityGuard |
| 6 | Revoke CRM/PMS entitlements in target applications | Application owners | Outside IdentityGuard |

## Simulated Stakeholder Actions

The following actions were simulated for the fictional training scenario and are NOT real organisational activity:

- HR joiner event HR-JNR-2026-001 (approved)
- HR amendment confirmation (Finance, Priya Nair)
- Hiring manager endorsement (Priya Nair)
- IAM Administrator approval (identityguard.admin)
- HR mover event (Investment Operations, 1 February 2027)
- HR leaver event (30 June 2027)

## Actual Local Lab Operations Performed

The following operations were executed against the local IdentityGuard API (`http://127.0.0.1:8000`):

1. Identity inventory read (11 users, no EMP-1001)
2. User creation: Maya Rao (EMP-1001), user ID 12, ACTIVE
3. Mover attempt: 404 - department not configured
4. User termination: Maya Rao, status TERMINATED
5. Report reads: identity inventory, role access assignments, audit events, access requests

## Application Limitations Discovered

1. No future-dated activation (joiner creates ACTIVE immediately)
2. Destination department not configured (mover blocked)
3. No LDAP account disablement by termination endpoint
4. No server-side token revocation (short-lived JWTs only)
5. Birth-right entitlements not implemented in IdentityGuard (proposed training data)
6. Single approver per access request (no native multi-stage chain)
7. Direct role assignment bypasses SoD (control gap managed by procedure)
8. Mover endpoint does not auto-remove roles

## Evidence

24 evidence items were collected (JML-001-E01 to JML-001-E24). Evidence files are located in:
- Desktop: `C:\Users\hp\Desktop\IAM-Scenario-1-JML-Completion\`
- Portfolio repo: `01-Joiner-Mover-Leaver/Evidence/`

## Classification

This is a fictional training scenario. Asteron Financial Services is a fictional organisation. All simulated stakeholder actions are labelled as such. No real organisational activity is represented. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

**Evidence reference:** JML-001-E24
