# Evidence Register

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Scenario:** Provisioning Exceptions and SLA Management (Scenario 3)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Compiled:** 12 November 2026
**Compiled by:** IAM Operations Analyst

## Evidence naming scheme

Evidence IDs follow the format `EXC-###-E##`. For shared evidence spanning all cases, the prefix `EXC-ALL` is used. Each evidence item records:
- Evidence ID
- Evidence title
- Date and time
- Source
- Type (actual lab evidence / simulated stakeholder evidence / policy analysis)
- What it demonstrates
- Related IAM activity
- File path

## Evidence items

| ID | Title | Date/time | Source | Type | Demonstrates | Activity | File path |
|---|---|---|---|---|---|---|---|
| EXC-ALL-E01 | Access request inventory (all requests) | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | All four access requests and their status | Access request monitoring | Evidence/EXC-ALL-E01-access-request-inventory.txt |
| EXC-ALL-E02 | Role access assignments report | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | Current role assignments incl. expires_at | Role assignment review | Evidence/EXC-ALL-E02-role-access-assignments.txt |
| EXC-ALL-E03 | SoD violations report | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | Zero active SoD conflicts | SoD validation | Evidence/EXC-ALL-E03-sod-violations.txt |
| EXC-ALL-E04 | Audit trail (last 40 events) | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | SOD_VIOLATION, ACCESS_REQUESTED, ACCESS_APPROVED events | Audit trail review | Evidence/EXC-ALL-E04-audit-trail.txt |
| EXC-ALL-E05 | User inventory | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | User identities, status, departments | Identity validation | Evidence/EXC-ALL-E05-user-inventory.txt |
| EXC-001-E01 | Exception identification — Request ID 4 | 12 Nov 2026 18:52 | IdentityGuard API (live) | Actual lab evidence | Request ID 4 APPROVED, unprovisioned | Exception identification | 01-Exception-Identification/01-Access-Request-Monitoring.md |
| EXC-001-E02 | Initial triage — Request ID 4 | 12 Nov 2026 18:52 | IAM Operations Analyst | Policy analysis | Duplicate entitlement; stuck APPROVED | Initial triage | 01-Exception-Identification/03-Initial-Triage.md |
| EXC-001-E05 | Provisioning investigation — Request ID 4 | 12 Nov 2026 18:52 | IdentityGuard API (live) | Actual lab evidence | 409 duplicate; cannot reject | Provisioning investigation | 02-Investigation-and-Resolution/01-Provisioning-Investigation.md |
| EXC-001-E07 | Root cause analysis — EXC-001 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Duplicate (data/operational); no control failed | Root cause analysis | 02-Investigation-and-Resolution/02-Root-Cause-Analysis.md |
| EXC-001-E08 | SLA assessment — EXC-001 | 12 Nov 2026 | Exception Management SOP targets | Policy analysis | P3-Medium; within SLA | SLA tracking | 03-SLA-and-Escalation/01-SLA-Tracking.md |
| EXC-001-E10 | Corrective action — EXC-001 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Close as superseded; access already held | Corrective actions | 02-Investigation-and-Resolution/04-Corrective-Actions.md |
| EXC-001-E11 | Retry evaluation — EXC-001 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Retry not performed (access already held) | Retry evaluation | 02-Investigation-and-Resolution/05-Resolution-and-Retry.md |
| EXC-001-E12 | Post-resolution verification — EXC-001 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | No duplicate; single Finance Manager | Post-resolution verification | 04-Verification-and-Closure/01-Post-Resolution-Verification.md |
| EXC-001-E13 | Audit trail — EXC-001 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | ACCESS_REQUESTED, ACCESS_APPROVED for Request 4 | Audit trail | 04-Verification-and-Closure/01-Post-Resolution-Verification.md |
| EXC-001-E14 | Closure record — EXC-001 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Closed — entitlement already held | Case closure | 04-Verification-and-Closure/02-Scenario-Closure-Report.md |
| EXC-002-E01 | Exception identification — Request ID 3 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | Request ID 3 APPROVED, unprovisioned | Exception identification | 01-Exception-Identification/01-Access-Request-Monitoring.md |
| EXC-002-E02 | Initial triage — Request ID 3 | 12 Nov 2026 18:53 | IAM Operations Analyst | Policy analysis | SoD-01 conflict; stuck APPROVED | Initial triage | 01-Exception-Identification/03-Initial-Triage.md |
| EXC-002-E05 | Provisioning investigation — Request ID 3 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | 409 SoD block; 409 reject (already decided) | Provisioning investigation | 02-Investigation-and-Resolution/01-Provisioning-Investigation.md |
| EXC-002-E06 | SoD validation — EXC-002 | 12 Nov 2026 | SoD Policy and Rules Register | Policy analysis | SoD-01 enforced; no conflict granted | SoD validation | 02-Investigation-and-Resolution/03-SoD-Exception-Assessment.md |
| EXC-002-E07 | Root cause analysis — EXC-002 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | SoD preventive control functioned | Root cause analysis | 02-Investigation-and-Resolution/02-Root-Cause-Analysis.md |
| EXC-002-E08 | SLA assessment — EXC-002 | 12 Nov 2026 | Exception Management SOP targets | Policy analysis | P2-High; within SLA | SLA tracking | 03-SLA-and-Escalation/01-SLA-Tracking.md |
| EXC-002-E10 | Corrective action — EXC-002 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Close as conflict prevented | Corrective actions | 02-Investigation-and-Resolution/04-Corrective-Actions.md |
| EXC-002-E11 | Retry evaluation — EXC-002 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Retry not performed (SoD blocks) | Retry evaluation | 02-Investigation-and-Resolution/05-Resolution-and-Retry.md |
| EXC-002-E12 | Post-resolution verification — EXC-002 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | Payment Approver not granted; sod-violations = 0 | Post-resolution verification | 04-Verification-and-Closure/01-Post-Resolution-Verification.md |
| EXC-002-E13 | Audit trail — EXC-002 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | SOD_VIOLATION events 36, 48 (DENIED) | Audit trail | 04-Verification-and-Closure/01-Post-Resolution-Verification.md |
| EXC-002-E14 | Closure record — EXC-002 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Closed — conflict prevented | Case closure | 04-Verification-and-Closure/02-Scenario-Closure-Report.md |
| EXC-003-E01 | Exception identification — Request ID 2 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | Request ID 2 PROVISIONED, time-limited | Exception identification | 01-Exception-Identification/01-Access-Request-Monitoring.md |
| EXC-003-E02 | Initial triage — Request ID 2 | 12 Nov 2026 18:53 | IAM Operations Analyst | Policy analysis | Expiring access; ~44 min remaining | Initial triage | 01-Exception-Identification/03-Initial-Triage.md |
| EXC-003-E08 | SLA assessment — EXC-003 | 12 Nov 2026 | Exception Management SOP targets | Policy analysis | P3-Medium; monitoring | SLA tracking | 03-SLA-and-Escalation/01-SLA-Tracking.md |
| EXC-003-E12 | Post-resolution verification — EXC-003 | 12 Nov 2026 18:53 | IdentityGuard API (live) | Actual lab evidence | System Administrator active with expires_at | Post-resolution verification | 04-Verification-and-Closure/01-Post-Resolution-Verification.md |
| EXC-003-E14 | Closure record — EXC-003 | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Open — monitoring until expiry | Case closure | 04-Verification-and-Closure/02-Scenario-Closure-Report.md |

## Evidence type definitions

- **Actual lab evidence:** Generated by executing against the local IdentityGuard API and database. Sanitised API responses and reports (no secrets).
- **Simulated stakeholder evidence:** Created for the fictional training scenario to represent stakeholder communications. None were actually executed; all labelled simulated.
- **Policy analysis:** Analysis of governance documents (Exception Management SOP, SoD Register, RBAC Matrix, Entitlement Catalogue, Approval Matrix, Access Control Policy).

## Evidence file locations

All evidence files are located in:
- Desktop: `C:\Users\hp\Desktop\IAM-Scenario-3-Exceptions-SLA-Completion\`
- Portfolio repo: `03-Provisioning-Exceptions-and-SLA/`

## Notes

- Evidence IDs EXC-001-E03, EXC-001-E04, EXC-001-E09, EXC-002-E01(exception identification is E01), EXC-002-E03, EXC-002-E04, EXC-003-E03, EXC-003-E04, EXC-003-E05, EXC-003-E06, EXC-003-E07, EXC-003-E09, EXC-003-E10, EXC-003-E11 are represented by the corresponding documentation files rather than separate text files, to avoid duplication.
- No secrets, passwords, or API tokens are included in evidence.
- The capture_evidence.py and exec_*.py working scripts are not evidence and are not part of the portfolio.
