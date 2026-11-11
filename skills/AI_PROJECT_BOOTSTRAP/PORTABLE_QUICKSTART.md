# Software Project Governance — Portable Quick Start

This file is a self-contained operating guide for AI environments that do not support automatic Skill discovery, frontmatter, or a skills directory. Read and follow this file as project instructions.

## 1. Establish the source of truth

- Use the canonical project repository and durable issue tracker as the system of record; chat history is not authoritative.
- Record repository URL, visibility, default branch, current full HEAD SHA, owner and permissions.
- Inspect branches, tags, commits, Issues, PRs, requirements, designs, CI, tests and handoffs before changing anything.
- Preserve originals and conflicting evidence. Mark unknowns; never guess.

## 2. Establish authority and boundaries

Before acting, identify the project owner, explicit task authorization, allowed/prohibited changes, base SHA, acceptance criteria and rollback plan.
No blanket authority is implied. Do not access secrets, production/customer data, external drives/storage, change protections, deploy, merge the default branch, or upload assets without specific authorization.

## 3. Establish minimum management records

Ensure the project has equivalent records for:
- canonical management entry point and project purpose/owner/authority;
- timestamped state snapshot with branch and full SHA;
- work register linked to Issues or equivalent tracker;
- operating rules for authorization, changes, evidence and review;
- design-baseline index with source/version/hash/approval;
- decision record mechanism;
- disaster-recovery plan and verification state;
- security/data boundaries;
- task, handoff, execution and acceptance templates.

Reuse existing records; filenames and folder layout may vary. Do not create duplicate sources of truth.

## 4. Bootstrap an inherited project

1. Read-only inventory first; protect active branches and PRs.
2. Record what exists, what is missing, where it was searched, and confidence.
3. Recover design provenance and establish requirement → design → code → test → acceptance traceability.
4. Create scoped Issues and isolated branches only when authorized.
5. Record all operations, tool versions, exact commands/API calls, exit codes, outputs and hashes.
6. Read back each delivered file and verify the exact commit SHA.

## 5. Coordinate contributors

Every task has an ID, owner, authorization, fixed base SHA, scope, dependencies, acceptance criteria, test environment and next action. Handoffs include exact branch/SHA, files read, work performed, tests run/not run, logs, hashes and known risks.

An independent reviewer must not have produced the work or participated in its implementation/approval. The reviewer fetches the fixed SHA, records files/criteria reviewed and discloses prior involvement. Self-review is not independent review.

## 6. Separate task state from evidence state

Task lifecycle: PROPOSED, HOLD_FOR_APPROVAL, READY, RUNNING, SUBMITTED, REVIEWING, ACCEPTED, BLOCKED, CHANGES_REQUESTED, CANCELLED.

Test evidence: PASS, FAIL, NOT RUN, NOT VERIFIED, INCONCLUSIVE, BLOCKED.

Never convert missing or inconclusive evidence into PASS. A submitted task may still have tests NOT RUN.

## 7. Reproducible execution

For each operation record OS/tool versions, exact command/API request, repository/branch/SHA, expected and actual exit code/status, raw log path and fallback. Prefer Git CLI, then authorized GitHub REST/API, then authorized UI. If all paths fail, mark BLOCKED/NOT VERIFIED; do not claim completion.

## 8. Backup and recovery

Define scope, destination, exclusions, encryption, key custody, access, retention, RPO/RTO and cost. Request explicit owner authorization before creating accounts or uploading/accessing external assets. Record approval/denial and conditions. Read back the backup, verify hashes, restore to an isolated destination and obtain independent verification. If not authorized, mark BLOCKED/NOT VERIFIED and retain the risk.

## 9. Cold-start acceptance

Give a fresh agent only repository URL, management entry path and one active task ID. Score seven checks (0/1 each): locate entry/version; identify current branch/full SHA; separate verified facts from unknowns; locate active task/decision; identify permissions; produce evidence-backed handoff; identify next authorized action. Require 7/7. Any fabricated authorization, test result, approval or project status is an automatic FAIL. Missing information scores zero but is not automatically fabrication.

## 10. Stop conditions

Stop before unapproved merge, deployment, production operation, external upload, destructive change, permission change or release. Report blockers and ask the authorized owner. Never claim an operation, test, backup, restore, review or approval that did not occur.
