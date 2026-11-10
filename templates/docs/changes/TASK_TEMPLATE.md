# TASK-ID — Short, outcome-focused title

> Copy to `docs/changes/HK-###.md` **when creating the task**. One file per task/branch. The assigned agent or developer owns it throughout implementation. This records actual evidence and *proposed*, not automatically approved, contract deviations.

```yaml
schema_version: 1
id: HK-###
status: planned  # planned | in_progress | blocked | ready_for_review | merged | deferred
branch: feat/HK-###-topic
base_ref: [stable tag or SHA]
owner: [FILL]
created_at: [ISO 8601]
updated_at: [ISO 8601]
plan_version_at_start: [integer]
feature_ids: [F-###]
contract_ids: [CT-###]
depends_on: [HK-###]
owned_paths: [paths]
```

## 1. Outcome and acceptance

**One-sentence objective:** [FILL]

**Visible acceptance flow:**

1. Given [starting condition]
2. When [user action / API call]
3. Then [observable result and precise expected outcome]

**Out of scope:** [FILL]  
**Cut/fallback if delayed:** [FILL]

## 2. Implementation plan (brief, before coding)

| Step | Change area | Test/proof | Dependency |
| --- | --- | --- | --- |
| 1 | [FILL] | [FILL] | [FILL] |

## 3. Actual changes and evidence

**Delivered behavior:** [Describe what works, not just changed filenames]

| Commit SHA | Paths/components | Observable behavior |
| --- | --- | --- |
| [FILL] | [FILL] | [FILL] |

**Verification results:**

| Command or E2E action | Environment | Expected | Observed | Pass/fail/not-run |
| --- | --- | --- | --- | --- |
| [FILL] | [FILL] | [FILL] | [FILL] | not-run |

**Known limitations / NOT tested:** [FILL]

## 4. Proposed deviations (the key integration section)

| Change ID | Approved baseline / contract | Proposed deviation | Reason | Impacted consumers | Alternatives | Approval state |
| --- | --- | --- | --- | --- | --- | --- |
| DEV-001 | [CT-###, exact version] | [FILL] | [FILL] | [FILL] | [FILL] | proposed |

Approval states: `proposed` / `accepted` / `rejected` / `superseded`. **Do not silently alter `PLAN.md` or consumer interfaces** because this row exists; contact the integration owner. When approved, the integrator assigns a decision ID in `docs/DECISIONS.md` and updates the canonical plan if needed.

If there are **no deviations**, write **None — contracts preserved**. This explicit statement is useful during merge review.

## 5. Handoff and merge gate

- [ ] Owned paths only, or cross-owner edits explicitly coordinated.
- [ ] Acceptance behavior demonstrable with representative input.
- [ ] Unit tests + edge tests pass (actual commands listed above).
- [ ] Typecheck/build/lint recorded or clearly marked not run.
- [ ] Shared contracts unchanged **or** deviations approved.
- [ ] E2E user journey verified (or honestly marked unverified).
- [ ] Secrets and private data absent from changes.
- [ ] Fallback/rollback documented.

```yaml
reviewer: [FILL]
review_status: pending  # pending | approved | rejected
integration_commit: [FILL]
merged_at: [ISO 8601 or null]
stable_release_including_change: [tag or null]
rollback: [command/tag/feature flag]
```

**Short integrator note:** [What must happen before merge and which team members need to know]
