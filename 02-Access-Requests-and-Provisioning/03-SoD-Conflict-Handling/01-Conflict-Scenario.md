# SoD Conflict Handling - Conflict Scenario

**Case:** AR-2026-003
**Employee:** Rahul Mehta (EMP002)
**Requested role:** Payment Approver (role ID 8)
**Conflict rule:** SoD-01 (Payment Initiator + Payment Approver)
**Tested:** 12 November 2026 18:38:22 UTC
**Evidence:** AR-003-E01, AR-003-E02, AR-003-E03

## Purpose

Demonstrate the SoD preventive control using the implemented Payment Initiator + Payment Approver conflict. Confirm that provisioning is blocked when a conflict exists and that no conflicting access is granted.

## SoD rule reference (implemented)

Source: `app/governance/sod.py` (SOD_CONFLICT_RULES) and `05-SoD-Policy-and-Rules-Register.docx`

| Rule ID | Conflicting roles | Business rationale | Implemented in IdentityGuard |
|---|---|---|---|
| SoD-01 | Payment Initiator + Payment Approver | Whoever creates a payment must not approve it | Yes - enforced at provisioning |
| SoD-02 | System Administrator + SOC Analyst | An administrator must not run the monitoring that watches admins | Yes - enforced at provisioning |
| SoD-03 | Database Administrator + Security Auditor | Whoever administers the database must not audit the platform | Yes - enforced at provisioning |

## Safe test target selection

Rahul Mehta was selected as the test target because he already holds Payment Initiator (a live, pre-existing assignment). Requesting Payment Approver for him creates the SoD-01 conflict. The test is safe because:
- The provisioning is expected to be BLOCKED, so no conflicting access is granted.
- Rahul's existing roles are unchanged.
- No unrelated users or business activity are affected.
- The test uses a controlled access request that remains APPROVED but unprovisioned.

## Test design

| Field | Value |
|---|---|
| Target user | Rahul Mehta (user 2) |
| Target existing role | Payment Initiator (ACTIVE) |
| Requested role | Payment Approver (role ID 8) |
| Expected result | Provisioning blocked by SoD-01 at provision_access_request |
| Access actually granted | None (Payment Approver not assigned) |

## Conclusion

The conflict scenario is designed to demonstrate that IdentityGuard blocks conflicting role grants at provisioning. The request was submitted and approved, then provisioning was attempted and blocked.

**Classification:** Actual lab test. SoD-01 is an implemented IdentityGuard rule.
