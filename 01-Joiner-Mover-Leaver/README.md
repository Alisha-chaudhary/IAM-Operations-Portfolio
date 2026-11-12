# Scenario 1 - Joiner, Mover, Leaver (JML)

**Case ID:** JML-2026-001
**Employee:** Maya Rao (EMP-1001)
**Organisation:** Asteron Financial Services (fictional training organisation)
**Scenario:** Joiner-Mover-Leaver lifecycle

## Purpose

This folder contains the complete portfolio documentation for Scenario 1 (Joiner-Mover-Leaver). It documents the end-to-end IAM lifecycle for one fictional employee, Maya Rao, including joiner intake, identity creation, birth-right access analysis, approvals, SoD validation, provisioning, verification, mover, leaver, termination, and case closure.

## Fictional Scenario Notice

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder actions (HR events, manager endorsements, IAM Administrator approvals) are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

## Structure

```
01-HRIS-Joiner-Event-Notification.md     # Original simulated HR joiner event (E01)
02-HRIS-Joiner-Attribute-Amendment.md    # Simulated HR amendment (E05)
03-HRIS-Mover-Event.md                   # Simulated HR mover event (E15)
04-HRIS-Leaver-Event.md                  # Simulated HR leaver event (E19)
01-Initial-IAM-Intake.md                 # Joiner intake
02-Initial-IAM-Validation-Verdict.md     # Initial validation verdict (E04)
03-Post-Amendment-Validation.md          # Post-amendment validation (E06)
04-RBAC-and-Entitlement-Mapping.md       # Birth-right access mapping (E07)
05-Approval-and-SoD-Validation.md        # Approvals and SoD (E08, E09, E10)
06-Joiner-Provisioning.md                # Joiner provisioning (E11, E12, E13)
07-Joiner-Verification.md                # Joiner verification (E14)
01-Mover-Intake-and-Validation.md        # Mover intake (E15)
02-Access-Review-and-Mapping.md          # Mover access review (E16)
03-Mover-Execution.md                    # Mover execution - blocked (E17)
04-Mover-Verification.md                 # Mover verification (E18)
01-Leaver-Intake-and-Validation.md       # Leaver intake (E19)
02-Pre-Termination-Access-Review.md      # Pre-termination inventory (E20)
03-Termination-Execution.md              # Termination execution (E21)
04-Post-Termination-Verification.md      # Post-termination verification (E22)
Evidence/                                # Sanitised evidence files
  Evidence-Register.md                   # Evidence register (E24 support)
  Exceptions-and-Limitations.md          # Exceptions register
  Final-Scenario-Closure-Report.md       # Case closure report (E24)
  [sanitised API response .txt files]
README.md                                # This file
```

## Key Findings

- **Joiner:** Completed. Maya Rao (EMP-1001) created as user ID 12, ACTIVE, Finance, manager Priya Nair.
- **Birth-right access:** CRM: Relationship Manager + PMS: Portfolio Viewer are proposed Asteron training data, not implemented in IdentityGuard. Handled as manual/target-application controls.
- **Mover:** Blocked. Destination department Investment Operations is not configured in IdentityGuard. Documented as a blocker.
- **Leaver:** Completed. Account terminated (status TERMINATED). Roles expired. Audit event recorded.

## Evidence

24 evidence items collected (JML-001-E01 to JML-001-E24). See `Evidence/Evidence-Register.md`.

## Governance References

Governance documents are held in the IdentityGuard portfolio repository at `00-Governance-Framework/`:
- 01-Access-Control-Policy.docx
- 02-RBAC-Matrix.xlsx
- 03-Entitlement-Catalogue.xlsx
- 04-Approval-Matrix.xlsx
- 05-SoD-Policy-and-Rules-Register.docx
- 06-Provisioning-and-Deprovisioning-SOP.docx
- 07-Exception-Management-SOP.docx

These are referenced, not copied, into this scenario folder.
