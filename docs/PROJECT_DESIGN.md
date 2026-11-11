# Lumen Desk — Project Design 2.1

**Status:** APPROVED  
**Approval:** DEC-003, 2026-10-30  
**Supersedes:** Project Design 1.3  
**Owner:** Product Owner

## 1. Purpose
Lumen Desk supports small community events with event creation, attendee registration, check-in, and attendee-list export.

## 2. Scope
In scope:
- Create and update an event.
- Register an attendee using an event-specific registration request.
- Prevent duplicate registration records for the same event and normalized email.
- Check in a registered attendee.
- Export an event attendee list as CSV.

Out of scope:
- Payments, ticket sales, identity verification, mass email, and multi-tenant billing.

## 3. Current architecture
- Web client communicates with a JSON HTTP API.
- API service owns validation and business rules.
- Relational storage persists events, registrations, and check-in timestamps.
- CSV export is generated from the authorized event attendee query.
- Configuration is environment-specific and is not to be edited as part of documentation or analysis tasks.

## 4. Registration and idempotency
A registration request is associated with one event and one normalized email address. The intended behavior is that retries of the same logical request do not create duplicate registrations. The exact retry-key and conflict-response behavior remains subject to the open task LUM-014 and an Owner decision on test-data strategy. Do not infer an implementation detail that has not been confirmed.

## 5. Event-list pagination
The event list is ordered by `created_at` descending, then immutable event ID ascending as a deterministic tie-breaker. The API design target is cursor-based pagination. The request accepts an opaque cursor and a page size; the service applies the configured maximum page size. The response includes `items`, `next_cursor`, and `has_more`. An absent next cursor means there is no next page. This section describes the approved API contract; implementation conformance has not yet been verified. See `docs/API_CONTRACT.md`.

## 6. Accessibility
The web client should support keyboard-only navigation and screen-reader announcements for registration and check-in workflows. Detailed acceptance scenarios are not yet approved; see LUM-016.

## 7. Change records
Project-level change records are maintained in the repository-root `CHANGELOG.md`. Each entry should identify the date, decision or change, affected area, and approving authority. Do not reconstruct historical entries from memory or commit messages alone.

## 8. Version history
- 2.1 — approved by DEC-003 on 2026-10-30.
- 1.3 — historical draft; see `docs/archive/PROJECT_DESIGN_v1.3.md`.
