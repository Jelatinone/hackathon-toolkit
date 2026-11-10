# Architectural Decisions — Accepted Only

> This is the canonical ledger for decisions **approved by the integration owner**. Do not use it as a brainstorming file. Proposed changes live in each branch's `docs/changes/<TASK-ID>.md` until accepted. Keep entries concise and append new decisions rather than silently modifying the meaning of old ones.

## Decision index

| Decision ID | Date | Status | Title | Origin task | Plan version |
| --- | --- | --- | --- | --- | --- |
| ADR-001 | [ISO date] | accepted | [FILL] | HK-001 | 1 |

## ADR-001 — [Short decision statement]

```yaml
id: ADR-001
date: [ISO 8601]
status: accepted # accepted | superseded
approver: [release/integration owner]
origin_task: HK-001
plan_version: 1
supersedes: null
```

**Context:** What failed or changed that made this decision necessary? Cite concrete evidence.

**Decision:** State the chosen interface/model/runtime behavior precisely. Link the affected contract (`CT-###`) and modules.

**Reasoning:** Why this option rather than a simpler alternative? Mention time and integration costs.

**Affected consumers and migrations:** Who needs to adapt? Is data migration or service redeploy required?

**Verification / gate:** Tests or demonstration proving the decision is safe enough.

**Consequences and rollback:** What new limitations are introduced? How can the change be reversed?

**Source:** `docs/changes/HK-001.md`, commit `[SHA]`.

---

## How to add a decision

1. Read the proposed deviation in its task note.
2. Review effects on the core demo, existing contracts and other branches.
3. Accept/reject/defer explicitly, assigning a unique `ADR-###` only if accepted.
4. Update the corresponding `PLAN.md` contract and plan version in the same integration step.
5. Record tested results, impacted consumers and the final merge SHA in both locations.
