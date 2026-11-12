# Scenario 4 — Review Cycle Creation

**Cycle ID:** 1 — Asteron Q4 2026 User Access Certification
**Created at:** 12 November 2026 19:08:04 UTC
**Creator:** identityguard.admin (user 8, IAM Administrator)
**Evidence:** ACR-001-E04 (cycle creation response), ACR-001-E13 (completion)

## Purpose

Create the access review cycle using the supported IdentityGuard API and record the cycle details, population, and scope.

## API behaviour verified before creation

- Endpoint: `POST /access-reviews`
- Request schema: `{ "name": "<string 1-150 chars>" }`
- Required permission: `IdentityGuard:access_review.create`
- Behaviour: creates an OPEN cycle and snapshots ALL active (ACTIVE user, non-expired) UserRole assignments as PENDING review items
- Requirement: at least one active assignment must exist (a cycle with no assignments cannot be created)
- Audit event: `ACCESS_REVIEW_CREATED`

## Cycle creation request

| Field | Value |
|:---|:---|
| Endpoint | POST /access-reviews |
| Permission | IdentityGuard:access_review.create |
| Actor | identityguard.admin (user 8) |
| Request body | `{ "name": "Asteron Q4 2026 User Access Certification" }` |
| Response status | 201 Created |

## Cycle details

| Field | Value |
|:---|:---|
| Cycle ID | 1 |
| Name | Asteron Q4 2026 User Access Certification |
| Status | COMPLETED (was OPEN at creation) |
| Created by | identityguard.admin (user 8) |
| Created at | 2026-11-12T19:08:04.597418 UTC |
| Completed at | 2026-11-12T19:09:35.010770 UTC |
| Total items | 18 |

## Review population snapshot

The cycle snapshotted all 18 active role assignments across 11 active users as PENDING items (items 1–18). Terminated user Maya Rao (zero assignments) was not included. See `00-Review-Background/03-Review-Population.md` for the full categorisation and `02-Access-Certification/01-Certification-Register.md` for the item-level decisions.

## Review period and dates (fictional training dates)

| Field | Value |
|:---|:---|
| Review period | Q4 2026 (October–December 2026) |
| Review date | 12 November 2026 |
| Cycle created | 12 November 2026 19:08:04 UTC |
| Cycle completed | 12 November 2026 19:09:35 UTC |

These dates are fictional training dates used for the scenario.

## Scope and exclusions

- **In scope:** all active users with active (non-expired) role assignments (11 users, 18 items)
- **Excluded:** terminated users (Maya Rao — terminated, zero assignments)
- **Not review items:** pending access requests (Scenario 3 Request IDs 3 and 4, APPROVED but unprovisioned) — not role assignments, tracked separately

## Application limitation documented

IdentityGuard creates review items automatically by snapshotting all active assignments; the analyst cannot selectively include or exclude items at cycle creation. Exclusions (terminated users) are handled by the snapshot logic (terminated users have no active assignments, so none are included). The cycle name and creator are the only configurable inputs.
