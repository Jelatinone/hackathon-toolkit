# Hackathon Toolkit

A reusable operating system for short software hackathons, distilled from the HackUTD ZeroDay 2026 **Egress** retrospective. This repository separates **lessons**, **agent behavior**, **the project's agreed plan**, and **branch-level implementation evidence**.

## Repository layout

| File | Role | Where it belongs |
| --- | --- | --- |
| [`HACKATHON_PLAYBOOK.md`](HACKATHON_PLAYBOOK.md) | Human-readable retrospective and end-to-end competition workflow | Keep in this toolkit; refer to it before every event |
| [`AGENTS.md`](AGENTS.md) | Reusable rules for coding/review/ideation agents | Copy into the root of each new hackathon project; adapt commands |
| [`templates/PLAN.md`](templates/PLAN.md) | Machine-readable project baseline: goals, contracts, tasks, acceptance gates | Copy to `<project>/PLAN.md` at project kickoff |
| [`templates/docs/changes/TASK_TEMPLATE.md`](templates/docs/changes/TASK_TEMPLATE.md) | One immutable-in-identity handoff file per assigned task/branch | Copy to `<project>/docs/changes/TASK-ID.md` |
| [`templates/docs/DECISIONS.md`](templates/docs/DECISIONS.md) | Consolidated, accepted architectural decisions | Copy to `<project>/docs/DECISIONS.md` |

**Important:** Do **not** maintain one shared, constantly edited `DOCS.md` across every branch. That creates merge conflicts and mixes proposed decisions with accepted ones. The equivalent here is a **standardized task note per branch** (`docs/changes/TASK-ID.md`); an integrator updates `PLAN.md` and `docs/DECISIONS.md` only when a decision is accepted.

## Use this in a new hackathon

1. Before the event, each teammate prepares at least one concept using the idea brief in the Playbook. Review the event rules; ideation may be allowed before coding starts, while implementation may not be.
2. At kickoff, compare candidate ideas against sponsor criteria, judge-facing demos, feasibility and integration risk. Select one **core demonstration**.
3. Copy the three project templates (`AGENTS.md`, `PLAN.md`, `docs/DECISIONS.md`). Fill the project-specific values and mark unresolved assumptions plainly. Assign a release/integration owner.
4. Agree on an API/data contract and initial vertical slice. Create task IDs *centrally*, with one branch and one `docs/changes/TASK-ID.md` per task. Assign one accountable owner per deliverable.
5. Every agent reads `AGENTS.md`, `PLAN.md` and its task note before coding. Agents may recommend changes to the plan but do not silently rewrite shared contracts.
6. Merge only after tests + full-user-flow verification. Tag stable milestones. The integrator incorporates accepted changes into the canonical plan and decisions ledger.
7. Capture demo footage continuously, freeze scope before submission, and submit with a buffer.

## Operating principle

> Build one end-to-end, demonstrably useful product, with sponsor integrations that matter to the workflow. Prefer a stable, legible demonstration over an impressive list of untested features.

The toolkit is deliberately opinionated, but adjustable to each event's duration, rules, team size, and track criteria. The Egress story is a case study—not proof that any specific tactic caused or prevented an award.
