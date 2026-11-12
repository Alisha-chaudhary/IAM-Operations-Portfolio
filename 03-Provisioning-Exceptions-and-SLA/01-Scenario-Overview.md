# Scenario 3 — Provisioning Exceptions and SLA Management: Overview

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003
**Organisation:** Asteron Financial Services (fictional training organisation)
**Application:** IdentityGuard local IAM governance lab (`http://127.0.0.1:8000`)
**Scenario date:** 12 November 2026

## Purpose

This scenario demonstrates the responsibilities of an IAM Operations Analyst when access provisioning encounters exceptions. The objective is to show that access is not granted merely because someone requests it, and that provisioning failures, SoD conflicts, and expiring access are identified, investigated, resolved (or documented as unresolvable), and closed with evidence.

The scenario demonstrates:
- Monitoring access requests and identifying exceptions
- Distinguishing normal pending requests from genuine provisioning failures
- Validating request details, approval status, and requested entitlements
- Investigating provisioning failures and SoD conflicts
- Assessing business impact and urgency
- Tracking SLA timelines
- Identifying cases requiring escalation
- Coordinating with simulated business approvers, IAM Administrators, and application owners
- Documenting investigation findings and root causes
- Executing approved corrective actions where supported
- Verifying resulting access
- Maintaining an audit trail
- Closing resolved cases or documenting why they remain open

## Connection to preceding scenarios

Scenario 3 reuses access requests created during Scenario 2 (Access Requests and Provisioning). No new identities or duplicate access requests were created to populate this scenario. The three exception cases are real requests left in an unresolved state after Scenario 2 completed:

| Scenario 2 request | Employee | Role | Status | Why it is an exception |
|---|---|---|---|---|
| Request ID 4 | Rahul Mehta (EMP002) | Finance Manager | APPROVED, unprovisioned | Duplicate — Rahul already holds Finance Manager via Request ID 1 |
| Request ID 3 | Rahul Mehta (EMP002) | Payment Approver | APPROVED, unprovisioned | SoD-01 conflict — Rahul already holds Payment Initiator |
| Request ID 2 | Sneha Rao (EMP003) | System Administrator | PROVISIONED, time-limited | Expiring privileged access — auto-expires 2026-11-12T19:37:23 |

## Classification

Asteron Financial Services is a fictional organisation created exclusively for training and portfolio demonstration. All simulated stakeholder actions are explicitly labelled as simulated. This is not a real organisational event. No production SailPoint experience is claimed. This is IdentityGuard lab execution only.

SLA targets used in this scenario are the **training SLA targets** defined in the Exception Management SOP (07-Exception-Management-SOP.docx). They are labelled as training targets and are not regulatory requirements or commitments of IdentityGuard or any real organisation.

## Evidence

Evidence files are stored in the Evidence/ folder and referenced by ID (EXC-001-E## to EXC-003-E##). See Evidence/Evidence-Register.md.

## Documentation structure

```
03-Provisioning-Exceptions-and-SLA/
├── README.md
├── 00-Scenario-Background/
├── 01-Exception-Identification/
├── 02-Investigation-and-Resolution/
├── 03-SLA-and-Escalation/
├── 04-Verification-and-Closure/
└── Evidence/
```
