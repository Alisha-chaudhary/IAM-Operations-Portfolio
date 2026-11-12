# HRIS Joiner Event Notification

**Classification:** SIMULATED UPSTREAM EVENT  
**Organisation:** Asteron Financial Services (fictional)

| Field | Value |
|---|---|
| HR event ID | HR-JNR-2026-001 |
| IAM case reference | JML-2026-001 |
| Event type | Joiner |
| Event source | Asteron HR Information System (HRIS), simulated |
| Event status | Approved by HR; received by IAM |
| Event issued date | 12 November 2026 |
| Employee ID | EMP-1001 |
| Employee name | Maya Rao |
| Employment type | Full-time |
| Job title | Relationship Manager |
| Department / business unit | Wealth Management |
| Work location | Hyderabad |
| Reporting manager | Neha Kapoor |
| Employment start date | 17 November 2026 |
| Requested account availability | On or after 17 November 2026 |
| HR approval reference | HR-APP-2026-441 (simulated) |
| Event owner | HR Operations (simulated role) |

## Event summary

Asteron HR Operations has recorded an approved new-hire event for Maya Rao, employee ID EMP-1001. The employment start date is 17 November 2026. HR requests that IAM prepare the identity lifecycle work so that required access can be made available on or after the employee's start date, subject to IAM validation and the organisation's access governance requirements.

## HR-originated instructions

1. Treat this notification as the authoritative simulated HR event for this case exercise.
2. Do not create or activate the IdentityGuard account before the stated start date unless an approved exception explicitly authorises pre-provisioning.
3. Validate employee and organisational attributes against approved reference data.
4. Verify manager and application-owner approvals where required by the access governance process.
5. Return missing, inconsistent, or unsupported data to the appropriate upstream owner. IAM must not invent or silently amend HR master data.

## IAM hand-off

The HR activity ends at the authorised event hand-off. IAM owns case intake, validation, identity correlation, access determination, provisioning controls, verification, audit evidence, and closure.

This event is a simulated training artifact. It is not a real HRIS message, production notification, or evidence of an actual employee record.

## Validation items for IAM

- Confirm whether EMP-1001 already exists in the live IdentityGuard database.
- Confirm whether Wealth Management exists as a configured department in the live database.
- Confirm whether Neha Kapoor is present as an eligible manager identity and whether the manager relationship is supported.
- Confirm the relevant access profile and entitlements from the existing governance library.
- Confirm required approvals and applicable segregation-of-duties constraints.

## Evidence metadata

| Attribute | Value |
|---|---|
| Evidence ID | JML-001-E01 |
| Classification | SIMULATED |
| Prepared by | Scenario facilitator |
| Received by | IAM Operations queue (simulated) |
| Case status | Awaiting IAM intake and validation |
| Date created | 12 November 2026 |
