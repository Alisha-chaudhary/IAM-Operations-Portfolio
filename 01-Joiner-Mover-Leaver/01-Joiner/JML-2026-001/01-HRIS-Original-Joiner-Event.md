# HRIS Joiner Attribute Amendment

**Classification:** SIMULATED UPSTREAM EVENT  
**Organisation:** Asteron Financial Services (fictional)

## 1. Amendment Information

| Attribute | Value |
|---|---|
| Original HR Event ID | `HR-JNR-2026-001` |
| IAM Case Reference | `JML-2026-001` |
| Amendment Reference | `HR-AMD-2026-001` |
| Amendment Date | 12 November 2026 |
| Event Type | Joiner attribute correction |
| Amendment Status | Approved by HR (simulated) |
| Source Owner | HR Operations (simulated) |

## 2. Employee Details

| Attribute | Original Event | Amended Value |
|---|---|---|
| Employee ID | `EMP-1001` | `EMP-1001` |
| Employee Name | Maya Rao | Maya Rao |
| Employment Type | Full-time | Full-time |
| Job Title | Relationship Manager | Relationship Manager |
| Department | Wealth Management | Finance |
| Location | Hyderabad | Hyderabad |
| Reporting Manager | Neha Kapoor | Priya Nair |
| Employment Start Date | 17 November 2026 | 17 November 2026 |

## 3. Manager Reference

The amended reporting manager is correlated with the existing IdentityGuard identity:

| Attribute | Value |
|---|---|
| Manager Name | Priya Nair |
| Employee ID | `EMP001` |
| IdentityGuard User ID | `1` |
| Username | `priya.nair` |
| Department | Finance |
| Email | `priya.nair@example.test` |

The manager reference is based on the current IdentityGuard identity inventory. The inventory also shows an existing Finance employee, Rahul Mehta (`EMP002`), with `manager_id: 1`.

## 4. Amendment Instructions to IAM

1. Retain the original HRIS joiner event as historical evidence.
2. Use this approved amendment as the corrected source for department and reporting-manager attributes.
3. Validate the amended attributes against the current IdentityGuard reference data.
4. Complete access mapping using the approved RBAC matrix and entitlement catalogue.
5. Verify required approvals and applicable SoD controls before provisioning.
6. Do not create the employee account before the approved employment start date unless a separate pre-provisioning exception is authorised.

## 5. IAM Hand-off

HR Operations has completed the simulated source-data correction and returned the amended event to IAM Operations.

IAM is responsible for post-amendment validation, access determination, approval verification, provisioning, verification, audit evidence, and case closure.

**This amendment is a simulated portfolio artifact. It is not an actual HRIS transaction or production approval.**
