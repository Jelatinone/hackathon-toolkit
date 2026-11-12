# Hackathon Toolkit

A project-agnostic workflow library for planning, building, managing, demonstrating, and submitting software hackathon projects. Use it as a **pinned Git submodule inside an existing starter**. The starter supplies the application, stack, Git setup, and deployment; this toolkit supplies reusable procedures and formats.

## Responsibilities and sources of truth

| Resource | Purpose | Owner/location |
| --- | --- | --- |
| [Playbook](HACKATHON_PLAYBOOK.md) | Principles, lessons, human checklists, rubric | Toolkit; stays consolidated |
| [Maintenance instructions](AGENTS.md) | How to change this library | Toolkit maintainers |
| [Project contract](docs/PROJECT_CONTRACT.md) | Reusable project operating policy | Toolkit source; adopted by starter instructions |
| [Formats](docs/FORMATS.md) | Strict skills, plans, reports, checkpoints | Toolkit; versioned |
| [.agents/skills](.agents/skills) | Twelve canonical agent workflows | Toolkit; native starter adapters reference these |
| [PLAN template](templates/PLAN.md) | Structured approved intent, commands, tasks, gates | Instantiate as starter PLAN.md at kickoff |
| [Decision template](templates/docs/DECISIONS.md) | Accepted architecture and rationale | Instantiate as starter docs/DECISIONS.md |
| [Task template](templates/docs/changes/TASK_TEMPLATE.md) | One task's assignment, plan and evidence | Starter docs/changes/allocated-ID.md |

Project instructions and approved PLAN govern the application. Task proposals do not override them. Actual tests establish behavior, not approval. Only the integration owner updates accepted architectural status. Do not maintain a shared multi-agent scratch DOCS.md.

## Adopt in a starter

The starter maintainer initializes its Git repository and adds this repository at `toolkit/` (or another chosen path). Supply the actual repository URL; the toolkit does not initialize Git or generate an app:

```sh
git submodule add https://github.com/Jelatinone/hackathon-toolkit toolkit
```

For an existing starter checkout, initialize its recorded revision:

```sh
git submodule update --init --recursive
```

Run the optional dependency-free utility with Node 20 or later from the starter root:

```sh
node toolkit/scripts/toolkit.mjs bootstrap --project .
node toolkit/scripts/toolkit.mjs bootstrap --project . --write
```

Preview is the default. Both agents are exposed by default; use `--agents codex` or `--agents claude` to select one. Paths containing spaces must be quoted. The script resolves its own toolkit mount; no hardcoded `toolkit/` assumption or symlink is needed.

Bootstrap creates small native entrypoints in `.agents/skills` and `.claude/skills`, a missing project AGENTS stub referencing the shared contract/formats, and a missing CLAUDE stub importing `@AGENTS.md`. It does **not** create PLAN, task notes, application files, Git repositories, submodules, commits, tags, dependencies, or deployments.

Existing files are preserved. Intact generated files can refresh; edited adapters are conflicts. Existing project instructions with the required references/import are retained. Otherwise bootstrap prints proposed snippets, exits nonzero, and writes nothing. Integrate the snippets deliberately into existing instructions, then rerun. Review and commit generated entrypoints with the starter so teammates can use them immediately.

Invoke `kickoff-project` to prepare the project baseline from the existing starter. Fill actual commands and rules, allocate IDs, approve the baseline and checkpoint, then execute assigned work. A template's example IDs and nulls never authorize implementation.

## Invoke workflows

In Codex CLI/IDE use `$skill-name`; in Claude Code use `/skill-name`. Descriptions also support normal skill selection. Native discovery directories differ, so the starter adapters load the canonical submodule files explicitly. [Codex documentation](https://learn.chatgpt.com/docs/build-skills), [Claude Code documentation](https://code.claude.com/docs/en/skills)

The small `CLAUDE.md` import keeps shared policy in AGENTS without relying on symlinks or particular native AGENTS support. [Claude instruction documentation](https://code.claude.com/docs/en/memory#share-one-file-with-other-coding-tools)

| Workflow | Use when | Result boundary |
| --- | --- | --- |
| [review-ideation](.agents/skills/review-ideation/SKILL.md) | Comparing ideas/tracks | Recommendation and first proof; no coding |
| [kickoff-project](.agents/skills/kickoff-project/SKILL.md) | Starting from an existing starter | Proposed project records; no scaffolding |
| [plan-checkpoint](.agents/skills/plan-checkpoint/SKILL.md) | Allocating bounded work | Task plans, dependencies, gates |
| [replan-checkpoint](.agents/skills/replan-checkpoint/SKILL.md) | Capacity, progress or scope changes | Proposed cuts/reassignments; no implicit approval |
| [implement-next-checkpoint](.agents/skills/implement-next-checkpoint/SKILL.md) | Executing approved assigned work | One checkpoint; no automatic integration |
| [test-build](.agents/skills/test-build/SKILL.md) | Testing an identified build | Revision-bound evidence; no source repairs |
| [review-integration](.agents/skills/review-integration/SKILL.md) | Assessing scope/contracts/evidence | Review verdict; no automatic merge |
| [create-stable](.agents/skills/create-stable/SKILL.md) | Promoting a verified revision | Authorized unique tag; separate publication result |
| [prepare-demo](.agents/skills/prepare-demo/SKILL.md) | Preparing or rehearsing judging | Script, proof scenes, honest rehearsal evidence |
| [submission-preflight](.agents/skills/submission-preflight/SKILL.md) | Checking final artifacts | Readiness distinct from confirmed submission |
| [recap-project](.agents/skills/recap-project/SKILL.md) | Orientation/retrospective | Factual state and next action; no silent writes |
| [handoff-task](.agents/skills/handoff-task/SKILL.md) | Finishing/transferring work | Evidence and receiver instructions |

All workflows use fixed metadata/sections from FORMATS, including blocked outcomes. Use the [plan](templates/AGENT_PLAN.md) and [report](templates/WORKFLOW_REPORT.md) templates. Reports normally stay in chat. Formatting alone never establishes truthful evidence or action authorization.

## Manual adoption without Node

1. Keep the toolkit submodule initialized at the starter's recorded revision.
2. Add a project-root AGENTS instruction to read `toolkit/docs/PROJECT_CONTRACT.md` and `toolkit/docs/FORMATS.md`, retaining project-specific rules and explicitly naming the starter as project root. Add `@AGENTS.md` to CLAUDE.md for Claude compatibility.
3. For each desired workflow, create its native `SKILL.md` in `.agents/skills/<name>/` and/or `.claude/skills/<name>/`. Copy only the canonical name/description frontmatter. Add a relative link to the canonical SKILL.md and instruct the agent to read it, retain the host root, and follow its formats. From a root adapter the default relative source is `../../../toolkit/.agents/skills/<name>/SKILL.md`.
4. Treat these manual adapters as user-owned: bootstrap will not overwrite them. Automated adoption validation expects generated adapters; manual setups need manual source/reference review, or explicit replacement with the previewed generated adapters.
5. At kickoff instantiate only project-owned PLAN, empty decisions, and allocated task notes from templates. Do not copy the full playbook or skill bodies.

## Validation and upgrades

```sh
node toolkit/scripts/toolkit.mjs validate --project .
node toolkit/scripts/toolkit.mjs validate-report path/to/report.md
node toolkit/scripts/toolkit.mjs validate-report path/to/plan.md --kind plan
```

Project validation requires initialized native adapters, schema-v2 project records, task notes, and a registered submodule checkout matching the starter index pin. Before kickoff, a missing PLAN is an expected diagnostic. Metadata uses the documented JSON-valued YAML subset; no general YAML dependency is installed. Verdicts and required format sections are checked, but no validator can prove that evidence is real or approval genuine.

If the toolkit is uninitialized, its script cannot run: execute the starter's submodule initialization first. If an adapter is stale, review the pinned upgrade and bootstrap preview. Upgrade deliberately: select/review a toolkit revision, update the starter's submodule pin, inspect format/template changes, refresh adapters, validate, and run the starter's checks. Never use an automatic latest-upstream update during project workflows. Schema-v1 project documents require a reviewed migration, not overwriting. [Git submodule documentation](https://git-scm.com/docs/git-submodule)

From the toolkit repository, maintainers run:

```sh
node --test
node scripts/toolkit.mjs validate
git diff --check
```

Tests use temporary starter fixtures. Native-client discovery and execution are separate acceptance checks; see [behavioral scenarios](tests/SCENARIOS.md). No particular model, framework, sponsor, event, or deployment provider is required. Skills are instructions, not a sandbox or orchestration service.
