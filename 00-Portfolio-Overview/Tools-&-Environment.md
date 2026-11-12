# IAM Operations Portfolio
## Tools and Environment

**Document ID:** IAM-OPS-ENV-001  
**Status:** Training Reference  
**Primary IAM Platform:** IdentityGuard  
**Organisation:** Asteron Financial Services (Fictional)

---

## 1. Environment overview

The portfolio uses a combination of an existing IAM governance application, a local directory lab, an ITSM development instance and documentation tools.

IdentityGuard is the primary platform for IAM identity lifecycle and access governance operations.

The environment is intentionally divided into separate systems. No integration is assumed unless it has been implemented and verified.

## 2. Primary IAM platform

### IdentityGuard

**Repository:** https://github.com/Alisha-chaudhary/IdentityGuard

IdentityGuard is a custom IAM governance and access-management lab developed using:

- Python
- FastAPI
- SQLAlchemy
- SQLite
- Pytest
- React

It provides the main environment for practical IAM operations.

Relevant implemented capabilities include:

- User identity lifecycle operations.
- Joiner, mover and leaver processing.
- Role-based access control.
- Access request and approval workflow.
- Access provisioning.
- Separation-of-duties checks.
- Access review workflows.
- Audit events and governance reporting.
- Simulated privileged access lifecycle.

### Existing database and reference records

The existing database must be treated as persistent operational data.

Before performing any scenario:

- Inspect existing users and employee identifiers.
- Inspect departments and manager relationships.
- Inspect existing roles and role assignments.
- Inspect permissions and access request records.
- Check for duplicate identities and conflicting records.
- Record the initial state before making changes.

The checked-in seed configuration is not automatically proof of the current local database state.

The existing Asteron governance reference library and the live IdentityGuard database are separate sources that must be reconciled where necessary.

**Database safety requirements:**

- Do not reset or reseed the existing database.
- Do not delete existing records to make a scenario easier.
- Do not change existing assignments without an authorised scenario requirement.
- Do not expose passwords, tokens, secrets or sensitive configuration in screenshots or GitHub.

### Important implementation limitations

The current JML implementation has the following constraints:

| Functionality | Verified behaviour |
|---|---|
| Joiner | Creates an active IdentityGuard user |
| Mover | Updates department and/or manager |
| Role changes on mover | Existing roles are not automatically replaced |
| Leaver | Terminates the user and expires active role assignments |
| Access request | Request, approval and provisioning workflow |
| Approval | One approver per IdentityGuard access request |
| PAM | Simulated privileged access lifecycle |
| Audit | Hash-chained, tamper-evident audit events |
| Database schema changes | No Alembic migration framework; `create_all()` is used |
| Session revocation | No server-side JWT revocation mechanism identified |

The Joiner endpoint does not schedule future account activation. The operator must therefore respect the effective start date and avoid premature account creation.

**Implementation references:**

- `app/db/seed.py`
- `app/db/models.py`
- `app/iam/jml.py`
- `app/api/jml.py`

## 3. Directory environment

### OpenLDAP

OpenLDAP is used as a separate directory lab for identity discovery and verification where applicable.

IdentityGuard's LDAP integration supports:

- Read-only directory discovery.
- Dry-run comparison.
- Controlled application of approved changes to local IdentityGuard records.

IdentityGuard does not write changes back to LDAP.

Any separate LDAP account operation must be performed independently, only when required, and after inspecting the existing directory structure and permissions.

Active Directory and Microsoft Entra ID are not part of the established lab.

## 4. IT Service Management

### ServiceNow Personal Developer Instance

ServiceNow PDI is used for supporting operational records such as:

- Incidents or service requests, depending on available modules.
- Assignment and work tracking.
- Approval records where supported.
- SLA and escalation tracking.
- Operational closure and work notes.

The PDI is not integrated with IdentityGuard.

The two systems will be correlated manually using the relevant employee and case references.

For this portfolio, IAM execution will be completed first and supporting ITSM documentation added afterwards. This is a training sequence, not a claim that every production organisation permits fulfilment before ticket registration. Actual execution order must follow the applicable organisational SOP.

## 5. Documentation and evidence tools

| Tool | Purpose |
|---|---|
| Microsoft Excel | Operational registers, access matrices, validation records and reconciliation |
| Microsoft Word | Formal reports, procedures and case documentation |
| PDF | Preserved evidence and final reports |
| Markdown | Scenario documentation and GitHub records |
| Notion | Portfolio progress tracking and work organisation |
| GitHub | Version-controlled public portfolio and sanitised deliverables |

## 6. Learning and reference platform

### SailPoint

SailPoint training material and certifications are used as a learning reference for IAM concepts and provisioning operations.

IdentityGuard is the practical execution platform for this portfolio.

No SailPoint tenant execution or production SailPoint administration is claimed.

## 7. Environment boundaries

| System | Role in the portfolio | Integration status |
|---|---|---|
| IdentityGuard | Primary IAM execution | Standalone |
| SQLite | IdentityGuard persistence | Native application database |
| OpenLDAP | Directory lab | IdentityGuard read-only discovery and controlled local apply |
| ServiceNow PDI | ITSM work tracking | No IdentityGuard integration |
| Excel / Word / PDF | Operational documentation | Manual |
| Notion | Progress tracking | Manual |
| GitHub | Portfolio publication | Repository hosting |

## 8. Evidence integrity

Every artefact must be identified as one of the following:

- **SIMULATED:** Generated to represent activity from another department.
- **ACTUAL LAB EXECUTION:** Produced by a real operation in the local lab.
- **ANALYST DOCUMENTATION:** Created by the portfolio owner to record validation, decisions or results.
- **REFERENCE MATERIAL:** Existing governance or technical documentation.

This classification prevents simulated activity from being mistaken for real system integration or production work.

---

**Environment integrity statement:** This portfolio uses a personal IAM lab and fictional organisational records. Tool capabilities are described according to verified implementation, not assumed enterprise functionality.
