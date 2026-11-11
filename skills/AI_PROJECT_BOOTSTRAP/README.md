# Software Project Governance Skill

Reusable operating skill for building durable, GitHub-centered governance for software projects.

## Install / use

Choose the installation path supported by the target AI environment:

1. **Automatic Skill loading:** place this directory in the platform's documented project-skill directory and verify that the platform actually discovers it.
2. **Manual Skill loading:** provide the complete `SKILL.md` path or paste its content into the agent's project instructions; record the loaded version and SHA.
3. **No Skill mechanism:** use [PORTABLE_QUICKSTART.md](PORTABLE_QUICKSTART.md), a self-contained single-file operating guide that does not depend on frontmatter parsing or automatic discovery.

Do not assume that a directory name or frontmatter makes a platform load the skill. Confirm discovery by asking the agent to report the exact loaded path and version.

## Install templates into a project

The `templates/` directory in this skill is the reusable source set. During project bootstrap:
- reuse existing equivalent project templates if they already exist;
- otherwise copy the needed files to the target project's `docs/management/templates/` (or documented equivalent);
- record the skill release/tag/full SHA and the destination paths in the project's management README;
- keep project-specific edits in the project repository, not in the shared source copy.

Directly referencing the shared templates is acceptable only when all contributors have stable access to a pinned release or full commit SHA. See the template placement section in `SKILL.md`.

## Files

- `SKILL.md`: full workflow and operating rules.
- `PORTABLE_QUICKSTART.md`: single-file version for environments without Skill loading.
- `references/`: detailed checklists, governance model and reproducible execution examples.
- `templates/`: reusable project records.
- `examples/`: illustrative repository structure.

## Versioning

Use the Git tag/release and full commit SHA as the version identity. The initial content version is recorded in `SKILL_CHANGELOG.md`; do not rely on non-standard frontmatter fields.

## Safety

This skill is a process framework, not automatic permission. It never grants access to production systems, secrets, user data, branch protection, external storage, deployments, or default-branch merges. Each project owner retains decision authority.
