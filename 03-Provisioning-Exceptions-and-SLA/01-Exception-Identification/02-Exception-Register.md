# Scenario 3 — Exception Register

**Case references:** IAM-EXC-2026-001 to IAM-EXC-2026-003
**Register compiled:** 12 November 2026
**Compiled by:** IAM Operations Analyst
**Priority classification source:** Exception Management SOP training SLA targets (simulated)

## Exception register

| Exception ID | Related request ID | Employee | Username | Access target | Requested entitlement | Exception category | Date/time identified | Status | Severity/priority | Business impact |
|---|---|---|---|---|---|---|---|---|---|---|
| IAM-EXC-2026-001 | Request ID 4 | Rahul Mehta | EMP002 | IdentityGuard (platform) | Finance Manager (finance-ledger:read) | Provisioning failure — duplicate entitlement | 12 Nov 2026 18:52 | Closed (resolved by circumstance) | P3 - Medium | None — entitlement already held via Request ID 1 |
| IAM-EXC-2026-002 | Request ID 3 | Rahul Mehta | EMP002 | IdentityGuard (platform) | Payment Approver (payments-system:approve) | SoD conflict — provisioning blocked | 12 Nov 2026 18:53 | Closed (conflict prevented) | P2 - High | None — conflicting access not granted |
| IAM-EXC-2026-003 | Request ID 2 | Sneha Rao | EMP003 | IdentityGuard (platform) | System Administrator (PROD-LINUX-01:admin, PROD-WIN-01:admin) | Expiring time-limited privileged access | 12 Nov 2026 18:53 | Open — monitoring | P3 - Medium | Low — emergency access self-expires |

## Register details

| Exception ID | Root cause | Assigned owner | Required action | SLA target | SLA due time | Escalation status | Evidence refs | Closure decision |
|---|---|---|---|---|---|---|---|---|
| IAM-EXC-2026-001 | Request approved for an entitlement already assigned (duplicate). Provisioning returns 409; reject returns 409 (already decided). | IAM Operations Analyst | Document that Finance Manager is already held via Request ID 1; close as superseded. No further provisioning required. | P3 - Medium: 1 biz day response / 3 biz days resolution | Start of next business day (13 Nov 2026 09:00) | Not escalated — resolved by circumstance | EXC-001-E01 to EXC-001-E14 | Closed — entitlement already assigned; request moot |
| IAM-EXC-2026-002 | SoD-01 conflict: Payment Approver conflicts with Rahul's existing Payment Initiator. Provisioning blocked; request stuck APPROVED. | IAM Operations Analyst | Document SoD-01 block; do not grant conflicting access. Close as conflict prevented. | P2 - High: 4 biz hours response / 1 biz day resolution | Start of next business day (13 Nov 2026 09:00) | Not escalated — blocked by preventive control | EXC-002-E01 to EXC-002-E14 | Closed — conflicting access not granted; SoD control effective |
| IAM-EXC-2026-003 | Time-limited privileged access (System Administrator) auto-expires at 19:37:23. No renewal required (emergency access). | IAM Operations Analyst | Monitor until auto-expiry. Verify post-expiry that assignment is expired. No renewal. | P3 - Medium: 1 biz day response / 3 biz days resolution | Expiry at 19:37:23 on 12 Nov 2026 | Not escalated — self-resolving | EXC-003-E01 to EXC-003-E14 | Open — monitoring until expiry |

## Numbering

Case references continue the numbering established in prior scenarios. IAM-EXC-2026-001 to IAM-EXC-2026-003 are the three exceptions in this scenario. No additional cases were created.

## Distinction: exception vs provisioning failure

Not every provisioning attempt that returns an error is a business exception:
- Request ID 4 and Request ID 3 are genuine exceptions because they are APPROVED but cannot complete provisioning, and the stuck state needs operational handling and documentation.
- The SoD block on Request ID 3 is a preventive control working as intended (no conflicting access granted), so it is recorded as "conflict prevented" rather than a production incident.
