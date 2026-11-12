# IAM Operations Portfolio — Asteron Financial Services

**Identity and Access Management governance and operations documentation pack**
**Entry-level IAM / Access Management / SailPoint Provisioning Operations portfolio**

---

## Purpose

This documentation pack supports five practical IAM operations scenarios that are executed and documented separately (Joiner/Mover/Leaver, Access Requests and Provisioning, Provisioning Exceptions and SLA, Access Certification and SoD, Reconciliation and Audit).

It provides a connected set of professional IAM governance and operational documents for the fictional organisation **Asteron Financial Services**, grounded in the actual implementation of the **IdentityGuard** IAM governance application.

---

## Fictional organisation (training data only)

**Asteron Financial Services** is a fictional organisation created exclusively for training and portfolio demonstration.

- Its policies are **not** real corporate policies.
- It is **not** associated with EY or any other organisation.
- No signatures, approvals, certifications or corporate authorisation are fabricated.
- All documents carry `Status: Training Reference` and `Organisation: Asteron Financial Services (Fictional)`.

### Business environment (fictional)
- Wealth Management
- Investment Operations
- Compliance
- Human Resources
- IT

### Fictional business applications (proposed training data)
- Customer Relationship Management (CRM)
- Portfolio Management System (PMS)
- Trade Operations Portal
- Compliance Case Management (CCM)
- HR Management System (HRMS)

These applications and their entitlements are **proposed Asteron training data** and are labelled as such throughout the pack. They are **not** IdentityGuard records.

### Main scenario subject (fictional)
- **Maya Rao**, Employee ID **EMP-1001**, Hyderabad, Full-time
- Initial department: Wealth Management — Relationship Manager
- Manager: Neha Kapoor — Join date: 17 November 2026
- Mover date: 1 February 2027 — Investment Operations Analyst, Investment Operations
- Leaver date: 30 June 2027

Maya's Joiner / Mover / Leaver access is logically consistent across all documents.

---

## Source repository

**IdentityGuard:** https://github.com/Alisha-chaudhary/IdentityGuard  
A Python/FastAPI IAM governance lab (SQLAlchemy, SQLite, Pytest, React). Status: in active development. The repository was inspected in full (source code, database models, seed data, policy files, LDAP/PAM/Vault integrations, tests, and documentation) before this pack was written.

**Important:** No application code was modified, no new APIs/scripts/modules were introduced, and the existing database was not changed, reset, seeded or deleted.

### Repository findings report
`00-Repository-Assessment/IdentityGuard-Repository-Findings.md`

This report is the evidence base for the pack. It documents the verified repository contents (schema, seed users/roles/permissions, workflows, SoD rules, access reviews, audit, LDAP, Vault, implemented vs. designed-only features, gaps) with source file paths for every major conclusion.

---

## Actual vs. proposed functionality

A central requirement of this pack is to distinguish:

| Category | Meaning |
|----------|---------|
| **Implemented (IdentityGuard)** | Capability verified in the IdentityGuard source code and tests. Technical names (roles, permissions, resources, event types) are retained verbatim. |
| **Designed-only / planned / unimplemented** | Features described in IdentityGuard documentation or roadmap but not implemented; not presented as operational. |
| **Proposed — Asteron training data** | Fictional business applications, roles and entitlements created for the five training scenarios. Clearly labelled; not IdentityGuard records. |
| **Manual / simulated** | Organisational procedures operated in ServiceNow PDI, Excel or Word/PDF because IdentityGuard does not implement them. |

**No planned or unimplemented feature is described as an operational IdentityGuard capability.**

Key IdentityGuard limitations observed and reflected in this pack:
- PAM is **simulated** (request / approve / time-limited checkout / expiry); no credential vault, password rotation or session recording.
- LDAP integration is **OpenLDAP only, read-only, dry-run by default, controlled apply**. **Active Directory is NOT implemented** and is not described as Active Directory.
- IdentityGuard supports a **single approver per access request**; multi-stage chains are operated manually or in ServiceNow PDI.
- Access reviews are created **on demand**; there is no scheduled recurring review.
- No ServiceNow integration exists in the repository; none is claimed or fabricated.
- No migration framework (Alembic); SQLite `create_all()` only.
- No server-side token revocation; logout is client-side.

---

## Document pack structure

```
IAM-Operations-Portfolio/
├── 00-Repository-Assessment/
│   └── IdentityGuard-Repository-Findings.md     # Evidence base (repository investigation)
├── 00-Governance-Framework/
│   ├── 01-Access-Control-Policy.docx            # Formal Access Control Policy
│   ├── 02-RBAC-Matrix.xlsx                      # Role-Based Access Control matrix
│   ├── 03-Entitlement-Catalogue.xlsx            # Entitlement inventory
│   ├── 04-Approval-Matrix.xlsx                  # Approval matrix for access requests
│   ├── 05-SoD-Policy-and-Rules-Register.docx    # SoD policy and rules register
│   ├── 06-Provisioning-and-Deprovisioning-SOP.docx   # Provisioning SOP (intake to closure)
│   └── 07-Exception-Management-SOP.docx         # Exception Management SOP
├── 01-Joiner-Mover-Leaver/
│   ├── README.md                                 # Scenario 1 overview and navigation
│   ├── 00-Scenario-Background/
│   │   ├── 01-HRIS-Joiner-Event-Notification.md  # Original simulated HR joiner event
│   │   ├── 02-HRIS-Joiner-Attribute-Amendment.md # Simulated HR amendment confirmation
│   │   ├── 03-HRIS-Mover-Event.md                # Simulated HR mover event
│   │   └── 04-HRIS-Leaver-Event.md               # Simulated HR leaver event
│   ├── 01-Joiner/
│   │   ├── 01-Initial-IAM-Intake.md
│   │   ├── 02-Initial-IAM-Validation-Verdict.md
│   │   ├── 03-Post-Amendment-Validation.md
│   │   ├── 04-RBAC-and-Entitlement-Mapping.md
│   │   ├── 05-Approval-and-SoD-Validation.md
│   │   ├── 06-Joiner-Provisioning.md
│   │   └── 07-Joiner-Verification.md
│   ├── 02-Mover/
│   │   ├── 01-Mover-Intake-and-Validation.md
│   │   ├── 02-Access-Review-and-Mapping.md
│   │   ├── 03-Mover-Execution.md
│   │   └── 04-Mover-Verification.md
│   ├── 03-Leaver/
│   │   ├── 01-Leaver-Intake-and-Validation.md
│   │   ├── 02-Pre-Termination-Access-Review.md
│   │   ├── 03-Termination-Execution.md
│   │   └── 04-Post-Termination-Verification.md
│   └── Evidence/
│       ├── Evidence-Register.md
│       ├── Exceptions-and-Limitations.md
│       ├── Final-Scenario-Closure-Report.md
│       └── [sanitised evidence files]
└── README.md                                     # This file
```

### Document conventions
- **DOCX** for formal policies and SOPs (each includes Document ID, Version, Status: Training Reference, Organisation, Purpose, Scope, Definitions, Roles and responsibilities, review/approval placeholders, references).
- **XLSX** for matrices, catalogues and registers (filtered tables, frozen header rows, data validation, implementation-status legend, separate Read Me and Reference Data sheets).
- **Markdown** for the repository findings report and this README.

Each XLSX workbook contains:
- `Read Me & Legend` — purpose, implementation-status legend, notes
- `Reference Data` — shared reference data used across all documents (departments, fictional applications, Maya Rao scenario)
- The main worksheet (RBAC Matrix / Entitlement Catalogue / Approval Matrix)

---

## Alignment with the five practical scenarios

All scenarios use the same organisation, business roles, applications, policies and reference data (including Maya Rao, EMP-1001).

| Scenario | Focus | Supporting documents |
|----------|-------|----------------------|
| 1. Joiner, Mover and Leaver | Onboarding, initial access, role change, access add/remove, termination, revocation, verification and evidence | 01 (lifecycle sections), 02 (RBAC), 03 (Entitlement Catalogue), 06 (JML procedures) |
| 2. Access Requests and Provisioning | Intake, justification, entitlement validation, approval, work item, fulfilment, verification, closure | 04 (Approval Matrix), 06 (standard procedure), 03 (Entitlement Catalogue) |
| 3. Provisioning Exceptions and SLA | Failed requests, pending approvals, incorrect access, provisioning failures, SLA tracking, escalation | 07 (Exception Management SOP), 06 |
| 4. Access Certification and SoD | Manager review, retain/revoke, excessive access, incompatible permissions, revocation, certification evidence | 01 (access review), 05 (SoD Policy & Rules Register), 03, 06 |
| 5. Reconciliation and Audit | Compare identities and entitlements, unmatched accounts, discrepancies, exceptions, corrective action, audit report | 01 (audit logging), 03, 06, 07 |

### Where activities are performed
| Activity | IdentityGuard | LDAP (OpenLDAP) | ServiceNow PDI | Excel | Word/PDF |
|----------|---------------|-----------------|----------------|-------|----------|
| Request intake & tracking | Access request API | No | Ticket / work item | Register | No |
| Approval | Single approver (access.approve) | No | Additional/manual approvals | Approval log | No |
| Provisioning (roles) | provision_access_request / UserRole | Group-mapped roles (non-privileged only) | No | Entitlement log | No |
| JML (joiner/mover/leaver) | create_user / move_user / terminate_user | Sync can create/disable local users | Ticket | JML tracker | SOP |
| Privileged access | Simulated PAM checkout (max 60 min) | No | Ticket | PAM log | No |
| Access review / certification | Review cycles, RETAIN/REVOKE | No | Ticket | Review evidence | Report |
| Audit & reconciliation | Hash-chained audit events + reports | Sync runs/changes | Ticket audit | Reconciliation register | Audit report |

---

## How to use this pack

1. Read `00-Repository-Assessment/IdentityGuard-Repository-Findings.md` first — it establishes what IdentityGuard actually implements.
2. Use `01-Access-Control-Policy.docx` as the governing policy (marks each requirement as organisational `[Policy requirement]` or IdentityGuard `[IG-implemented]`).
3. Use `02-RBAC-Matrix.xlsx`, `03-Entitlement-Catalogue.xlsx` and `04-Approval-Matrix.xlsx` as the reference data for access requests and reviews.
4. Use `05-SoD-Policy-and-Rules-Register.docx` for SoD rules (implemented IdentityGuard rules plus labelled training rules).
5. Execute `06-Provisioning-and-Deprovisioning-SOP.docx` and `07-Exception-Management-SOP.docx` as operating procedures during the practical exercises.

---

## Repository findings summary

IdentityGuard implements (verified in source and tests): RBAC with roles/permissions and a permission-checked API; access request/approval/provisioning; Joiner/Mover/Leaver lifecycle; SoD rules enforced at provisioning (Payment Initiator + Payment Approver; System Administrator + SOC Analyst; Database Administrator + Security Auditor) plus a violations report; access review cycles with RETAIN/REVOKE decisions and correction; hash-chained append-only audit logging; simulated PAM (time-limited checkout); read-only OpenLDAP synchronisation (dry-run default, controlled apply); read-only Vault integration (Vault enforces its own policy); a feature-flagged policy engine for privileged assignment.

Not implemented: Active Directory integration, SSO/OIDC, real PAM vaulting/rotation/session recording, server-side token revocation, database migrations, scheduled recurring reviews, multi-stage approval chains, ServiceNow integration, LDAP writes, LDAP authentication.

Full details: `00-Repository-Assessment/IdentityGuard-Repository-Findings.md`.

---

## Scenario 1 — Joiner, Mover, Leaver (Completed)

Scenario 1 documents the complete Joiner-Mover-Leaver lifecycle for Maya Rao (EMP-1001) at the fictional organisation Asteron Financial Services. The scenario was executed in the local IdentityGuard lab and documented end to end.

**Case ID:** JML-2026-001  
**Scenario documentation:** `01-Joiner-Mover-Leaver/`

### Lifecycle status

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

### Key limitations

- The joiner endpoint creates an account ACTIVE immediately; no future-dated activation scheduler.
- The mover could not execute because Investment Operations is not a configured IdentityGuard department.
- IdentityGuard termination does not disable OpenLDAP or revoke all sessions/tokens server-side.
- Birth-right entitlements (CRM, PMS) are proposed Asteron training data, not IdentityGuard records.

### Navigation

- Scenario overview: `01-Joiner-Mover-Leaver/README.md`
- Evidence register: `01-Joiner-Mover-Leaver/Evidence/Evidence-Register.md`
- Exceptions and limitations: `01-Joiner-Mover-Leaver/Evidence/Exceptions-and-Limitations.md`
- Closure report: `01-Joiner-Mover-Leaver/Evidence/Final-Scenario-Closure-Report.md`

All simulated stakeholder actions are explicitly labelled. The governance library remains in `00-Governance-Framework/` and is referenced, not duplicated.

---

## Scenario 2 — Access Requests and Provisioning (Completed)

Scenario 2 documents the operational handling of employee access requests for the fictional organisation Asteron Financial Services. The scenario was executed in the local IdentityGuard lab and demonstrates that access is not granted merely because someone requests it.

**Case references:** AR-2026-001, AR-2026-002, AR-2026-003, AR-2026-004  
**Scenario documentation:** `02-Access-Requests-and-Provisioning/`

### Case outcome summary

| Case | Focus | Outcome |
|---|---|---|
| AR-2026-001 | Standard non-privileged access (Rahul Mehta -> Finance Manager) | Provisioned |
| AR-2026-002 | Privileged access with four-eyes (Sneha Rao -> System Administrator, time-limited) | Provisioned (time-limited) |
| AR-2026-003 | SoD conflict (Rahul Mehta -> Payment Approver, conflicts with Payment Initiator) | Blocked (SoD-01) |
| AR-2026-004 | Exception handling (missing justification, invalid target, inactive target, duplicate) | All exceptions confirmed |

### Key limitations

- IdentityGuard supports one approver per access request; additional organisational approvals (manager endorsement) are recorded separately as simulated stakeholder records.
- Only two IAM Administrator identities exist in the lab; for privileged four-eyes, the requester and provisioner are the same identity while the approver is different.
- Privileged access to an ordinary user was made time-limited (expires_at) to avoid permanent privileged access.
- The `/users` endpoint does not expose `manager_id`; manager relationships were validated directly against the database.

### Navigation

- Scenario overview: `02-Access-Requests-and-Provisioning/README.md`
- Evidence register: `02-Access-Requests-and-Provisioning/Evidence/Evidence-Register.md`
- Exceptions and limitations: `02-Access-Requests-and-Provisioning/Evidence/Exceptions-and-Limitations.md`
- Closure report: `02-Access-Requests-and-Provisioning/Evidence/Final-Scenario-Closure-Report.md`

All simulated stakeholder actions are explicitly labelled. The governance library remains in `00-Governance-Framework/` and is referenced, not duplicated.

---

## Scenario 3 — Provisioning Exceptions and SLA Management (Completed)

Scenario 3 documents the operational handling of access provisioning exceptions for the fictional organisation Asteron Financial Services. Three real access requests left unresolved after Scenario 2 were monitored, investigated, resolved (or placed in monitoring), and closed with evidence.

**Case references:** IAM-EXC-2026-001, IAM-EXC-2026-002, IAM-EXC-2026-003  
**Scenario documentation:** `03-Provisioning-Exceptions-and-SLA/`

### Case outcome summary

| Exception ID | Focus | Priority | Outcome | Status |
|---|---|---|---|---|
| IAM-EXC-2026-001 | Approved-but-unprovisioned duplicate (Finance Manager) | P3 - Medium | Closed — entitlement already held via Request ID 1 | Closed |
| IAM-EXC-2026-002 | SoD-blocked provisioning (Payment Approver vs Payment Initiator) | P2 - High | Closed — conflict prevented, no access granted | Closed |
| IAM-EXC-2026-003 | Time-limited privileged access expiring (System Administrator) | P3 - Medium | Open — monitoring auto-expiry | Open (monitoring) |

### Key limitations

- APPROVED requests that cannot be provisioned cannot be rejected through the API (reject requires REQUESTED status); such requests remain stuck APPROVED and are resolved by documentation.
- IdentityGuard does not implement server-side SLA tracking or automatic breach escalation; SLA monitoring is manual.
- IdentityGuard has no ServiceNow integration; ticket logging is simulated/manual.
- Direct role assignment bypasses SoD and was not used.

### Navigation

- Scenario overview: `03-Provisioning-Exceptions-and-SLA/README.md`
- Evidence register: `03-Provisioning-Exceptions-and-SLA/Evidence/Evidence-Register.md`
- Exceptions and limitations: `03-Provisioning-Exceptions-and-SLA/Evidence/Exceptions-and-Limitations.md`
- Closure report: `03-Provisioning-Exceptions-and-SLA/Evidence/Final-Scenario-Closure-Report.md` (within `04-Verification-and-Closure/`)

All simulated stakeholder actions are explicitly labelled. The governance library remains in `00-Governance-Framework/` and is referenced, not duplicated.

---

## Scenario 4 — Access Reviews and User Access Certification (Completed)

Scenario 4 documents an end-to-end user access certification review for the fictional organisation Asteron Financial Services. Eighteen active role assignments across eleven active users were reviewed, with two roles revoked and sixteen retained. The review cycle was completed with full audit evidence.

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification  
**Scenario documentation:** `04-Access-Reviews-and-Certification/`

### Case outcome summary

| Metric | Value |
|:---|---:|
| Review cycle | ID 1, COMPLETED |
| Active users reviewed | 11 (1 terminated user excluded) |
| Review items | 18 |
| RETAIN decisions | 16 |
| REVOKE decisions | 2 |
| Actual revocations performed | 2 |
| Escalations | 0 |
| Active SoD violations | 0 |

### Key findings

- **meera.iyer (EMP004) — Finance Analyst revoked:** Stale cross-department access retained after a Finance→HR department move.
- **sneha.rao (EMP003) — System Administrator revoked:** Privileged emergency access concluded; no current justification for an HR user.
- **rahul.mehta — Payment Initiator retained:** Sensitive but Finance-appropriate; no active SoD conflict (no Payment Approver held). Flagged for periodic re-confirmation.
- Reviewer independence preserved: no user reviewed their own assignment.

### Key limitations

- IdentityGuard's review API supports only RETAIN and REVOKE (no MODIFY/ESCALATE).
- REVOKE decisions take effect at cycle completion, not at decision time.
- No auto-assignment of reviewers by manager; business judgments simulated per-department.

### Navigation

- Scenario overview: `04-Access-Reviews-and-Certification/README.md`
- Evidence register: `04-Access-Reviews-and-Certification/Evidence/Evidence-Register.md`
- Exceptions and limitations: `04-Access-Reviews-and-Certification/Evidence/Exceptions-and-Limitations.md`
- Certification register: `04-Access-Reviews-and-Certification/02-Access-Certification/01-Certification-Register.md`
- Final report: `04-Access-Reviews-and-Certification/04-Review-Closure/02-Final-Access-Certification-Report.md`

All simulated stakeholder actions are explicitly labelled. The governance library remains in `00-Governance-Framework/` and is referenced, not duplicated.

---

## Generated files

| # | File | Type |
|---|------|------|
| 0 | `00-Repository-Assessment/IdentityGuard-Repository-Findings.md` | Markdown findings report |
| 1 | `00-Governance-Framework/01-Access-Control-Policy.docx` | Access Control Policy |
| 2 | `00-Governance-Framework/02-RBAC-Matrix.xlsx` | RBAC Matrix |
| 3 | `00-Governance-Framework/03-Entitlement-Catalogue.xlsx` | Entitlement Catalogue |
| 4 | `00-Governance-Framework/04-Approval-Matrix.xlsx` | Approval Matrix |
| 5 | `00-Governance-Framework/05-SoD-Policy-and-Rules-Register.docx` | SoD Policy and Rules Register |
| 6 | `00-Governance-Framework/06-Provisioning-and-Deprovisioning-SOP.docx` | Provisioning & Deprovisioning SOP |
| 7 | `00-Governance-Framework/07-Exception-Management-SOP.docx` | Exception Management SOP |
| — | `README.md` | Pack overview (this file) |

---

## Unresolved assumptions / items for review

- The actual data in any running/deployed IdentityGuard database instance was not inspected (the local SQLite file was not opened or modified); seed data in code is used as the evidence base.
- Whether an OpenLDAP or Vault server is running in any target environment is not confirmed (integrations are environment-variable configured).
- Training SLA targets in `07-Exception-Management-SOP.docx` are labelled training targets, not regulatory commitments; replace with organisational SLAs for real use.
- The IdentityGuard frontend exposes several workflows as API-first (per the repository README); practical exercises may need to use the API directly.
