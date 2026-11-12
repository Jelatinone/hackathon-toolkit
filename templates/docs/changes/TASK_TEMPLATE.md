# Task outcome and evidence

Instantiate in the starter's docs/changes using an allocated ID. The author owns implementation evidence; reviewer/integration owner owns review and merge fields after handoff. Example IDs are not allocations.

```yaml
schema_version: 2
id: "HK-001"
checkpoint_id: "CP-001"
status: "planned"
branch: "feat/HK-001-foundation"
base_ref: null
owner: null
created_at: null
updated_at: null
plan_version_at_start: 0
feature_ids: ["F-001"]
contract_ids: ["CT-001"]
depends_on: []
owned_paths: []
```

## 1. Outcome and acceptance

**Objective:** unresolved. **Visible flow:** Given starting condition, when action, then observable result. Include a representative input and meaningful edge case. **Out of scope:** unresolved. **Cut/fallback:** unresolved.

## 2. Implementation plan

### Objective

Unresolved.

### Scope and exclusions

Unresolved.

### Inputs and baseline

Unresolved.

### Ordered steps

| Step | Outcome | Task IDs | Owned paths | Dependencies | Verification |
| --- | --- | --- | --- | --- | --- |
| 1 | Unresolved | HK-001 | Unresolved | None | Unresolved |

### Acceptance and verification

Unresolved.

### Risks and rollback

Unresolved.

### Decisions requiring approval

Unresolved.

## 3. Actual changes and evidence

**Delivered behavior:** None yet.

| Revision/artifact | Paths/components | Observable behavior |
| --- | --- | --- |
| None | None | Not implemented |

| Check | Revision/artifact | Environment | Expected | Observed | Status |
| --- | --- | --- | --- | --- | --- |
| Acceptance | None | None | Defined flow | Not implemented | not_run |

**Known limitations / not tested:** unresolved. Evidence must identify dirty working trees accurately; recheck changed code/environment/scope.

## 4. Proposed deviations

| Change ID | Approved baseline / contract | Proposed deviation | Reason | Impacted consumers | Alternatives | Approval state | Approval reference |
| --- | --- | --- | --- | --- | --- | --- | --- |

None — contracts preserved. If this changes, replace that statement with proposal rows. States: proposed, accepted, rejected, superseded. A proposal does not approve changes; the integration owner synchronizes accepted decisions and PLAN.

## 5. Handoff and merge gate

- [ ] Owned scope or explicit cross-owner agreement.
- [ ] Representative behavior and edge case verified.
- [ ] Required checks pass; unavailable checks block readiness; inapplicable checks have reasons.
- [ ] Contracts preserved or deviations approved.
- [ ] Required real integrations and core journey verified.
- [ ] No secrets/private data in changes.
- [ ] Rollback and unfinished work recorded.

```yaml
reviewer: null
review_status: "pending"
approval_ref: null
integration_commit: null
merged_at: null
stable_release_including_change: null
rollback: null
```

**Integrator note:** what must happen before merge, who receives ownership, environment prerequisites, and next action. Task statuses: planned, in_progress, blocked, ready_for_review, merged, deferred. Review statuses: pending, approved, rejected.
