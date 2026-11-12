# IAM Operations Portfolio
## Portfolio Scope

**Portfolio Owner:** Alisha Chaudhary  
**Portfolio Type:** Practical IAM Operations Lab  
**Primary IAM Platform:** IdentityGuard  
**Organisation:** Asteron Financial Services (Fictional)  
**Status:** In Progress  
**Classification:** Public portfolio documentation containing sanitised training data only

---

## 1. Purpose

This portfolio demonstrates practical Identity and Access Management (IAM) operations through structured, end-to-end case studies.

The exercises are designed around the responsibilities commonly performed by an entry-level IAM Operations Analyst, Access Management Analyst or SailPoint Provisioning Operations Analyst.

The portfolio focuses on operational accuracy, access governance, controlled provisioning, exception handling, evidence collection and audit readiness.

It uses the existing IdentityGuard IAM governance lab and its established governance documentation as the primary reference environment.

## 2. Scope of work

The initial portfolio submission covers three operational scenarios.

| Scenario | Operational scope |
|---|---|
| 01. Joiner, Mover and Leaver | Employee lifecycle event intake, identity validation, access mapping, provisioning, access modification, termination and verification |
| 02. Access Requests and Provisioning | Request validation, business justification, entitlement checks, approval, provisioning, verification and closure |
| 03. Provisioning Exceptions and SLA | Exception identification, investigation, failed or delayed provisioning, resolution, escalation, SLA tracking and closure |

Additional scenarios may be developed later, including access certification, SoD review, identity reconciliation and audit reporting.

## 3. Operational responsibilities demonstrated

The portfolio will demonstrate the following analyst activities:

- Receiving and registering identity lifecycle events and access requests.
- Checking employee and requester information against authorised reference records.
- Identifying missing, inconsistent, duplicate or unauthorised requests.
- Reviewing role and entitlement requirements.
- Applying least-privilege and access governance principles.
- Checking approval requirements and separation-of-duties conflicts.
- Executing authorised IAM operations in IdentityGuard.
- Verifying identity attributes, role assignments and account status.
- Investigating provisioning failures and access discrepancies.
- Maintaining operational records and evidence.
- Documenting exceptions, escalations and resolution outcomes.
- Completing case closure and maintaining an auditable trail.

Activities normally performed by HR, managers, application owners and other departments will be represented through simulated upstream records and responses. The portfolio owner will perform the IAM Operations activities relevant to the target role.

## 4. Reference and data governance

The existing IdentityGuard repository is the primary technical and governance reference.

The existing IAM Governance and Operations documentation pack provides the fictional Asteron business context and supporting governance material, including:

- Access control policy.
- RBAC matrix.
- Entitlement catalogue.
- Approval matrix.
- SoD policy and rules register.
- Provisioning and deprovisioning SOP.
- Exception management SOP.
- Existing scenario and employee reference information.

The live IdentityGuard database will be inspected before operational execution. Existing users, departments, roles, permissions and assignments must not be assumed from documentation alone.

**Data-use rules:**

1. Existing reference data must be reused wherever applicable.
2. Existing database records must not be reset, deleted or overwritten for convenience.
3. Any mismatch between the governance reference library and the live database must be documented and investigated.
4. New training records may only be created when required by the scenario and after validation.
5. Fictional Asteron records must never be represented as real corporate records.

## 5. Execution and simulation model

The portfolio uses a hybrid practical simulation.

| Activity | Execution approach |
|---|---|
| HR event generation | Simulated upstream HR event |
| HR authorisation | Simulated approval evidence |
| Employee master information | Existing Asteron scenario reference data |
| IAM identity operations | Actual execution in the local IdentityGuard lab |
| Access request and role provisioning | Actual execution in IdentityGuard, subject to implemented functionality |
| Directory verification | OpenLDAP lab, where applicable |
| ITSM records | ServiceNow Personal Developer Instance |
| Operational registers | Excel and Markdown |
| Final case documentation | Markdown, Word or PDF |
| Portfolio publication | GitHub |

Simulated upstream activity and actual technical execution will be clearly distinguished.

No production HRIS, ServiceNow or directory integration is claimed.

## 6. Out of scope

The portfolio does not claim:

- Production enterprise IAM administration.
- Production SailPoint IdentityIQ or Identity Security Cloud provisioning.
- Real HRIS integration or automated HR event ingestion.
- Active Directory or Microsoft Entra ID administration.
- Production application integrations.
- Production PAM credential vaulting, rotation or session recording.
- Automated multi-stage approval orchestration within IdentityGuard.
- Enterprise SLA automation where the tool does not implement it.

SailPoint training and certifications demonstrate product knowledge, but do not establish hands-on production SailPoint administration.

## 7. Expected outcomes

Each completed scenario should contain:

1. Scenario background and scope.
2. Incoming event or request record.
3. Relevant validation and approval evidence.
4. Analyst execution records.
5. Actual system evidence.
6. Verification results.
7. Exception records, if applicable.
8. Final operational closure report.
9. Sanitised portfolio documentation.

The objective is to demonstrate a repeatable, controlled and evidence-based IAM operations workflow.

---

**Portfolio integrity statement:** All Asteron Financial Services business records are fictional training data. System operations are performed only in the designated personal lab environment. Actual execution evidence is distinguished from simulated departmental records.
