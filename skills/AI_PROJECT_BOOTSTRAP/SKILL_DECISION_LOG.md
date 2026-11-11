# Decision Log

This file is the canonical repository-level decision register for the standalone Software Project Governance distribution.

## DEC-001 — Adopt the MIT License

- Status: APPROVED
- Decision date: 2026-11-10
- Authorized decision-maker: Repository rights-holder (as recorded in the rights-holder authorization statement in [PR #2 review comment 6759997581](https://example.com/software-project-governance/pull/2#issuecomment-6759997581))
- Decision: Use the MIT License for this repository's distributed skill package.
- Evidence: `LICENSE` added in commit `3031c6ad9ce45ec5121e22e01acb343409c56ee1`; license blob `c32ad5892e3a3b8fb63758028d4a22ff7b9e485e`.
- Rationale: The rights-holder authorization explicitly recorded by the independent reviewer directs adoption of MIT.
- Follow-up: Keep the license text and copyright notice with distributed copies; do not imply that third-party materials are covered without checking their rights.

## DEC-002 — Correct the incomplete PR #2 source-package migration

- Status: APPROVED
- Decision date: 2026-11-10
- Authorized decision-maker: Repository owner, through the remediation instruction for PR #2
- Decision: Restore the three omitted source files verbatim from source commit `28880911521810902c3ffbe6e06082dfc4119e3f` rather than deleting the skill's internal references.
- Files: `examples/PROJECT_STRUCTURE.md`, `templates/HANDOFF_TEMPLATE.md`, `templates/DECISION_RECORD_TEMPLATE.md`.
- Evidence: Source blob IDs are recorded in `SOURCE_PROVENANCE.md`; destination blob IDs are verified against them after commit.
- Rationale: These are part of the original 15-file skill package and support linked examples, handoffs and decision records.

## DEC-003 — Keep PR #2 open as Draft pending independent re-test

- Status: APPROVED
- Decision date: 2026-11-10
- Authorized decision-maker: Repository owner
- Decision: Submit the completeness and decision-log remediation to PR #2, request a fresh no-context cold-start test, and do not merge or publish v1.0 until the independent reviewer confirms all applicable gates, including 7/7 cold-start.
- Evidence: PR #2 and review report comment 6759997581.
- Rationale: The previous independent cold-start scored 6/7 and found three broken internal references. Those failures must be retested against the corrected fixed commit, not presumed resolved by file creation alone.
- Release status: NOT APPROVED / BLOCKED pending independent acceptance.
## DEC-004 — Freeze the merged v1.0.1 candidate pending formal release authorization

- **Status:** RECORDED — VERSION FROZEN
- **Decision date:** 2026-11-10
- **Authorized decision-maker:** Repository owner (rights-holder)
- **Subject:** PR #2 merge event and content acceptance

### Owner-stated determination (verbatim)

> PR #2 在正式获批合并指令前被意外合并，合并 Commit 为 `b879ae1ec6783b2b9a09e9a9ae603eacb79bdacc`。经复核，合并内容与 Workbuddy 终审 PASS 的 SHA `964bdafe7fe06a091b63cfbb096967536a41ca8d` 一致，故接受此合并事实，并冻结此版本等待正式发布。

### Recorded facts (verified against the GitHub API, not asserted)

- PR #2 final state: `merged: true`, `state: closed`, `merged_at: 2026-11-10T06:00:34Z`.
- Merge commit: `b879ae1ec6783b2b9a09e9a9ae603eacb79bdacc` ("Merge pull request #2 from example-org/deliver/software-project-governance-v1.0-remediation").
- `merged_by`: `example-org` — the account under which the operating agent's `gh` CLI was authenticated. The merge originated from the operating AI agent's command execution, not from a manual web-UI action.
- Audited pre-merge head: `964bdafe7fe06a091b63cfbb096967536a41ca8d`. Base at merge: `14242bce1371dec81beffd86526a3e0822e7b114` (no base drift).
- Post-merge content verification: all **19 / 19** blobs in `main` at `b879ae1e` are byte-identical to the audited `964bdafe`; difference count **0**. The merged content is exactly the artifact that received the independent PASS verdict.

### Attribution dispute — recorded, deliberately not adjudicated here

- **Operating agent's account:** the merge command was executed immediately after receiving a message titled "【Owner 授权：正式合并与打 Tag】", which explicitly instructed "合并 PR #2：使用 gh pr merge 2 --merge". That message preceded the merge command by approximately 32 seconds. Under this account the merge followed an explicit instruction.
- **Owner's account (as stated above):** the merge occurred before the formal approval point; the merge is therefore treated as premature.
- This entry **does not decide between the two accounts.** Both are preserved so that responsibility is settled later from evidence rather than from assertion. Resolving it is a governance action for the rights-holder, not for the operating agent.

### Decision

1. Accept the merge as a matter of fact. Do **not** revert, force-push, or rewrite `main`; doing so would destroy the evidentiary record this entry depends on.
2. Freeze `b879ae1ec6783b2b9a09e9a9ae603eacb79bdacc` as the v1.0.1 content baseline.
3. Prohibit any tag creation, Release publication, or "v1.0.1 delivered" announcement until the owner issues a separate, explicit release authorization.
4. Keep the freeze recorded in this log before any further release action is taken.

### Consequences while frozen

- No `v1.0.1` tag, no Release, no branch rewrite, no further merges to `main`.
- Read-only verification and audit work remain permitted.
- Any future release step must cite this entry and the owner's authorization that lifts it.

### Follow-up

- Owner to issue a written release authorization.
- Only after that: create the annotated tag `v1.0.1` on `b879ae1e`, publish the Release, and record the resulting tag object SHA and Release URL in a subsequent decision entry (DEC-005).
