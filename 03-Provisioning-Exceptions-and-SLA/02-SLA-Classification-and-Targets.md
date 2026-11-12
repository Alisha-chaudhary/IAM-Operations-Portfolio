# Scenario 3 — SLA Classification and Targets

**Source:** Exception Management SOP (`00-Governance-Framework/07-Exception-Management-SOP.docx`), Section 2 — Training SLA targets
**Classification:** Training targets (simulated) — not regulatory requirements or real organisational commitments

## SLA training target table

The Exception Management SOP states: "SLA targets in this document are training targets defined for the Asteron practical exercises. They are not regulatory requirements and not commitments of IdentityGuard or any real organisation."

| Priority | Definition (from SOP) | Training SLA target (initial response) | Training SLA target (resolution) |
|---|---|---|---|
| P1 - Critical | Urgent leaver; active SoD conflict in production; failed termination leaving access live | 1 business hour | 4 business hours |
| P2 - High | Provisioning failure; incorrect entitlement assignment; pending approval blocking business need | 4 business hours | 1 business day |
| P3 - Medium | Missing or invalid approval; delayed request; directory synchronisation mismatch | 1 business day | 3 business days |
| P4 - Low | General enquiry; low-risk documentation gap | 2 business days | 5 business days |

## Business hours assumption

For SLA calculations, business hours are assumed to be 09:00–17:00, Monday–Friday. This is a scenario-specific working assumption for the training exercise and is labelled as such. The IdentityGuard application itself does not enforce business-hour SLAs; SLA tracking is an operational (manual) control.

## How SLAs are applied in this scenario

All three exceptions were identified on 12 November 2026 after 17:00 (end of business day). Under the business-hours assumption, the SLA clock effectively starts at 09:00 on the next business day (13 November 2026). This is noted in the SLA tracking report.

## Priority classification used

| Exception | Priority | Rationale |
|---|---|---|
| IAM-EXC-2026-001 (Request ID 4 — duplicate, access already held) | P3 - Medium | Approved-but-unprovisioned request, but the entitlement is already assigned so there is no business disruption. Administrative cleanup and formal closure required. |
| IAM-EXC-2026-002 (Request ID 3 — SoD-01 blocked) | P2 - High | Provisioning failure caused by an SoD conflict. No conflicting access was granted (blocked at provisioning), so it is not an active production conflict (which would be P1-Critical). |
| IAM-EXC-2026-003 (Request ID 2 — time-limited access expiring) | P3 - Medium | Time-limited privileged access approaching auto-expiry. Monitoring only; no renewal required. Self-resolving control. |

## Distinction: training SLA vs real commitment

These SLA values come from the governance document's own statement that they are training targets. They are presented in this portfolio as simulated operational targets, not as actual organisational SLAs. The IdentityGuard application does not implement server-side SLA tracking or automatic breach escalation; SLA monitoring is a manual, procedural control performed by the IAM Operations Analyst.
