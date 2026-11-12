# Architectural decisions

Canonical accepted decisions only. Proposed deviations stay in task notes. Preserve history and append superseding decisions; do not silently rewrite an earlier decision. Start with an empty index and add an allocated ADR record only after approval.

## Decision index

| Decision ID | Date | Status | Title | Origin task | Plan version |
| --- | --- | --- | --- | --- | --- |

## Accepted records

None.

For each accepted decision, replace None with `### ADR-001` (allocated ID), then a YAML block containing these keys: `id`, `date`, `status`, `approver`, `approval_ref`, `origin_task`, `plan_version`, `supersedes`. Use JSON-valued YAML. Status is accepted or superseded; supersedes is null or an earlier ADR ID.

Use these H4 fields in order for each record: Context; Decision; Reasoning; Affected consumers and migrations; Verification and gate; Consequences and rollback; Source.

Context cites evidence; Decision names the contract/version and modules; Reasoning includes simpler alternatives and integration cost; Verification names actual results or required gates; Source links the originating task and revision.

## Integration procedure

1. Read the proposed deviation and affected consumers.
2. Explicitly accept/reject/defer; allocate an ADR only for acceptance.
3. Synchronize PLAN, plan version, approval reference, and the decision before dependent implementation.
4. Record integrated verification and merge SHA once available; do not claim future evidence.
