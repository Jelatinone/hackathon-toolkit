# Shared project operating contract

Version 2. Adopt this through a starter's project instructions. **Project root** is the starter identified by the adapter/user; **toolkit root** is this pinned submodule. Never infer project root from a canonical skill's location or run project Git operations in the toolkit. This is not the toolkit maintenance contract.

## Authority and sources

Read project instructions, relevant approved PLAN sections, accepted DECISIONS, and assigned task notes before implementation. Kickoff and ideation can run before PLAN exists. Missing required records in later workflows block dependent work; templates are not approved records.

Order: current human authorization and official event rules; project working instructions; approved PLAN; accepted DECISIONS; task proposals/evidence; actual code/runtime observations. Report disagreements. Approved intent never proves actual behavior. Synchronize accepted architectural decisions with PLAN before dependent implementation. A branch proposal is not approval.

Read [FORMATS](FORMATS.md) before each workflow and follow its strict plans/reports. Use relevant [playbook](../HACKATHON_PLAYBOOK.md) sections rather than duplicating criteria. Reuse explicit authorization already given for the same action.

## Assignment and ownership

- One accountable owner, feature branch, and `docs/changes/<TASK-ID>.md` per task. The integration owner allocates IDs centrally; never guess IDs across active branches.
- Assign bounded vertical outcomes, acceptance, owned paths, dependencies, and rollback before coding. Use the [task template](../templates/docs/changes/TASK_TEMPLATE.md).
- Concurrent workers use separate worktrees/clones. Coordinate shared ports, databases, fixtures, and external services. Branches alone do not isolate working files or runtime resources.
- Propose public contract, security, deployment, ownership, and deadline-risking changes in the task note before implementing them; obtain responsible-owner approval.
- If an owner disappears, the integration owner can explicitly reassign after inspecting unfinished changes and environment requirements. Never discard another worker's work.
- Authors own implementation evidence; the designated reviewer/integration owner owns review, merge, and release fields after handoff. Do not use a shared multi-agent scratch log.

## Checkpoint execution

PLAN owns ordered checkpoints, tasks, commands, owners, official clock, and gates. Select the earliest approved unfinished checkpoint whose checkpoint dependencies are complete. Work only its assigned eligible tasks in listed dependency order; use listed order to break ties. Never claim tasks or launch other agents automatically.

Each task retains its own branch and note. Dependencies require an available approved base reference, not merely an unmerged predecessor. Stop dependent work rather than silently merging or changing ownership. Report partial outcomes and remaining blockers; do not advance to another checkpoint.

Write the strict implementation plan before edits, preserve neighboring behavior, run applicable checks, and update task evidence. Implementation can reach `ready_for_review`; only verified integration and checkpoint acceptance permit `complete`. Approval, task state, checkpoint state, workflow status, and review verdict are distinct.

## Verification, integration, and release

Inspect PLAN commands before executing them. Do not run source-rewriting formatters in test/review-only work. Test resources may be created within the designated test environment; destructive/external operations require applicable authorization. Record actual commands/actions, expectations, observations, exact revision/artifact, dirty-tree identity where applicable, and environment. Reassess evidence whenever code, environment, or acceptance scope changes.

Require representative input, a meaningful edge/failure case, integration coverage, and the core journey when applicable. `not_run` is never passed; `not_applicable` needs a reason. Required failures or unavailable checks block readiness. Documentation-only work uses document checks, not invented application tests. Mocks cannot prove a required live integration.

Review approval does not authorize merge, deployment, tagging, publication, or submission. An authorized integrator checks the integrated revision and synchronizes accepted records. Stable promotion uses a unique annotated tag on the exact verified integrated commit; never replace a tag. Record local creation separately from remote publication. Retain a known-good environment and rollback.

## Event and scope boundaries

Respect official eligibility, pre-existing-code, AI, licensing, coding-window, judging, and submission rules. Record sources and timezone/offsets in PLAN. Missing rules are uncertainty, not permission. Pre-event ideation does not authorize implementation.

Feature freeze stops new features. The release owner may authorize bounded critical fixes with impact, rollback, and renewed checks recorded. Capacity changes, missed gates, and scope cuts trigger replanning, not hidden expansion.

Never expose secrets, fabricate evidence, claim unsupported certification, bypass event/license rules, overwrite another worker, or force-push stable history. Qualify scientific, financial, modeled, and user-impact claims against inputs and evidence. Separate implemented, tested, planned, and hypothetical behavior.

Stop affected work on contradictory requirements, unavailable required access, ownership conflicts, invalid core assumptions, repeated baseline-threatening failures, or unapproved freeze exceptions. Continue independent authorized work when possible and report the concrete blocker.

## Handoff and persistence

Final reports follow FORMATS; `handoff-task` preserves task handoff fields inside that report. Reports stay in chat unless an owned note or explicit destination is assigned. Keep code, tests, and evidence together for review; commit only within the authorized project workflow. Toolkit updates are separate maintenance work.
