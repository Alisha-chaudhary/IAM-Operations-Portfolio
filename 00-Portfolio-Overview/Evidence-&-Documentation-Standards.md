# IAM Operations Portfolio
## Evidence and Documentation Standards

**Document ID:** IAM-OPS-EVD-001  
**Status:** Training Reference  
**Applies to:** All portfolio scenarios

---

## 1. Purpose

This document establishes how operational activities, decisions, approvals and system outcomes are recorded and evidenced.

The objective is to ensure that every scenario is traceable, reproducible and suitable for technical review or interview discussion.

Evidence must demonstrate what happened, who or what performed the activity, when it happened, what was checked and what result was obtained.

## 2. Evidence classification

Every portfolio artefact must use one of the following classifications.

| Classification | Meaning | Example |
|---|---|---|
| SIMULATED | Represents activity performed by another fictional department or stakeholder | HR lifecycle notification |
| ACTUAL LAB EXECUTION | Direct output from a tool operated in the personal lab | IdentityGuard API response |
| ANALYST DOCUMENTATION | Records the analyst's checks, decisions or conclusions | Event validation record |
| REFERENCE MATERIAL | Existing policy, procedure or technical source | RBAC matrix |

A simulated approval must never be described as an actual approval in IdentityGuard or ServiceNow.

An API response must not be described as proof of end-to-end completion unless the resulting state has also been independently verified.

## 3. Evidence identification

Evidence must use a consistent identifier.

Recommended pattern:

`[SCENARIO]-[STAGE]-E[NUMBER]`

Examples:

| Evidence ID | Description |
|---|---|
| JML-J-E01 | Joiner event notification |
| JML-J-E02 | Employee reference validation |
| JML-J-E03 | IdentityGuard pre-execution state |
| JML-J-E04 | Joiner execution response |
| JML-J-E05 | Post-provisioning verification |
| JML-M-E01 | Mover event record |
| JML-L-E01 | Leaver event record |
| ARP-E01 | Access request record |
| EXC-E01 | Provisioning exception record |

Evidence IDs must be unique within the portfolio. Once assigned, they should not be reused for a different artefact.

## 4. Minimum evidence metadata

Each evidence item should record:

| Field | Description |
|---|---|
| Evidence ID | Unique reference |
| Scenario | Scenario name and number |
| Process stage | Intake, validation, approval, execution, verification or closure |
| Evidence title | Short description |
| Evidence classification | Simulated, actual lab execution, analyst documentation or reference |
| Source system | IdentityGuard, OpenLDAP, ServiceNow, Excel or other source |
| Capture date/time | When evidence was obtained |
| Related case | Operational case reference |
| Related employee/request | Employee or request reference, where applicable |
| Description | What the evidence demonstrates |
| Result | Observed outcome |
| Storage location | Repository path or evidence reference |

Use the actual timestamp available from the system. Do not manufacture a timestamp to make records appear sequential.

## 5. Evidence capture requirements

### IdentityGuard

Capture evidence of:

- Relevant pre-operation identity state.
- Employee identifier and internal user ID, where appropriate.
- Department and manager relationship.
- Current roles and assignments.
- Access request status and approval result.
- Provisioning result.
- Final account status.
- Audit events associated with the operation.
- Relevant error responses or exceptions.

Use Swagger/API evidence where the frontend does not expose the required operation.

### OpenLDAP

Where directory operations are relevant, capture:

- The directory search or lookup result.
- Relevant distinguished name and account state.
- Group membership where applicable.
- Comparison or synchronisation report.
- Separate directory-side operation evidence, if performed.

Do not claim that an IdentityGuard operation changed LDAP unless an independently verified LDAP operation proves it.

### ServiceNow

Where ITSM work is relevant, capture:

- Record number.
- Record type.
- Short description.
- Assignment group or assignee.
- Work notes and status.
- Approval or SLA information, where available.
- Closure details.

Do not claim integration with IdentityGuard.

## 6. Operational documentation standards

Each scenario must document the complete operational lifecycle:

1. Scenario background and scope.
2. Incoming event or request.
3. Event or request registration.
4. Validation and data checks.
5. Access mapping and policy checks.
6. Required approvals.
7. Execution plan.
8. IAM operation.
9. Post-operation verification.
10. Exception handling, where required.
11. Audit and evidence review.
12. Final closure.

For every material operation, record:

- What was requested.
- What was validated.
- What was authorised.
- What action was performed.
- Which system performed it.
- What result was observed.
- How the result was verified.
- What evidence supports the conclusion.

## 7. Before-and-after verification

Where a system record is changed, capture the relevant state before and after the operation.

The comparison should identify:

- The expected change.
- The actual change.
- Any unexpected difference.
- Whether the result satisfies the request.
- Whether further action is required.

Do not rely solely on a success message or HTTP status code.

## 8. Exceptions and failed operations

Failed, rejected, incomplete or delayed operations must not be hidden.

Record:

- Exception reference.
- Related case and employee/request.
- Date and time detected.
- Expected outcome.
- Actual outcome.
- Error message or failure evidence.
- Impact and risk.
- Investigation performed.
- Owner or responsible team.
- Escalation details.
- Resolution action.
- Retest or verification result.
- Closure status.

Preserve the original failure evidence. Record corrections and subsequent actions separately.

## 9. Data protection and public repository rules

Only sanitised training data may be published.

Never commit:

- Passwords or password hashes.
- API tokens, session tokens or credentials.
- LDAP bind credentials.
- Vault tokens or secret values.
- Personal data from real people.
- Private employee or customer records.
- Internal production hostnames or confidential configuration.
- Unredacted screenshots containing sensitive information.

Use the fictional Asteron scenario records for public documentation.

Screenshots must be reviewed before publication. Redact sensitive values without removing the evidence needed to understand the operation.

## 10. Source and traceability

Where a decision relies on an existing governance document, record its title and relevant section.

Where a decision relies on system behaviour, record the relevant API endpoint, application version or source file where appropriate.

Where the result comes from a simulation, state that explicitly.

Do not claim that a policy requirement is implemented by IdentityGuard merely because it appears in a governance document.

## 11. Completion criteria

A scenario may be marked complete only when:

- Required intake and validation records exist.
- Required approvals are evidenced or exceptions are documented.
- The authorised operation has been performed, if applicable.
- The resulting system state has been verified.
- Relevant audit evidence has been reviewed.
- Exceptions have been resolved or formally documented as outstanding.
- The closure report accurately reflects the outcome.
- Public artefacts have been sanitised.

---

**Evidence integrity statement:** The portfolio distinguishes simulated business events, actual lab execution, analyst-generated records and reference material. No evidence item may be altered or described in a way that misrepresents its origin or result.
