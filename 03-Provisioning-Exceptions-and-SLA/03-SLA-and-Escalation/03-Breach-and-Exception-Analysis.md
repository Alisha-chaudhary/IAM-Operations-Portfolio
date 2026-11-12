# Scenario 3 — Breach and Exception Analysis

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Analysed at:** 12 November 2026
**Analyst:** IAM Operations Analyst

## SLA breach analysis

| Exception ID | Priority | Within SLA? | Breach? | Breach reason | Escalation due to breach |
|---|---|---|---|---|---|
| IAM-EXC-2026-001 | P3 - Medium | Yes | No | N/A | No |
| IAM-EXC-2026-002 | P2 - High | Yes | No | N/A | No |
| IAM-EXC-2026-003 | P3 - Medium | Yes | No | N/A | No |

No SLA breaches occurred. All exceptions were identified, resolved (or placed in monitoring), and documented on the same day, within their training SLA targets.

## Exception analysis by category

| Category | Cases | Outcome |
|---|---|---|
| Provisioning failure — duplicate | IAM-EXC-2026-001 | Closed — entitlement already held |
| Provisioning failure — SoD-blocked | IAM-EXC-2026-002 | Closed — conflict prevented |
| Expiring time-limited access | IAM-EXC-2026-003 | Open — monitoring auto-expiry |

## Key findings

1. **No control failed.** In all three cases, the application behaved as designed: duplicates are rejected at provisioning, SoD conflicts are blocked at provisioning, and time-limited access expires automatically.

2. **Approval precedes SoD evaluation.** Requests can be approved before the SoD check is performed at provisioning. This means an APPROVED request can still fail at provisioning. This is a sequencing characteristic of the IdentityGuard workflow, not a defect.

3. **APPROVED requests are stuck.** Once approved, a request cannot be rejected through the API (reject requires REQUESTED status). If provisioning is also blocked, the request remains APPROVED and unprovisioned indefinitely, resolvable only by documentation. This is an application limitation.

4. **No conflicting access was granted.** The SoD control prevented Payment Approver from being assigned to Rahul (who holds Payment Initiator). /reports/sod-violations shows zero active conflicts.

5. **No access was granted merely to close an SLA case.** Retries were evaluated and determined inappropriate for all three cases.

## Evidence

- EXC-001-E14, EXC-002-E14, EXC-003-E14: Closure records
