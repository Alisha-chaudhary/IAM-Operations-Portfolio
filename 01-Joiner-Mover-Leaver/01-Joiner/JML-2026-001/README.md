# Case JML-2026-001 - Maya Rao (EMP-1001)

**Case reference:** JML-2026-001  
**Employee:** Maya Rao, Employee ID EMP-1001  
**Organisation:** Asteron Financial Services (fictional training organisation)  
**Lifecycle:** Joiner, Mover, Leaver (Scenario 1)

## Case overview

This case documents the complete Joiner-Mover-Leaver lifecycle for Maya Rao, from joiner intake (12 November 2026) through leaver termination. The case began with an approved HR joiner event (HR-JNR-2026-001) that was placed on hold after initial IAM validation failed department and manager checks. Following a simulated HR attribute amendment, the case was revalidated and the identity was created in the local IdentityGuard lab.

## Case status

| Phase | Status |
|---|---|
| Joiner intake and validation | Completed (initial hold, then approved after amendment) |
| Identity creation | Completed (user ID 12, ACTIVE, Finance, manager Priya Nair) |
| Birth-right access analysis | Completed (proposed training-data entitlements, not in IdentityGuard) |
| Approval validation | Completed (simulated stakeholder approvals) |
| SoD validation | Completed (no conflict) |
| Access provisioning | Completed (no IdentityGuard roles; target-app controls) |
| Post-provisioning verification | Completed |
| Mover | Blocked (destination department Investment Operations not configured) |
| Leaver | Completed (account TERMINATED, roles expired) |
| Post-termination verification | Completed |
| Case closure | Completed |

## Documents in this case folder

| File | Evidence | Description |
|---|---|---|
| `01-HRIS-Original-Joiner-Event.md` | JML-001-E05 | Simulated HR attribute amendment (Finance, Priya Nair) |
| `03-IdentityGuard-Reference-Data-Snapshot.md` | JML-001-E02/E03 | Live IdentityGuard reference data and identity inventory |
| `04-Post-Amendment-Validation.md` | JML-001-E06 | Revalidation after HR amendment |
| `05-RBAC-and-Entitlement-Mapping.md` | JML-001-E07 | Birth-right access analysis using RBAC Matrix and Entitlement Catalogue |
| `06-Approval-and-SoD-Validation.md` | JML-001-E08/E09/E10 | Approvals and SoD validation |
| `07-Joiner-Provisioning.md` | JML-001-E11/E12/E13 | Identity creation and provisioning evidence |
| `08-Joiner-Verification.md` | JML-001-E14 | Post-provisioning verification |

## Related case documents

| File | Evidence | Description | Location |
|---|---|---|---|
| `01-HRIS-Joiner-Event-Notification.md` | JML-001-E01 | Original simulated HR joiner event | `00-Scenario-Background/` |
| `00-IAM Validation Verdict.md` | JML-001-E04 | Initial IAM validation verdict (NOT APPROVED, ON HOLD) | `01-Joiner-Mover-Leaver/` root |
| Mover documents | JML-001-E15/E16/E17/E18 | Mover intake, access review, execution (blocked), verification | `02-Mover/` |
| Leaver documents | JML-001-E19/E20/E21/E22 | Leaver intake, pre-termination review, termination, verification | `03-Leaver/` |
| Evidence register | JML-001-E24 support | Complete evidence register | `Evidence/` |
| Exceptions and limitations | — | Exceptions and limitations register | `Evidence/` |
| Closure report | JML-001-E24 | Final scenario closure report | `Evidence/` |

## Classification

This is a fictional training scenario. All simulated stakeholder actions (HR events, manager endorsements, IAM Administrator approvals) are explicitly labelled as simulated. This is not a real organisational event. IdentityGuard is a local IAM governance and operations lab, not a production SailPoint deployment.
