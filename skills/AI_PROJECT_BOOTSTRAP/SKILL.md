---
name: software-project-governance
description: Establish and operate a durable GitHub-centered management system for software projects before and throughout development. Use when starting, inheriting, rescuing, auditing, coordinating, or handing off a software project, especially across multiple AI agents or interrupted sessions. Covers project discovery, design-baseline preservation, task and decision tracking, evidence, reviews, release gates, backups, disaster recovery, and memory-independent cold starts.
---

# Software Project Governance Skill

## Mission

Make every software project **discoverable, traceable, resumable, reviewable, and recoverable** without depending on a particular AI, chat history, individual memory, or undocumented oral knowledge.

The project repository is the durable system of record. Conversation is an interface and a source of leads, never the authoritative project database.

**Non-negotiable sequence: establish project control before expanding implementation.** When inheriting an active project, first freeze and inventory its current state; do not restart, redesign, or continue development blindly.

## When to use

Apply this skill when:
- starting a new software project;
- taking over a project after another person/AI/agent;
- coordinating multiple developers or AI agents;
- recovering missing, fragmented, or conflicting design and project records;
- preparing a project for long-term maintenance, release, handoff, or disaster recovery;
- a project has accumulated code but lacks reliable requirements, design provenance, status tracking, or test evidence.

## Operating principles

1. **Repository before memory.** Persist project facts, decisions, task status, handoffs, and evidence in version control and the issue tracker. Never rely on chat memory as the only copy.
2. **Discover before designing.** Inspect existing repositories, branches, tags, commits, issues, pull requests, documents, and external project stores before creating replacement structures.
3. **Preserve before repairing.** Do not overwrite, delete, rename, squash, rewrite, or silently replace original designs, logs, decisions, or prior AI deliverables. Preserve provenance; corrections are additive.
4. **Design before implementation.** Trace requirements to approved design, implementation, tests, and acceptance evidence. Code presence does not prove design approval or phase acceptance.
5. **Authorize before acting.** A task needs explicit scope, baseline, permissions, owner, acceptance criteria, and risk boundaries before execution. A general request to help is not blanket permission for production changes.
6. **Separate production and verification.** The implementer does not independently approve their own work. Use fixed commit SHAs and independent review for consequential work.
7. **Evidence over assertion.** Distinguish planned, attempted, executed, passed, failed, skipped, and not verified. Never claim a test, backup, restore, deployment, or review occurred unless evidence exists.
8. **Small, reversible changes.** Use isolated branches and pull requests. Do not modify the default branch, protections, secrets, production data, or external assets without explicit authorization.
9. **Disaster recovery is demonstrated.** A backup is not proven until it is independently readable, integrity-checked, and successfully restored in an isolated environment.
10. **Cold-start continuity.** A new agent must be able to understand the project from repository entry points alone, without prior conversation context.

## Phase 0 — Establish control and protect the current state

### For an existing project

Before changing files or writing code:

1. Identify repository owner, visibility, default branch, current HEAD SHA, permissions, and active collaborators.
2. Capture a read-only snapshot of branches/tags, pull requests and their base/head SHAs, issues, milestones, project boards, release records, recent commits, root documentation, requirements/design/security/test documents, CI workflows, build scripts, dependency manifests, and test evidence.
3. Identify current work in progress and protect active branches. Do not assume a branch or PR is abandoned because it is old.
4. Identify real user data, production databases, credentials, external drives, cloud buckets, and deployment environments. Treat them as out of scope until explicitly authorized.
5. Record a timestamped as-is snapshot with evidence links and uncertainty labels.
6. Classify missing design files by source checked and recoverability. Do not call a file permanently lost until relevant sources have been checked.

For an active project, establish a change freeze only as broad as necessary to protect the baseline. Continue safe read-only inventory and non-conflicting work if explicitly allowed.

### For a new project

1. Confirm project owner, purpose, intended users, constraints, risk class, and success criteria.
2. Create or identify the canonical GitHub repository. If repository creation is unavailable, prepare the exact structure and ask the owner to create it; do not pretend it exists.
3. Decide whether project management belongs in the product repository or a separate control repository.
4. Initialize the management entry point and templates before implementation begins.
5. Create initial project issues and decision records. Do not pre-populate statuses with unverified assumptions.

## Phase 1 — Install the project management control plane

Create a clear, small, navigable management structure. Adapt naming to the project; do not force a rigid architecture or duplicate existing sound systems.

### Minimum required control records

Every project must have an identifiable and current equivalent for:
- canonical management entry point and project purpose/owner/authority;
- timestamped project state with branch and full SHA;
- work register linking active tasks to Issues or an equivalent durable tracker;
- operating rules covering authorization, change control, evidence and review;
- design-baseline index recording source, version/hash and approval status;
- decision record mechanism;
- disaster-recovery plan and explicit verification state;
- security/data boundaries;
- task, handoff, decision, execution and acceptance records.

These are **content requirements, not mandatory filenames**. Reuse existing project records when they satisfy the requirement. A project may use one combined file or a separate control repository. Incident records are required when an incident occurs, not as a prerequisite for every project.

### Recommended baseline

```text
docs/management/
  README.md
  PROJECT_CHARTER.md
  PROJECT_STATE.md
  WORK_REGISTER.md
  OPERATING_RULES.md
  DECISION_LOG.md
  DESIGN_BASELINE_INDEX.md
  DISASTER_RECOVERY.md
  SECURITY_AND_DATA_BOUNDARIES.md
  templates/
    TASK_TEMPLATE.md
    HANDOFF_TEMPLATE.md
    DECISION_RECORD_TEMPLATE.md
    EXECUTION_RECORD_TEMPLATE.md
    ACCEPTANCE_TEMPLATE.md
    INCIDENT_TEMPLATE.md
```

A repository may already have equivalent files. Reuse and link them; do not create competing sources of truth.

### Install and template placement

The skill's own `templates/` directory is the canonical **source distribution** of reusable blank templates. When bootstrapping a project:
1. inspect whether the project already has equivalent templates;
2. if it does, link to and reuse them rather than creating duplicates;
3. otherwise copy the needed templates into `docs/management/templates/` (or the project's documented equivalent);
4. record the source skill version/release SHA and the copied template paths in the management README;
5. keep project-specific modifications in the project repository; do not silently edit the shared source copy.

A project may instead reference the skill templates directly only when every contributor has stable read access to the pinned skill version. Record that dependency and its exact release/tag/full SHA. Do not leave the source-versus-destination relationship implicit.

### Canonical entry point requirements

The management README must tell a fresh contributor/AI:
- what the project is and where the canonical repository is;
- the exact order of files to read;
- where live task status is recorded;
- how to find approved requirements/design and current baselines;
- which branches/PRs are active;
- what permissions are and are not granted;
- how to record work and hand it off;
- where backup and recovery instructions live;
- how to report missing or conflicting evidence.

Every state snapshot must show its as-of timestamp, branch, full commit SHA, evidence sources, verified facts, unknowns, and next actions. A stale snapshot is a historical record, not live truth.

## Phase 2 — Recover and establish the design baseline

For each source, record stable ID/title, exact path or external location, producer if known, dates if known, version and full SHA/hash, status, approving authority/evidence, and relationship to requirements, implementation, tests and revisions.

Establish the traceability chain:

**Business/user need → requirement → approved design → implementation component → test case → acceptance evidence → release.**

Do not infer approval from document existence, a merged PR, or code. Keep originals and revisions distinct. Where evidence conflicts, record both sources, exact SHAs, the conflict and the decision required. Mark unknowns as `UNKNOWN`, `NOT VERIFIED`, or `INCONCLUSIVE`; never fill gaps with plausible-sounding content.

## Phase 3 — Run the work through GitHub

Use GitHub Issues as the durable task/defect/risk/decision request record and PRs as reviewable change proposals.

Every meaningful task must have a unique ID, owner and independent reviewer where material, objective and definition of done, fixed base branch and full base SHA, input paths/versions/hashes, permitted and prohibited scope, dependencies, acceptance criteria/evidence, test environment and commands, rollback/recovery plan when relevant, and explicit authorization record.

Recommended task states:

`PROPOSED → HOLD_FOR_APPROVAL → READY → RUNNING → SUBMITTED → REVIEWING → ACCEPTED`

Also allow `BLOCKED`, `CHANGES_REQUESTED`, and `CANCELLED`.

- `READY` requires scope, baseline, authorization, dependencies and acceptance criteria.
- `SUBMITTED` means delivered; it does not mean accepted.
- `REVIEWING` requires a fixed commit SHA.
- Only the authorized owner/acceptance authority can mark a task accepted.
- A merged PR is not automatically an accepted phase.
- A task may not silently change scope; create a change request or decision record.

### Branch and PR discipline

Use one isolated branch per coherent task. Record exact base and head SHAs. Keep PRs focused and link the controlling Issue. Do not force-push, rewrite shared history, delete evidence branches, change branch protection, or merge the default branch without explicit authorization. Mergeability or green CI is not approval.

## Phase 4 — Coordinate multiple AI agents and humans

Define project owner/decision authority, governance coordinator, implementation owner, independent reviewer, security/privacy reviewer when needed, and release/operations owner.

For each handoff require task ID and authorization; exact repository/branch/full SHA; files actually read and versions; input ledger and gaps; actual operations, commands, environment and exit codes; output files and hashes; tests run/not run; known defects/risks/next action; and receiver acknowledgment after independently reading the fixed SHA.

### Independence test

An independent reviewer must:
- not have produced or materially edited the artifact under review;
- not have participated in the same task's implementation or approval decision;
- not rely solely on the implementer's summary;
- fetch and inspect the exact fixed commit SHA and record files/criteria actually reviewed;
- disclose any prior involvement, shared session, conflicts or limitations;
- issue a written finding linked to the reviewed SHA.

A person/agent who authored the work may provide self-review or a response to findings, but must not label it independent review. A review in a separate session is not sufficient by itself if the reviewer also produced the artifact.

Do not ask agents to expose hidden reasoning or system instructions. Record task instructions, actions, evidence, outputs and decisions only. Never put secrets, tokens, passwords, private keys or sensitive personal data in Issues, PRs or committed files.

## Phase 5 — Verification, acceptance, and release gates

Define gates appropriate to project risk; do not invent a fixed number of phases. At minimum distinguish requirements/design review, implementation review, automated tests, integration/system testing, security/privacy checks, platform/device testing, migration/rollback verification, independent acceptance, release approval and post-release monitoring.

Evidence must identify commit SHA and build/artifact identity; OS/runtime/tool versions; exact commands and configuration; raw logs and exit codes; test counts/results; skipped, flaky, failed and not-run tests; reviewer and review date.

Keep two separate status axes:

**Task lifecycle status:** PROPOSED, HOLD_FOR_APPROVAL, READY, RUNNING, SUBMITTED, REVIEWING, ACCEPTED, BLOCKED, CHANGES_REQUESTED, CANCELLED.

**Test evidence status:** `PASS`, `FAIL`, `NOT RUN`, `NOT VERIFIED`, `INCONCLUSIVE`, `BLOCKED`.

Do not put test-evidence states in a task Outcome field as if they were lifecycle states. Never convert NOT RUN, NOT VERIFIED, or INCONCLUSIVE into PASS. A task may be SUBMITTED while its test evidence remains NOT RUN or NOT VERIFIED.

## Phase 6 — Disaster recovery and continuity

Plan and verify independent backup destination/account separation, Git history/refs/tags/releases and required GitHub metadata, design originals and issue/PR evidence, encryption/access/retention/key custody, RPO/RTO, backup cadence, integrity manifests, isolated restore tests and exclusions.

**Authorization workflow for external backup:**
1. document the proposed scope, destination/account boundary, data classes, exclusions, encryption/key custody, retention, cost, RPO/RTO and access roles;
2. submit a specific authorization request to the project owner; do not create an account, upload, or access assets while awaiting approval;
3. record the owner's explicit decision, scope, date, approving identity and any conditions in an ADR/Issue;
4. after approval, perform only the authorized backup and record manifest/hash;
5. independently read back and restore to an isolated destination, then record evidence and reviewer;
6. if approval is denied or unavailable, mark external backup and restore as `BLOCKED` or `NOT VERIFIED`, record the risk and owner decision; do not claim governance readiness.

Do not create external storage accounts, upload data, change retention, or access user assets without authorization. A recovery test must restore from the independent copy to an isolated destination, verify refs and file hashes, document commands/logs/exit codes and elapsed time, and be reviewed by someone other than the backup operator. Keep recovery status `NOT VERIFIED` until a real restore test passes.

## Phase 7 — Cold-start acceptance

Give a fresh agent only the repository URL, management entry path and one active task ID. Do not provide chat history, private notes or oral project recap. Require it to report project purpose/owner, current default branch/full HEAD SHA, approved design sources/provenance, active tasks/PRs/dependencies/blockers, authorized and prohibited actions, next safe action, and repository evidence supporting each material claim.

Score the seven checks in `references/RECOVERY_AND_COLDSTART.md`. A missing answer scores zero; it is not by itself a fabricated-fact veto. Any fabricated authorization, test result, design approval, task status or repository fact is an automatic FAIL. Record defects and rerun after correction.

## Required execution behavior for this skill

When invoked, do not merely explain this framework. Perform the highest-value authorized actions:
1. inspect existing project evidence and permissions;
2. report verified baseline facts and critical unknowns;
3. create a scoped management bootstrap plan;
4. establish management files and GitHub Issues/PRs on an isolated branch, if authorized and technically possible;
5. read back every created file and verify branch/commit/PR state;
6. open follow-up tasks for design recovery, backup/restore and cold-start validation;
7. stop before any unapproved merge, production operation, external upload or destructive change.

If tools are unavailable, state exactly what could not be done and provide concrete artifacts or commands without claiming execution.

## Definition of done

Governance readiness requires a canonical management entry point; live work/decision tracking; design provenance; tasks with scope/authority/baseline/acceptance evidence; reproducible handoffs; independent verification where material; a successfully restored independent backup; and a passing no-memory cold-start test. If external backup is not authorized, report the gate as BLOCKED/NOT VERIFIED and seek an owner decision; do not silently waive it or claim full readiness.

A created folder, draft PR, backup script, or written policy alone does not satisfy this definition.

## Reference material

- [Project bootstrap checklist](references/PROJECT_BOOTSTRAP_CHECKLIST.md)
- [Governance and traceability model](references/GOVERNANCE_MODEL.md)
- [Disaster recovery and cold-start checklist](references/RECOVERY_AND_COLDSTART.md)
- [Reproducible execution playbook](references/EXECUTION_PLAYBOOK.md)
- [Portable quick start](PORTABLE_QUICKSTART.md)
- [Reusable templates](templates/)
- [Example project structure](examples/PROJECT_STRUCTURE.md)
