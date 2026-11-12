# Scenario 3 — Provisioning Exceptions and SLA Management

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab

## Purpose

This folder contains the complete portfolio documentation for Scenario 3 (Provisioning Exceptions and SLA Management). It demonstrates how an IAM Operations Analyst handles access provisioning exceptions — monitoring access requests, identifying exceptions, investigating provisioning failures and SoD conflicts, tracking SLAs, executing corrective actions, verifying results, and closing cases with evidence.

## Fictional scenario notice

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder actions and SLA targets are explicitly labelled as simulated/training. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

SLA targets are the training targets from the Exception Management SOP (`00-Governance-Framework/07-Exception-Management-SOP.docx`). They are labelled as training targets and are not regulatory requirements or commitments of IdentityGuard or any real organisation.

## Structure

```
03-Provisioning-Exceptions-and-SLA/
├── README.md                                          # This file
├── 00-Scenario-Background/
│   ├── 01-Scenario-Overview.md
│   ├── 02-SLA-Classification-and-Targets.md
│   └── 03-Exception-Handling-Workflow.md
├── 01-Exception-Identification/
│   ├── 01-Access-Request-Monitoring.md
│   ├── 02-Exception-Register.md
│   └── 03-Initial-Triage.md
├── 02-Investigation-and-Resolution/
│   ├── 01-Provisioning-Investigation.md
│   ├── 02-Root-Cause-Analysis.md
│   ├── 03-SoD-Exception-Assessment.md
│   ├── 04-Corrective-Actions.md
│   └── 05-Resolution-and-Retry.md
├── 03-SLA-and-Escalation/
│   ├── 01-SLA-Tracking.md
│   ├── 02-Escalation-Records.md
│   └── 03-Breach-and-Exception-Analysis.md
├── 04-Verification-and-Closure/
│   ├── 01-Post-Resolution-Verification.md
│   └── 02-Scenario-Closure-Report.md
└── Evidence/
    ├── Evidence-Register.md
    ├── Exceptions-and-Limitations.md
    └── [sanitised evidence .txt files]
```

## Case outcomes

| Exception ID | Focus | Priority | Outcome | Status |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Approved-but-unprovisioned duplicate (Finance Manager) | P3 - Medium | Closed — entitlement already held via Request ID 1 | Closed |
| IAM-EXC-2026-002 | SoD-blocked provisioning (Payment Approver vs Payment Initiator) | P2 - High | Closed — conflict prevented, no access granted | Closed |
| IAM-EXC-2026-003 | Time-limited privileged access expiring (System Administrator) | P3 - Medium | Open — monitoring auto-expiry | Open (monitoring) |

## Evidence

Evidence items referenced by ID (EXC-001-E## to EXC-003-E14, plus EXC-ALL shared evidence). See Evidence/Evidence-Register.md.

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
