# Source provenance

## Source package identity

This standalone distribution is based on the complete reusable skill directory at a fixed source commit.

- Source repository: https://example.com/PROJECT_NATURE
- Source branch: `fix/software-project-governance-v1.0-remediation`
- Source commit: `28880911521810902c3ffbe6e06082dfc4119e3f`
- Source directory: `.agents/skills/software-project-governance/`
- **Total source package files: 15** (all 15 are inventoried below; none intentionally excluded)
- Destination repository: https://example.com/software-project-governance
- Destination delivery branch: `deliver/software-project-governance-v1.0-remediation`

The skill package files are placed at the destination repository root for independent distribution. Each source Git blob SHA below identifies the exact file content copied from the fixed source commit.

## Complete source package inventory (15/15)

| Destination path | Source Git blob SHA |
|---|---|
| `SKILL.md` | `ee8fc2d6914880a43260ea68c8e3fd63274aeb39` |
| `README.md` | `5961c5fffff747d2732aabdbc568ab4e98a091e0` |
| `PORTABLE_QUICKSTART.md` | `39e5d441d676a6694da3903159c8522c619f7ebc` |
| `templates/ACCEPTANCE_TEMPLATE.md` | `7e9cef5f77c8c541620f16aeeab50c3c88074b0f` |
| `templates/INCIDENT_TEMPLATE.md` | `c3bdbb3352b45b92923e84084f1a98aa49a39752` |
| `references/EXECUTION_PLAYBOOK.md` | `f4e2fc1e3060470515cf136b4d1e13f42720175f` |
| `references/RECOVERY_AND_COLDSTART.md` | `da4943db4aff46448fe3bd22411bbbd4ed4826f9` |
| `references/GOVERNANCE_MODEL.md` | `9fa8a29fb8653920cc212c07eaf1e8c4be86e59a` |
| `references/PROJECT_BOOTSTRAP_CHECKLIST.md` | `55949dfcc709665d38b519c6d59a688488602fdb` |
| `templates/TASK_TEMPLATE.md` | `d53b150879b58df6bc03d0bd67b6bb784ab6df13` |
| `templates/EXECUTION_RECORD_TEMPLATE.md` | `99731764f1d666951f888637e7b58b41dd6956ca` |
| `SKILL_CHANGELOG.md` | `226226d87485c186f49afbbecd461a8884877a78` |
| `examples/PROJECT_STRUCTURE.md` | `dc446be7505f49f895f4074d4137afbb2c150b83` |
| `templates/HANDOFF_TEMPLATE.md` | `0a174aa4a764b19ac0e1fbc6d65eae60ba976094` |
| `templates/DECISION_RECORD_TEMPLATE.md` | `4a0eeb9cc370ba720a911565154ebaa65c9b446c` |

## Supplemental repository governance and distribution files

These files are repository-level additions, not members of the 15-file source skill package:

| File | Purpose / provenance |
|---|---|
| `INITIALIZATION.md` | Minimal initialization note committed on `main` before the delivery branch was created |
| `LICENSE` | MIT License; added on the delivery branch in commit `3031c6ad9ce45ec5121e22e01acb343409c56ee1`, following rights-holder authorization recorded in PR #2 comment [6759997581](https://example.com/software-project-governance/pull/2#issuecomment-6759997581) |
| `SOURCE_PROVENANCE.md` | This source inventory and provenance record |
| `SKILL_DECISION_LOG.md` | Repository-level decision register for distribution, licensing and release gates |

## Omission and correction history

The first PR #2 delivery omitted three source files inadvertently: `examples/PROJECT_STRUCTURE.md`, `templates/HANDOFF_TEMPLATE.md`, and `templates/DECISION_RECORD_TEMPLATE.md`. They were not intentionally excluded. This remediation adds the exact source-commit contents and records their original source blob SHAs above. The complete source package is therefore 15/15 files after this correction.

## License status

The repository includes an MIT `LICENSE` file. The earlier statement that no license file was included is obsolete and withdrawn. The license decision and its recorded authorization evidence are documented in `SKILL_DECISION_LOG.md` and the PR #2 review discussion. Do not describe this repository as unlicensed.