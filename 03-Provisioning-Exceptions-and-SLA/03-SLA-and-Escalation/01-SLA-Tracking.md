# Scenario 3 — SLA Tracking Report

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Tracked at:** 12 November 2026
**Tracker:** IAM Operations Analyst
**SLA source:** Exception Management SOP training SLA targets (simulated)

## SLA training targets (simulated)

| Priority | Initial response | Resolution |
|---|---|---|
| P1 - Critical | 1 business hour | 4 business hours |
| P2 - High | 4 business hours | 1 business day |
| P3 - Medium | 1 business day | 3 business days |
| P4 - Low | 2 business days | 5 business days |

Source: `00-Governance-Framework/07-Exception-Management-SOP.docx`, Section 2. Labelled as training targets — not regulatory requirements or real organisational commitments.

## Business hours assumption

Business hours assumed 09:00–17:00, Monday–Friday. All exceptions were identified on 12 November 2026 after 17:00, so the SLA clock effectively starts at 09:00 on 13 November 2026 (next business day). This is a scenario-specific working assumption.

## SLA tracking per exception

| Exception ID | Priority | Identified | Initial response due | Resolution due | Status at tracking | SLA outcome |
|---|---|---|---|---|---|---|
| IAM-EXC-2026-001 | P3 - Medium | 12 Nov 2026 18:52 | 13 Nov 2026 (1 biz day) | 16 Nov 2026 (3 biz days) | Closed | Within SLA (closed same day) |
| IAM-EXC-2026-002 | P2 - High | 12 Nov 2026 18:53 | 13 Nov 2026 13:00 (4 biz hours) | 13 Nov 2026 17:00 (1 biz day) | Closed | Within SLA (closed same day) |
| IAM-EXC-2026-003 | P3 - Medium | 12 Nov 2026 18:53 | 13 Nov 2026 (1 biz day) | 16 Nov 2026 (3 biz days) | Open (monitoring) | Within SLA (monitoring) |

## SLA calculation notes

- All three exceptions were identified and resolved (or placed in monitoring) on the same day they were identified (12 November 2026), well within their training SLA targets.
- EXC-003 remains open for monitoring because the access self-expires at 19:37:23 on 12 November 2026. This is within the P3 resolution window and is not a breach.
- No SLA breaches occurred in this scenario.

## Application limitation

IdentityGuard does not implement server-side SLA tracking or automatic breach escalation. SLA tracking is a manual, procedural control performed by the IAM Operations Analyst. The timestamps above are derived from live API responses (requested_at, decided_at, provisioned_at, expires_at) and the monitoring capture time.

## Evidence

- EXC-001-E08, EXC-002-E08, EXC-003-E08: SLA assessment
