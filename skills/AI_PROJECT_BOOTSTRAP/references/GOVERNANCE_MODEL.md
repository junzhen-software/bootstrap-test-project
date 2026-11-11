# Governance and Traceability Model

## Record types and authority

| Record | Canonical home | What it proves | What it does not prove |
|---|---|---|---|
| Charter | Versioned repository file | Purpose, roles, authority, boundaries | Product design approval unless explicit |
| Project state | Versioned timestamped snapshot | State observed at a specific time/SHA | Current state after later changes |
| Issue | GitHub Issues | Task/defect/risk/decision request and lifecycle | Code merged or accepted |
| Commit | Git history | Exact content snapshot | Review or acceptance |
| Pull request | GitHub PR | Proposed change and review discussion | Merge approval or phase acceptance |
| Design baseline | Approved versioned files + decision record | Authorized design intent | Correct implementation |
| Test evidence | Raw logs + execution record | What was run and its result | Untested environments/platforms |
| Acceptance record | Authorized approval + evidence | Formal acceptance against criteria | Future fitness after changes |
| Backup record | Backup manifest + restore evidence | Specific copy was made and verified | Recoverability until restore tested |

## Minimum control records

Every project must have equivalent content for a canonical entry point/owner/authority, timestamped state and full SHA, work register, operating rules, design-baseline index, decision mechanism, disaster-recovery status, security/data boundaries, and task/handoff/execution/acceptance records. Reuse existing files and naming. These are content requirements, not mandatory filenames. Incident records are created when incidents occur.

## Authority boundaries

The project owner retains authority for scope, priorities, risk acceptance, design approval, production access, releases, merges and policy changes unless explicitly delegated in writing.

AI assistants and agents may inspect and propose. They may execute only within explicit task authorization. A task-specific permission does not imply broader permissions.

## Traceability chain

Every consequential requirement/change should be linked:

`Need/Problem → Requirement ID → Design section/version → Implementation path/commit → Test ID/log → Acceptance record → Release`

Where a link is missing, create a traceability gap item; do not invent the missing link.

## Decision records

Record context, evidence, options, selected decision, rationale, impact, rejected alternatives, risks, rollback, decision-maker, date and status. AI-generated recommendations remain PROPOSED until the authorized decision-maker approves them.

## Change control

For any material change, record reason and affected requirements; affected design, interfaces, data, security and dependencies; migration and compatibility; test/acceptance impact; rollback/recovery; and owner approval.

## Separate lifecycle and evidence states

Task lifecycle: PROPOSED, HOLD_FOR_APPROVAL, READY, RUNNING, SUBMITTED, REVIEWING, ACCEPTED, BLOCKED, CHANGES_REQUESTED, CANCELLED.

Test evidence: PASS, FAIL, NOT RUN, NOT VERIFIED, INCONCLUSIVE, BLOCKED.

Do not mix these semantic axes in one status field. A task may be SUBMITTED while its tests remain NOT RUN or NOT VERIFIED.

## Independent review

An independent reviewer must not have produced/materially edited the artifact or participated in its implementation or approval. The reviewer must fetch the fixed SHA, identify files and criteria reviewed, disclose prior involvement/conflicts/limitations, and publish a written finding tied to that SHA. A producer's self-review or response to findings is not independent review.

## Evidence language

Use only precise states: PASS, FAIL, NOT RUN, NOT VERIFIED, INCONCLUSIVE, BLOCKED for evidence. Preserve raw logs and failed evidence. Never promote missing evidence to PASS.

## Cross-agent handoff

A receiving agent must independently fetch the cited commit and files. A forwarded summary is a navigation aid, not proof that the receiver has the same source version.
