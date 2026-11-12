# Standard Access Request - Post-Provisioning Verification

**Case:** AR-2026-001
**Employee:** Rahul Mehta (EMP002)
**Verified:** 12 November 2026 18:36:31 UTC
**Verifier:** IAM Operations Analyst
**Evidence:** AR-001-E09

## Purpose

Verify the resulting access after provisioning using the supported IdentityGuard reports and endpoints.

## Verification results

| Check | Expected | Actual | Result |
|---|---|---|---|
| Request status | PROVISIONED | PROVISIONED | PASS |
| Approval status | APPROVED | APPROVED (decision_by: identityguard.admin2) | PASS |
| Provisioning status | PROVISIONED | PROVISIONED (provisioned_at recorded) | PASS |
| Target user | Rahul Mehta (user 2) | Rahul Mehta | PASS |
| Role assigned | Finance Manager | Finance Manager (ACTIVE) | PASS |
| Only approved access assigned | Finance Manager only (new) | Finance Manager added; no extra roles | PASS |
| SoD status | No conflict | 0 SoD violations | PASS |
| Audit evidence | REQUESTED, APPROVED, PROVISIONED events | All three events present | PASS |
| No outstanding request remains | Request 1 resolved | Request 1 is PROVISIONED (closed) | PASS |

## Rahul's role assignments after provisioning

| Role | Status |
|---|---|
| Finance Analyst | ACTIVE (pre-existing) |
| Payment Initiator | ACTIVE (pre-existing) |
| Finance Manager | ACTIVE (newly provisioned) |

## Audit trail for Request ID 1

| Event ID | Timestamp | Actor | Event Type | Target | Result |
|---:|---|---|---|---|---|
| 16 | 2026-11-12T18:35:53 | identityguard.admin | ACCESS_REQUESTED | rahul.mehta | SUCCESS |
| 18 | 2026-11-12T18:36:04 | identityguard.admin2 | ACCESS_APPROVED | 1 | SUCCESS |
| 21 | 2026-11-12T18:36:21 | identityguard.admin | ACCESS_PROVISIONED | rahul.mehta | SUCCESS |

## Conclusion

Post-provisioning verification passed. Rahul Mehta now holds Finance Manager in addition to his pre-existing Finance Analyst and Payment Initiator roles. Only the approved access was assigned. No SoD conflict. Audit evidence exists for the full request lifecycle. The request is closed.

**Evidence reference:** AR-001-E09

**Classification:** Actual lab verification.
