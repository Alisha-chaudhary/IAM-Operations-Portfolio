# Evidence Register

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Scenario:** Joiner-Mover-Leaver (Scenario 1)
**Organisation:** Asteron Financial Services (fictional training organisation)

## Evidence Naming Scheme

Evidence IDs follow the format `JML-001-E##`. Each evidence item records:
- Evidence ID
- Evidence title
- Date and time
- Source
- Type (actual lab evidence / simulated stakeholder evidence / policy analysis)
- What it demonstrates
- Related IAM activity
- File path

## Evidence Items

| ID | Title | Date/Time | Source | Type | Demonstrates | Activity | File Path |
|---|---|---|---|---|---|---|---|
| JML-001-E01 | Original simulated HR joiner event | 12 Nov 2026 | Simulated HRIS | Simulated stakeholder | Joiner event received, HR approved | Joiner intake | 01-HRIS-Joiner-Event-Notification.md |
| JML-001-E02 | Initial identity inventory | 12 Nov 2026 | IdentityGuard API (live) | Actual lab | 11 active users, no EMP-1001, no Maya Rao | Joiner validation | E02-pre-joiner-inventory.txt |
| JML-001-E03 | Initial department and manager validation | 12 Nov 2026 | IdentityGuard reference data | Actual lab | Wealth Management not configured; Neha Kapoor not in inventory | Joiner validation | 02-Initial-IAM-Validation-Verdict.md |
| JML-001-E04 | Initial IAM validation verdict | 12 Nov 2026 | IAM Operations Analyst | Actual lab | NOT APPROVED, ON HOLD | Joiner validation | 02-Initial-IAM-Validation-Verdict.md |
| JML-001-E05 | Simulated HR amendment confirmation | 12 Nov 2026 | Simulated HR Operations | Simulated stakeholder | Dept Finance (1), Manager Priya Nair (user 1) | HR clarification | 02-HRIS-Joiner-Attribute-Amendment.md |
| JML-001-E06 | Post-amendment validation | 12 Nov 2026 | IdentityGuard reference data | Actual lab | APPROVED after amendment | Revalidation | 03-Post-Amendment-Validation.md |
| JML-001-E07 | RBAC and entitlement mapping | 12 Nov 2026 | RBAC Matrix, Entitlement Catalogue | Policy analysis | Birth-right access = CRM + PMS (proposed training data) | Birth-right analysis | 04-RBAC-and-Entitlement-Mapping.md |
| JML-001-E08 | Hiring manager endorsement | 12 Nov 2026 | Simulated HR stakeholder | Simulated stakeholder | Manager endorsement for joiner access | Approval | 05-Approval-and-SoD-Validation.md |
| JML-001-E09 | IAM Administrator approval | 12 Nov 2026 | Simulated IAM stakeholder | Simulated stakeholder | IAM Administrator approval for joiner access | Approval | 05-Approval-and-SoD-Validation.md |
| JML-001-E10 | SoD evaluation | 12 Nov 2026 | SoD Policy and Rules Register | Policy analysis | No SoD conflict identified | SoD validation | 05-Approval-and-SoD-Validation.md |
| JML-001-E11 | Joiner creation evidence | 12 Nov 2026 17:57:17Z | IdentityGuard API (live) | Actual lab | User ID 12 created, ACTIVE, Finance, manager Priya Nair | Joiner provisioning | E11-joiner-creation.txt |
| JML-001-E12 | Access request and approval evidence | 12 Nov 2026 | Simulated stakeholder | Simulated stakeholder | No IdentityGuard access requests (target-app controls) | Approval/provisioning | 05-Approval-and-SoD-Validation.md, 06-Joiner-Provisioning.md |
| JML-001-E13 | Provisioning evidence | 12 Nov 2026 | IdentityGuard API (live) | Actual lab | USER_CREATED audit event recorded | Joiner provisioning | E11-joiner-creation.txt, E14-post-joiner-verification.txt |
| JML-001-E14 | Post-provisioning verification | 12 Nov 2026 | IdentityGuard reports | Actual lab | Identity verified, ACTIVE, correct attributes, no roles, no outstanding requests | Joiner verification | E14-post-joiner-verification.txt |
| JML-001-E15 | Simulated mover event | Simulated | Simulated HRIS | Simulated stakeholder | Mover to Investment Operations, Investment Ops Analyst | Mover intake | 03-HRIS-Mover-Event.md |
| JML-001-E16 | Mover access review | 12 Nov 2026 | RBAC Matrix | Policy analysis | No IdentityGuard roles to retain/remove/request | Mover access review | 02-Access-Review-and-Mapping.md |
| JML-001-E17 | Mover execution evidence (blocked) | 12 Nov 2026 | IdentityGuard API (live) | Actual lab | 404 - Department 99 does not exist | Mover execution | mover-blocked-department.txt |
| JML-001-E18 | Post-mover verification | 12 Nov 2026 | IdentityGuard reports | Actual lab | No changes; remains Finance, manager Priya Nair | Mover verification | 04-Mover-Verification.md |
| JML-001-E19 | Simulated leaver event | Simulated | Simulated HRIS | Simulated stakeholder | Leaver effective 30 June 2027 | Leaver intake | 04-HRIS-Leaver-Event.md |
| JML-001-E20 | Pre-termination access inventory | 12 Nov 2026 | IdentityGuard reports | Actual lab | ACTIVE, no roles, no outstanding requests | Leaver pre-termination | E20-pre-termination-inventory.txt |
| JML-001-E21 | Termination execution evidence | 12 Nov 2026 18:15:20Z | IdentityGuard API (live) | Actual lab | Status TERMINATED, terminated_at recorded | Leaver termination | E21-termination-execution.txt |
| JML-001-E22 | Post-termination verification | 12 Nov 2026 | IdentityGuard reports | Actual lab | TERMINATED, roles expired, USER_TERMINATED audit event | Leaver verification | E22-post-termination-verification.txt |
| JML-001-E23 | Audit trail | 12 Nov 2026 | IdentityGuard API (live) | Actual lab | USER_CREATED (event 4), USER_TERMINATED (event 9) | Audit evidence | E14, E22 verification files |
| JML-001-E24 | Final scenario closure report | 12 Nov 2026 | IAM Operations Analyst | Policy analysis | Scenario summary, status, outstanding actions | Case closure | Final-Scenario-Closure-Report.md |

## Evidence File Locations

All evidence files are located in:
- Desktop: `C:\Users\hp\Desktop\IAM-Scenario-1-JML-Completion\`
- Portfolio repo: `01-Joiner-Mover-Leaver/Evidence/`

## Evidence Type Definitions

- **Actual lab evidence:** Generated by executing against the local IdentityGuard API and database. Sanitised API responses and reports.
- **Simulated stakeholder evidence:** Created for the fictional training scenario to represent HR, manager, or IAM Administrator actions. Not real organisational activity.
- **Policy analysis:** Analysis of governance documents (RBAC Matrix, Entitlement Catalogue, Approval Matrix, SoD Policy, Access Control Policy).

## Notes

- No secrets, passwords, or API tokens are included in evidence.
- The seed password used for lab setup is not recorded in evidence.
- API response excerpts are sanitised where necessary (no secrets present).
