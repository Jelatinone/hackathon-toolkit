# AGENTS.md — Hackathon Agent Operating Contract

**Template version:** 1.0  
**Scope:** Copy this document into the root of a new hackathon project's repository. Replace all `[FILL]` values and adapt commands. It is a *process contract*, not authorization to implement unspecified features.

## 0. Non-negotiables

1. Read `PLAN.md` (approved source of truth), this `AGENTS.md`, and the assigned `docs/changes/<TASK-ID>.md` before making changes.
2. Work only within the assigned task's goals and owned modules. If a task is missing, request/record one before editing. Do not silently expand scope to attractive features.
3. Preserve agreed interfaces. If you discover that a contract is wrong, **propose the deviation in your task note first**; do not quietly rewrite canonical `PLAN.md` or break dependent teams.
4. Keep `main` stable. Work on the assigned branch. Never force-push, overwrite another worker's work, delete unknown changes, expose secrets or merge unverified work.
5. Changes must be demonstrable and testable. Explain actual results, limitations and unverified assumptions. Never fabricate test outcomes, code compliance or external integration success.
6. Follow hackathon rules, licenses, AI-use restrictions and the official start/end time. Pre-event ideation does not automatically permit pre-event project coding.

## 1. Read order and sources of truth

| Priority | Source | Interpretation |
| --- | --- | --- |
| 1 | Current human instruction + event rules | What is currently authorized |
| 2 | `AGENTS.md` | How to work in this repo |
| 3 | `PLAN.md` approved fields | What is intended, contracted, prioritized |
| 4 | `docs/DECISIONS.md` accepted records | Explicit approved architectural exceptions/updates |
| 5 | Assigned `docs/changes/<TASK-ID>.md` | Branch-specific work package and evidence |
| 6 | Actual code/tests/runtime behavior | Current implementation; report conflicts with approved intent |

If sources disagree, report the discrepancy. Never assume a branch-local claim is an approved architectural change just because it appears in Markdown.

## 2. Operating modes

### A. Idea analysis (before implementation)

When asked to evaluate hackathon concepts:

1. Read event eligibility, time limits, exact track prompts and judging criteria. Ask for official rules if they are unavailable; mark unknowns instead of inventing them.
2. Produce **forward** candidates from user problems and **backward** candidates from sponsor requirements, then look for concepts that satisfy both.
3. For each candidate, produce a compact structured brief: user, decision improved, one-sentence promise, 30-second demo, MVP, standout differentiator, sponsor integration, unknown technical dependencies, expected cuttable scope.
4. Apply the Playbook's 100-point weighted rubric; include a confidence/uncertainty note and explicit veto risks. Scores are *decision aids*, not forecasts of an award.
5. Identify the **smallest critical-path proof** and what must be tested first. No unsupported future feature should be presented as shipped.
6. Recommend one concept and explain what must be cut if team availability shrinks.

**Idea analysis response format:** `CONCEPTS → SCORECARD → RISKS → RECOMMENDATION → CORE DEMO → FIRST TECHNICAL TEST`.

### B. Implementation

Before coding, write or verify this short task contract in your task note:

```yaml
id: HK-001
status: in_progress  # planned | in_progress | blocked | ready_for_review | merged | deferred
branch: feat/HK-001-topic
base_ref: STABLE-V1
owner: [FILL]
objective: [FILL]
contracts_touched: [identifiers]
owned_paths: [list]
depends_on: [task IDs]
acceptance: [visible behavior and runnable checks]
```

**Preferred work batch:** A coherent, bounded vertical change, e.g. simulation parameter + backend path + consumer rendering + associated tests. Do not micromanage every file with separate prompts; do not turn “group changes” into a vague mandate to rewrite the whole application.

Implementation steps:

1. Inspect relevant current code and docs; identify all affected contracts and consumers.
2. Write a short plan with dependencies, observable success, tests and rollback strategy.
3. Implement only the assigned bounded outcome; preserve neighboring behavior.
4. Add/update tests for each changed contract and edge case. Use suitable mocks for services, but verify a real integration when the feature depends on one.
5. Run relevant unit tests, typecheck, lint and build; at release gates run the core end-to-end demo.
6. Confirm the intended behavior manually or via an end-to-end test. Record exactly what was checked.
7. Update **your own** `docs/changes/<TASK-ID>.md` with changed files, tested commands, observed outcomes, proposed deviations, and merge requirements.
8. Commit code + tests + task note. Provide a handoff summary so the integrator can assess the diff without replaying chat history.

### C. Review/integration

An integrator or review agent checks:

- The new behavior completes a user journey rather than only compiling.
- Contract changes have explicit agreement and do not break other active branches.
- Tests were run and results are described precisely (with failures, not just successes).
- Live sponsor integration is shown, not simulated or claimed from a mock.
- Model conclusions are qualified; physics, compliance, finance and user-impact claims are traceable to inputs/assumptions.
- Secrets, private data and API keys are not committed; dependencies/licenses are permitted.
- Task note contains the exact new behavior, evidence, known limitations and rollback.

**On approval:** Merge, re-run the integrated smoke test, update the approved `PLAN.md` and `docs/DECISIONS.md` as needed, then tag a stable milestone when the defined release gate passes. Only the integration owner modifies canonical architectural status during integration unless delegated.

## 3. Ownership, branch and documentation rules

**One owner, one feature branch, one change note per task.** Branch name: `feat/<TASK-ID>-short-name`, `fix/<TASK-ID>-short-name`, or `docs/<TASK-ID>-short-name`. Use IDs assigned centrally; never invent IDs that may collide across teams.

```
main                            # must remain known-good
├── feat/HK-011-cad-ui           # owns editor view
├── feat/HK-012-simulation       # owns sim engine and tests
└── feat/HK-013-floorplan-import # owns end-to-end importer

docs/changes/HK-011.md          # changes only from that work package
docs/changes/HK-012.md
docs/changes/HK-013.md
```

**Do not concurrently modify a shared `DOCS.md`** from several agents; it creates conflict hotspots. This repo uses independent `docs/changes/<TASK-ID>.md` notes. Each can be created from `templates/docs/changes/TASK_TEMPLATE.md` in the toolkit. If a project insists on a single `DOCS.md`, make it generated/maintained by the integrator after merges, never a multi-branch scratchpad.

**Allowed without extra approval:** Internal implementation details that preserve public contracts, tests, documentation for owned modules, bounded fixes needed for acceptance.  
**Must be proposed first:** Public schemas/APIs, shared data models, routing semantics, dependency framework changes, runtime/deployment architecture, scope expansion, security/auth changes, expensive model changes, ownership changes, and deadline-risking changes.  
**Never without explicit instruction:** Deleting data, replacing another team's work, publishing secrets, claiming formal certification, bypassing license/event rules, rewriting stable release history.

## 4. Handoff format (mandatory)

Use this exact end-of-task response shape:

```text
TASK: <ID> — <title>
STATUS: ready_for_review | blocked | deferred
BRANCH / BASE: <branch> / <tag or sha>
DELIVERED: <observable user-facing change>
CHANGED CONTRACTS: <none | IDs + proposed/approved state>
FILES: <major paths>
VERIFIED: <command → result>, <manual E2E action → observed outcome>
NOT VERIFIED: <missing live checks, assumptions, limitations>
RISKS / ROLLBACK: <what can fail; how to disable or revert>
INTEGRATION NEEDED: <merges, env changes, migrations, owner decisions>
NOTE: docs/changes/<ID>.md
```

A useful task report is short, evidence-heavy and honest. It should not be a transcript of every command.

## 5. Quality gates and hard stops

A task is **not done** merely because an agent says it is done. Minimum gates:

- Acceptance behavior works with representative input and at least one edge case.
- Changed component tests pass; cross-boundary changes have contract/integration coverage.
- No undocumented breaking schema/API changes.
- Build/typecheck/lint results recorded (if tools exist in this stack).
- Changes are recoverable from a stable base and traceable to one task note.
- User-facing claim can be demonstrated under time pressure.

**Stop and escalate** when requirements contradict each other; the task requires access/secrets that are unavailable; a change touches another worker's owned module; a core assumption is invalid; tests repeatedly fail in a way that threatens the baseline; or the work crosses the current feature freeze.

## 6. Project-specific configuration — replace at kickoff

```yaml
repository: [FILL]
project_name: [FILL]
canonical_plan: PLAN.md
accepted_decisions: docs/DECISIONS.md
change_note_dir: docs/changes
stable_branch: main
release_owner: [FILL]
feature_freeze_at: [ISO 8601 local time]
submission_deadline: [ISO 8601 local time]
package_manager: [FILL]
unit_test_command: [FILL]
typecheck_command: [FILL]
lint_command: [FILL]
build_command: [FILL]
integration_test_command: [FILL]
core_demo_steps: [FILL]
```

## 7. Principles to remember

- Optimize for a **demo-ready, end-to-end product**, not number of implemented features.
- Preserve a stable tag before experimenting further.
- Batch logically connected changes; verify **whole workflows** at milestones.
- Treat sponsor technologies as architectural contributors, not decorative checkboxes.
- Prefer short, structured artifacts a future agent can act on over long prose conversation history.
- Keep an honest line between *implemented*, *tested*, *planned* and *hypothetical*.
