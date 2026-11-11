# Example project repository structure

This is an example, not a mandatory layout. Adapt it to the language, framework, scale, security needs and existing conventions of the project.

```text
project/
├── .agents/
│   └── skills/
│       └── software-project-governance/
│           └── SKILL.md
├── docs/
│   ├── requirements/
│   ├── architecture/
│   ├── security/
│   ├── testing/
│   ├── operations/
│   └── management/
│       ├── README.md
│       ├── PROJECT_CHARTER.md
│       ├── PROJECT_STATE.md
│       ├── WORK_REGISTER.md
│       ├── DESIGN_BASELINE_INDEX.md
│       ├── DECISION_LOG.md
│       ├── OPERATING_RULES.md
│       ├── DISASTER_RECOVERY.md
│       └── templates/
├── src/
├── tests/
├── scripts/
└── .github/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE.md
```

The management control plane may live in a separate repository if the program spans multiple product repositories or needs independent access control. Keep links and commit SHAs between the control plane and each product repository.
