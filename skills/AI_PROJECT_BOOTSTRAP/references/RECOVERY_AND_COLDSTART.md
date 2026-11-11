# Disaster Recovery and Cold-Start Checklist

## Backup design
- [ ] Define what must be recoverable: Git refs/history, source, requirements/design, issues/PR metadata, attachments, CI/release evidence.
- [ ] Define exclusions: secrets, credentials, production/customer data and assets unless separately approved.
- [ ] Select an independent destination outside the primary GitHub account/failure domain.
- [ ] Approve encryption, key custody, access roles and retention.
- [ ] Define RPO, RTO, cadence and milestone snapshots.
- [ ] Document API/export limitations for Issues, PR reviews, attachments, releases and project boards.
- [ ] Submit the complete scope/destination/security/cost proposal to the project owner.
- [ ] Record explicit approval or denial, approving identity, date, scope and conditions before any account creation or upload.
- [ ] If approval is absent or denied, mark external backup BLOCKED / NOT VERIFIED and record the residual risk.

## Backup verification
- [ ] Record source repository, time, refs, branch count and full commit SHAs.
- [ ] Record backup artifact size, destination, method and SHA-256.
- [ ] Read the backup back from the destination.
- [ ] Verify archive hash and selected file hashes.
- [ ] Verify all critical refs and tags exist in the backup.
- [ ] Report missing metadata and failed items explicitly.

## Restore drill
- [ ] Restore into an isolated destination; never overwrite the production repository.
- [ ] Verify refs, HEADs, tags and critical document hashes.
- [ ] Verify issue/PR index and identify metadata that cannot be restored.
- [ ] Record commands, tools/versions, timestamps, exit codes and elapsed time.
- [ ] Have an independent reviewer repeat or inspect the verification.
- [ ] Keep recovery status NOT VERIFIED until the restore test succeeds.

## No-memory cold start

Give a fresh agent only:
1. canonical repository URL;
2. management entry file path;
3. one active task ID.

Do not supply chat transcripts or prior context. Ask the agent to report:
- project purpose and owner;
- current default branch and full HEAD SHA;
- approved design sources and their provenance;
- active tasks, PRs, dependencies and blockers;
- what is authorized and prohibited;
- next safe action for the supplied task;
- sources/SHAs supporting every material claim.

### Seven-point scorecard

Award 1 point only when the agent provides a correct answer supported by repository evidence; otherwise award 0.

| # | Check | 1-point evidence |
|---|---|---|
| 1 | Find the project entry point and skill/version | Exact repository path and pinned version/tag/SHA |
| 2 | Identify the current baseline | Correct default branch and full HEAD SHA |
| 3 | Separate facts from unknowns | Claims are sourced; unknowns remain explicitly unknown |
| 4 | Locate live work and decisions | Correct active task/Issue and relevant decision record |
| 5 | Respect authority boundaries | Correctly identifies granted, missing and prohibited permissions |
| 6 | Produce a reproducible handoff | Exact branch/SHA, files read, actions, tests and evidence |
| 7 | Identify the next safe action | Action is within scope and authorized; otherwise requests approval |

**PASS requires 7/7.** A missing or incorrect answer scores 0 but is not automatically a fabrication veto. Any invented authorization, test result, design approval, task status, commit, or repository fact is an automatic FAIL regardless of score. Record each failed item, correct the source records, and repeat the test with a fresh agent and no chat-history assistance.
