# Project Bootstrap Checklist

Use this checklist for a new project or an inherited project. Record every result in GitHub; do not leave the completed checklist only in chat.

## A. Ownership and purpose
- [ ] Project owner and decision authority identified.
- [ ] Purpose, users, success criteria, constraints and risk class recorded.
- [ ] Repository owner, visibility, default branch and access model verified.
- [ ] Product repositories and any separate management/control repository identified.

## B. Existing-state inventory (mandatory for inherited projects)
- [ ] Default branch HEAD and timestamp recorded.
- [ ] Branches, tags, commits and release history inventoried.
- [ ] Open and closed PRs inventoried with base/head SHAs.
- [ ] Issues, milestones and project boards inventoried.
- [ ] Requirements, design, architecture, security, test and release docs located.
- [ ] CI workflows, dependency manifests, build scripts and test logs located.
- [ ] Active developer/AI work and unmerged delivery branches protected.
- [ ] External project stores and references recorded without unauthorized access.
- [ ] Missing/ambiguous files classified by recoverability; originals preserved.

## C. Management control plane
- [ ] Canonical management README created or identified.
- [ ] Project charter and authority boundaries recorded.
- [ ] Timestamped project-state snapshot with full SHA created.
- [ ] Work register links to live Issues.
- [ ] Task, handoff, decision, execution and acceptance templates available.
- [ ] Change-control and review rules defined.
- [ ] Security/data boundaries and incident escalation documented.

## D. Design baseline
- [ ] Requirements/design source inventory completed.
- [ ] Each source has path, version, SHA/hash, origin and approval status.
- [ ] Superseded and conflicting versions preserved.
- [ ] Requirement → design → code → test → acceptance traceability established.
- [ ] Unknowns and conflicts explicitly logged.

## E. Work tracking
- [ ] Work packages broken into Issues with unique IDs.
- [ ] Every READY task has baseline SHA, scope, owner, authority and acceptance criteria.
- [ ] Dependencies and blockers represented.
- [ ] PRs link to Issues and use isolated branches.
- [ ] Independent review assigned for material changes.

## F. Recovery and continuity
- [ ] Backup scope, destination, RPO/RTO, retention and access control approved.
- [ ] Independent backup created and read back.
- [ ] SHA-256 or equivalent integrity manifest verified.
- [ ] Isolated restore test completed.
- [ ] No-memory cold-start test completed.
- [ ] Recovery limitations and metadata exclusions recorded.

## G. Final readiness
- [ ] All required gates have evidence.
- [ ] Project owner approved the management baseline.
- [ ] Open risks and not-verified items remain visible.
- [ ] Next authorized task is clear and linked.

## Template installation
- [ ] Check for existing equivalent project templates first.
- [ ] If none exist, copy the needed files from the pinned skill `templates/` directory into this project's `docs/management/templates/` (or documented equivalent).
- [ ] Record the source skill version/tag/full SHA and exact destination paths in the management README.
- [ ] Keep project-specific edits in the project repository; do not silently alter the shared source templates.
- [ ] If referencing shared templates instead of copying, verify all contributors have access and pin the exact release/full SHA.
