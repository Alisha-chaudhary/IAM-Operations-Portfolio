# Scenario 4 — Access Reviews and User Access Certification

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab

## Purpose

This folder contains the complete portfolio documentation for Scenario 4 (Access Reviews and User Access Certification). It demonstrates an end-to-end user access certification review: review cycle creation, identity and role inventory, reviewer assignment with independence, certification decisions (RETAIN/REVOKE), SoD and excessive access findings, remediation (revocation), post-remediation verification, review completion, and audit evidence.

## Fictional scenario notice

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder decisions are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only. Review dates are fictional training dates.

## Results summary

| Metric | Value |
|:---|---|
| Review cycle | ID 1, Asteron Q4 2026 User Access Certification, COMPLETED |
| Users reviewed | 11 active (1 terminated excluded) |
| Review items | 18 |
| RETAIN decisions | 16 |
| REVOKE decisions | 2 |
| Actual revocations | 2 |
| Escalations | 0 |
| Active SoD violations | 0 |

## Structure

```
04-Access-Reviews-and-Certification/
├── README.md                                          # This file
├── 00-Review-Background/
│   ├── 01-Review-Scope.md
│   ├── 02-Review-Policy-and-Criteria.md
│   └── 03-Review-Population.md
├── 01-Review-Preparation/
│   ├── 01-Identity-and-Entitlement-Inventory.md
│   ├── 02-Reviewer-Assignment.md
│   └── 03-Review-Cycle-Creation.md
├── 02-Access-Certification/
│   ├── 01-Certification-Register.md
│   ├── 02-Review-Decisions.md
│   ├── 03-SoD-and-Excessive-Access-Findings.md
│   └── 04-Reviewer-Escalations.md
├── 03-Remediation/
│   ├── 01-Revocation-and-Modification.md
│   ├── 02-Remediation-Tracking.md
│   └── 03-Post-Remediation-Verification.md
├── 04-Review-Closure/
│   ├── 01-Review-Completion.md
│   └── 02-Final-Access-Certification-Report.md
└── Evidence/
    ├── Evidence-Register.md
    ├── Exceptions-and-Limitations.md
    └── [sanitised evidence .txt files]
```

## Evidence

Evidence items referenced by ID (ACR-001-E01 to ACR-001-E14, plus ACR-ALL shared files). See `Evidence/Evidence-Register.md`.

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
