# Workflow formats

Format version 1; project template schema version 2. Names, heading order, metadata keys, table columns, and enumerated values are exact. Validation checks structure and selected consistency rules; it cannot certify truth, permission, or agent compliance.

## Encoding and metadata

Use UTF-8 Markdown. Metadata uses a fenced `yaml` block and the **JSON-valued YAML subset**: one `key: <JSON value>` per line; quoted strings, numbers, booleans, null, or JSON string arrays. No comments, duplicate keys, nested maps, multiline scalars, or aliases. This is valid YAML, not a general YAML parser. Skill frontmatter uses the same values between `---` delimiters.

Use `null` for an unknown scalar, `[]` for an empty list, and `None` for an empty prose section. Unknown is not approved. Resolve execution prerequisites before approval. Times include an offset; PLAN records the timezone. Preserve template heading levels and exact section names.

## Canonical skill definition

Frontmatter contains exactly `name` and `description` strings. Name matches its lowercase hyphenated directory. H2 headings exactly once, in order:

1. Purpose and triggers
2. Inputs and prerequisites
3. Read and write boundaries
4. Workflow
5. Outputs
6. Acceptance criteria
7. Failure and approval behavior

Each Outputs section's H3 headings declare the exact Result subsections for its report. These declarations are the report validator's source of truth. All sections remain present on blocked outcomes with evidence or `None` and an explanation.

## Agent plan

Standalone plans use report metadata then these H2 sections; inside task implementation plans use H3; inside report Result subsections use H4:

1. Objective
2. Scope and exclusions
3. Inputs and baseline
4. Ordered steps
5. Acceptance and verification
6. Risks and rollback
7. Decisions requiring approval

| Step | Outcome | Task IDs | Owned paths | Dependencies | Verification |
| --- | --- | --- | --- | --- | --- |
| 1 | Bounded result | Assigned IDs | Explicit paths | IDs or None | Observable check |

Use the [agent plan template](../templates/AGENT_PLAN.md). Implementation and replanning workflows embed these seven sections under their designated Result subsection. Format validity never grants approval. Validate standalone plans using `validate-report <path> --kind plan`.

## Final workflow report

Use the [report template](../templates/WORKFLOW_REPORT.md). Required metadata keys in order:

`format_version`, `workflow`, `status`, `project_root`, `toolkit_ref`, `plan_version`, `checkpoint_id`, `task_ids`, `subject_ref`.

- `format_version`: 1; `workflow`: canonical skill name.
- `status`: `proposed`, `completed`, `blocked`, `incomplete`. Completed means the requested workflow finished, not that its subject passed or was merged. Proposed awaits a decision; blocked lacks required prerequisites; incomplete has remaining requested work.
- `project_root`: resolved project path. `toolkit_ref`: exact Git revision, with dirty marker if applicable, or null with explanation if unavailable.
- `plan_version`: nonnegative integer or null before kickoff. `checkpoint_id`: CP ID or null. `task_ids`: string array.
- `subject_ref`: exact reviewed/tested revision or artifact, or null if absent. Never identify a dirty tree as an unchanged commit.

H2 sections: **Summary**, **Result**, **Changes**, **Verification**, **Risks and blockers**, **Next actions**. Result contains the skill's H3 declarations in order. Every section is nonempty. Verdict subsections use `ready`, `not_ready`, or `incomplete`, followed by evidence; a verdict grants no authority.

| Check | Revision/artifact | Environment | Expected | Observed | Status |
| --- | --- | --- | --- | --- | --- |
| Example | Exact identity | Runtime/services | Acceptance | Actual result/reason | not_run |

Statuses: `pass`, `fail`, `not_run`, `not_applicable`. Observed explains not-run/not-applicable checks. Every report has at least one row, including source inspection for analysis. Required failed/missing checks prevent ready. Extra prose within sections is allowed; extra H2/Result H3 headings are not. Embedded plans use the seven H4 headings above.

A ready verdict or ready/merged task cannot contain failed/not-run rows in its gate verification table. Discuss optional exploratory checks outside that gate table; do not hide a required check there.

Progress messages/questions are exempt. Reports remain in chat unless assigned a destination. The validator checks saved reports; it does not intercept chat or enforce behavior at runtime.

## Project templates

Preserve exact H2 sections, metadata keys, and table headers from [PLAN](../templates/PLAN.md), [DECISIONS](../templates/docs/DECISIONS.md), and [TASK_TEMPLATE](../templates/docs/changes/TASK_TEMPLATE.md). Add records using their H3 patterns, retaining project-specific prose. Remove unused example records. Empty decision ledgers and proposed kickoff plans with unresolved nulls are valid; unresolved execution inputs cannot be approved.

PLAN owns configuration and ordered `### CP-001` records. Checkpoint metadata: `id`, `objective`, `task_ids`, `depends_on`, `owner`, `approval`, `approval_ref`, `status`, `acceptance_gate`, `cut_fallback`, `evidence_ref`.

- Approval: `proposed`, `approved`, `rejected`; approved requires an explicit reference.
- Checkpoints: `planned`, `in_progress`, `blocked`, `ready_for_review`, `complete`, `deferred`.
- Tasks: `planned`, `in_progress`, `blocked`, `ready_for_review`, `merged`, `deferred`.
- Complete checkpoints require approved status and integration/gate evidence.
- Dependencies exist and are acyclic. Checkpoint task lists agree with the task registry. Task notes live outside the toolkit.
- Decisions: `accepted`, `superseded`; require approver and approval reference. Supersession preserves history.

Dates, commands, and owner roles are authoritative in PLAN. Task notes record execution ownership and evidence, not a second configuration. Reviewers own review/merge fields after handoff. Schema v1 projects need a reviewed migration; scripts never migrate them automatically.

## Native adapter

Adapters are exempt from canonical skill headings. They contain identical name/description frontmatter, a `hackathon-toolkit-adapter:v1 sha256=<digest>` marker, a `Canonical workflow` relative link, and instructions to retain the host project root and follow source formats. The SHA-256 covers the full generated text with its digest replaced by 64 zeroes (LF normalized). It detects accidental edits, not malicious tampering.

Instruction stubs use the same convention with an `instructions` marker. Bootstrap updates intact generated files only; user-owned collisions receive proposed snippets. Adapters contain no workflow bodies. Links resolve relative to their containing files, while project data paths remain rooted in the starter.
