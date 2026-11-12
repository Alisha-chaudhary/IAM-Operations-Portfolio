# IAM Validation Verdict: Joiner Case 01

> **Validation outcome: NOT APPROVED**
>
> **Case status: ON HOLD**

## Case Information

| Attribute | Details |
|---|---|
| Case Reference | `JML-2026-001` |
| HR Event Reference | `HR-JNR-2026-001` |
| Employee Name | Maya Rao |
| Employee ID | `EMP-1001` |
| Lifecycle Event | Joiner |
| Employment Start Date | 17 November 2026 |
| Validation Date | 12 November 2026 |
| Validation Stage | Initial identity and organisational data validation |

## 1. Validation Findings

| Control / Validation | Finding | Verdict |
|---|---|---|
| Employee ID uniqueness | `EMP-1001` was not found among the 12 existing identities. | PASS |
| Existing identity check | No existing account matching Maya Rao was found. | PASS |
| Department validation | Wealth Management is not configured in the current IdentityGuard environment. | FAIL |
| Manager validation | Neha Kapoor is not present in the current identity inventory. | FAIL |
| Manager relationship support | The identity inventory exposes a `manager_id` attribute, confirming that manager relationships are supported. | PASS |
| Role mapping | Not yet assessed against the approved governance documentation. | PENDING |
| Approval validation | An HR approval reference was supplied, but application and access-specific approvals have not yet been assessed. | PENDING |
| Provisioning readiness | Required organisational attributes remain unresolved. | FAIL |

## 2. Risk and Control Assessment

The initial validation identified the following control issues:

1. **Organisational reference-data mismatch:** The requested department, Wealth Management, does not exist in the configured IAM environment. The department must not be silently mapped to another department.

2. **Unverified reporting relationship:** The nominated manager, Neha Kapoor, could not be correlated with an existing identity in the inventory. The reporting relationship therefore remains unverified.

3. **Identity and access integrity risk:** Provisioning with substituted or unverified organisational attributes could result in incorrect identity ownership, approval routing, and access assignments.

4. **Premature provisioning risk:** The current IdentityGuard implementation creates accounts with an `ACTIVE` status immediately. Creating the account before the approved employment start date could result in premature account availability. Provisioning must therefore be aligned with the effective date unless an authorised exception permits earlier creation.

## 3. Final Validation Decision

**IAM Disposition: HOLD / RETURN FOR HR CLARIFICATION**

The joiner request is not approved for provisioning at this stage.

The employee ID uniqueness and existing-identity checks passed. However, department and manager validation failed because the requested organisational attributes could not be verified against the current IAM reference data.

The case must remain on hold until HR Operations provides an authorised correction or confirms that the required organisational reference data must be onboarded.

Following clarification, IAM must revalidate the corrected attributes and complete access mapping, approval verification, and segregation-of-duties (SoD) checks before proceeding with provisioning.

No account creation or access assignment is authorised by this validation outcome.

## 4. Required Next Actions

| Responsible Team | Required Action |
|---|---|
| IAM Operations | Record the validation findings and maintain the provisioning hold. |
| HR Operations | Clarify the employee's department and reporting manager. |
| IAM Operations | Revalidate the corrected HR attributes against the IAM environment. |
| IAM Governance | Complete role mapping, approval requirements, and SoD assessment. |
| IAM Operations | Proceed with provisioning only after all required controls have passed. |

## 5. Evidence Register

| Evidence ID | Evidence Description | Classification |
|---|---|---|
| `JML-001-E01` | Simulated HRIS joiner event notification | Simulated |
| `JML-001-E02` | `GET /users` API response | Actual lab execution |
| `JML-001-E03` | `GET /reports/identity-inventory` API response | Actual lab execution |
| `JML-001-E04` | Initial IAM validation verdict | Portfolio assessment record |

## 6. Case Progress and Closure Checklist

### Completed

- [x] HR joiner event received.
- [x] Employee ID uniqueness checked.
- [x] Existing identity checked.
- [x] Department reference data checked.
- [x] Manager identity checked.
- [x] Initial validation findings documented.
- [x] Provisioning hold established.

### Pending

- [ ] HR clarification received.
- [ ] Corrected organisational attributes validated.
- [ ] Access mapping completed.
- [ ] Approval requirements verified.
- [ ] SoD assessment completed.
- [ ] Provisioning executed.
- [ ] Provisioned identity and access verified.
- [ ] Audit evidence reviewed.
- [ ] Case closure approved and documented.

## 7. Final Case Status

**OPEN - ON HOLD - AWAITING HR CLARIFICATION**

This document records the initial IAM validation outcome. It does not represent a completed joiner lifecycle process or successful provisioning.

No account or access changes have been performed in IdentityGuard as part of this validation stage.

---

## Evidence and Execution Notes

- The HRIS event is a simulated upstream notification prepared for this portfolio exercise.
- The user inventory and identity inventory report were retrieved from the local IdentityGuard API using read-only GET operations.
- The validation findings reflect the returned lab data at the time of assessment.
- IdentityGuard is a local IAM governance and operations lab, not a production SailPoint deployment.
