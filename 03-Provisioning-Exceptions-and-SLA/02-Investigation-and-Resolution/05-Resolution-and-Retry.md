# Scenario 3 — Resolution and Retry

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Resolved at:** 12 November 2026
**Resolver:** IAM Operations Analyst

## Resolution summary

| Exception ID | Resolution | Status | Access granted? | SoD satisfied? |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Closed — entitlement already held via Request ID 1 | Closed | No (already held) | N/A |
| IAM-EXC-2026-002 | Closed — SoD-01 conflict prevented, no access granted | Closed | No | Yes |
| IAM-EXC-2026-003 | Open — monitoring auto-expiry of time-limited access | Open (monitoring) | Yes (time-limited, expiring) | Yes (no conflict) |

## Resolution details

### IAM-EXC-2026-001

The Finance Manager entitlement was already assigned to Rahul Mehta via Request ID 1 (provisioned 18:36:21). Request ID 4 is a duplicate that cannot be provisioned or rejected through the API. The exception is closed with the decision that no further provisioning is required — the business need is already met.

### IAM-EXC-2026-002

Payment Approver was blocked by SoD-01 because Rahul holds Payment Initiator. No conflicting access was granted. The exception is closed as "conflict prevented." The SOD_VIOLATION audit events (IDs 36 and 48) provide evidence that the control functioned.

### IAM-EXC-2026-003

Sneha Rao's System Administrator access is time-limited and expires at 2026-11-12T19:37:23. The exception remains open for monitoring until expiry. No renewal is required (emergency access). Post-expiry verification will confirm the assignment is expired.

## Retry

No retries were performed. For each case, a retry was evaluated and determined inappropriate:
- EXC-001: Access already held; retry unnecessary.
- EXC-002: SoD blocks the conflicting role; retry would fail and must not grant conflicting access.
- EXC-003: Access self-expires; retry unnecessary.

This follows the SOP guidance not to grant access merely to close an SLA case, and not to retry repeatedly without identifying the cause.

## Verification

Post-resolution verification is documented in 04-Verification-and-Closure/01-Post-Resolution-Verification.md.

## Evidence

- EXC-001-E12, EXC-002-E12, EXC-003-E12: Post-resolution verification
- EXC-001-E13, EXC-002-E13, EXC-003-E13: Audit trail
