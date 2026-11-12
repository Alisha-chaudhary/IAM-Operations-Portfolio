# Scenario 2 - Access Requests and Provisioning

**Case references:** AR-2026-001, AR-2026-002, AR-2026-003, AR-2026-004
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab

## Purpose

This folder contains the complete portfolio documentation for Scenario 2 (Access Requests and Provisioning). It demonstrates the operational handling of employee access requests through the governed IdentityGuard access-request, approval and provisioning workflow, showing that access is not granted merely because someone requests it.

## Fictional scenario notice

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder actions (manager endorsements, IAM Administrator approvals) are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

## Structure

```
02-Access-Requests-and-Provisioning/
├── README.md                                          # This file
├── 00-Scenario-Background/
│   ├── 01-Scenario-Objectives.md
│   └── 02-Identity-and-Role-Reference.md
├── 01-Standard-Access-Request/                        # AR-2026-001
│   ├── 01-Requester-and-Identity-Validation.md
│   ├── 02-Request-Intake-and-Justification.md
│   ├── 03-RBAC-and-Entitlement-Validation.md
│   ├── 04-Approval-and-SoD-Validation.md
│   ├── 05-Provisioning-Execution.md
│   └── 06-Post-Provisioning-Verification.md
├── 02-Privileged-Access-Request/                      # AR-2026-002
│   ├── 01-Request-and-Eligibility-Validation.md
│   ├── 02-Approval-and-Four-Eyes-Control.md
│   └── 03-Provisioning-and-Verification.md
├── 03-SoD-Conflict-Handling/                          # AR-2026-003
│   ├── 01-Conflict-Scenario.md
│   └── 02-Validation-and-Outcome.md
├── 04-Exceptions-and-Failures/                        # AR-2026-004
│   └── 01-Exception-Analysis.md
└── Evidence/
    ├── Evidence-Register.md
    ├── Exceptions-and-Limitations.md
    ├── Final-Scenario-Closure-Report.md
    └── [sanitised evidence .txt files]
```

## Case outcomes

| Case | Focus | Outcome |
|---|---|---|
| AR-2026-001 | Standard access (Rahul -> Finance Manager) | Provisioned |
| AR-2026-002 | Privileged access four-eyes (sneha -> System Administrator, time-limited) | Provisioned (time-limited) |
| AR-2026-003 | SoD conflict (Rahul -> Payment Approver) | Blocked (SoD-01) |
| AR-2026-004 | Exception handling | All exceptions confirmed |

## Evidence

13 evidence items collected. See Evidence/Evidence-Register.md.

## Governance references

Governance documents are held in the IdentityGuard portfolio repository at `00-Governance-Framework/`:
- 01-Access-Control-Policy.docx
- 02-RBAC-Matrix.xlsx
- 03-Entitlement-Catalogue.xlsx
- 04-Approval-Matrix.xlsx
- 05-SoD-Policy-and-Rules-Register.docx
- 06-Provisioning-and-Deprovisioning-SOP.docx
- 07-Exception-Management-SOP.docx

These are referenced, not copied, into this scenario folder.
