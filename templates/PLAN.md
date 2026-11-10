# PLAN.md — Project Canonical Baseline

> Copy to the root of a new hackathon project at kickoff. `PLAN.md` records **approved intent** and contracts, not stream-of-consciousness implementation activity. Branch-local details go in `docs/changes/<TASK-ID>.md`. The integrator updates this file at stable gates and when changes are explicitly approved.

```yaml
schema_version: 1
project_name: [FILL]
event_name: [FILL]
project_status: ideation  # ideation | build | feature_freeze | submission | complete
plan_version: 0
updated_at: [ISO 8601]
code_start: [ISO 8601]
feature_freeze: [ISO 8601]
submission_deadline: [ISO 8601]
release_owner: [FILL]
base_release: [initial sha or tag]
current_stable_release: [sha or tag]
```

## 1. Product contract

```yaml
primary_user: [FILL]
user_problem: [FILL]
user_decision_improved: [FILL]
one_sentence_promise: [FILL]
core_demo: [start state -> action -> measured/observed result]
30_second_demo: [FILL]
3_minute_demo: [FILL]
claim_boundaries: [what must never be claimed]
```

**Do not add features just because they sound impressive.** All features must support the core demo, satisfy a meaningful sponsor requirement, or be explicitly authorized stretch work.

## 2. Sponsor requirements and proofs

| Track ID | Exact prompt clause/source | Essential technology/capability | Proof scene | Current state | Gap/limitation |
| --- | --- | --- | --- | --- | --- |
| SP-01 | [FILL] | [FILL] | [FILL] | planned | [FILL] |

States: `planned` / `in_progress` / `tested` / `demonstrated` / `deferred`. `demonstrated` requires actual evidence, not only working mocked data.

## 3. Scope tiers and release gates

| ID | Tier | Outcome | Dependencies | Measurable acceptance | Owner | State |
| --- | --- | --- | --- | --- | --- | --- |
| F-001 | CORE | [Smallest full user journey] | none | [E2E step/result] | [FILL] | planned |
| F-002 | COMPETITIVE | [Primary technical differentiator] | F-001 | [Observed proof] | [FILL] | planned |
| F-003 | STRETCH | [Cuttable enhancement] | F-002 | [Observed proof] | [FILL] | deferred |

**Release gates** (replace examples with project-specific facts):

- `STABLE-V0`: skeleton starts, contracts declared, test harness runs.
- `STABLE-V1`: complete core demo works end-to-end and is reproducible.
- `STABLE-V2`: sponsor differentiators proven; live integration and demo tested.
- `RC-1`: feature freeze, no known demo-blocking bugs, video footage captured.
- `FINAL`: deployment, video, Devpost and submission links verified.

## 4. System architecture (approved)

```text
[User/UI] -> [Client boundary/API] -> [Backend/model] -> [Persistence/service]
                                        |-> [Async runner/AI, if any]
```

| Module/owner | Responsibility | Inputs/outputs | Public contract ID | Backend/mock compatibility |
| --- | --- | --- | --- | --- |
| [FILL] | [FILL] | [FILL] | CT-001 | [FILL] |

**Critical contracts** (keep concise, explicit and versioned):

### CT-001 — [Interface name]

```yaml
version: 1
owner: [FILL]
consumers: [[FILL]]
input_schema: [file/type reference]
output_schema: [file/type reference]
errors: [expected failure modes]
concurrency_semantics: [ordering/replay/idempotency/none]
tests: [path or command]
```

If a contract changes, create a proposed deviation in the task note. Change this section only after approval and coordinate every consumer.

## 5. Work packages and parallel lanes

| Task ID | Branch | Owner | Owned paths | Dependency IDs | Acceptance / test | Status |
| --- | --- | --- | --- | --- | --- | --- |
| HK-001 | feat/HK-001-foundation | [FILL] | [FILL] | none | [FILL] | planned |

Rules: Assign IDs centrally. One owner, one branch, one `docs/changes/<TASK-ID>.md`. Don't assign multiple agents overlapping ownership unless integration owner coordinates it. An owner who goes unavailable must explicitly hand off unfinished work and environment requirements.

## 6. Technical verification and deployment

```yaml
runtime_version: [FILL]
package_manager: [FILL]
install: [FILL]
unit_tests: [FILL]
typecheck: [FILL]
lint: [FILL]
build: [FILL]
integration_e2e: [FILL]
run_demo: [FILL]
external_services: [[FILL]]
secrets_location: .env  # gitignored, never committed
```

**Canonical E2E demonstration:**

1. [Starting condition]
2. [User action]
3. [Observable data/result]
4. [Second action demonstrating differentiator]
5. [Measured result; limitations]

**Release/rollback:** [FILL with tag, hosting target, known-good environment and steps].

## 7. Known risks, unknowns and cuts

| Risk ID | Probability/impact | Earliest proof | Owner | Fallback/cut trigger |
| --- | --- | --- | --- | --- |
| R-001 | [FILL] | [test + deadline] | [FILL] | [FILL] |

Cut order (lowest user/track value first): `[FILL]`. If team capacity drops, re-scope immediately. No agent should expand the roadmap without approval.

## 8. Demo, video and submission

```yaml
presenter: [FILL]
video_owner: [FILL]
submission_owner: [FILL]
script_frozen_at: [ISO 8601]
video_rough_cut_at: [ISO 8601]
feature_freeze_at: [ISO 8601]
upload_start_at: [ISO 8601]
submission_deadline: [ISO 8601]
```

| Scene ID | Claim to prove | Screen action | Recording owner | Footage path | Status |
| --- | --- | --- | --- | --- | --- |
| VID-01 | [FILL] | [FILL] | [FILL] | [FILL] | planned |

## 9. Approved updates / gate log

| Plan version | Date | Release | Accepted task IDs / ADR IDs | Updated by | Why |
| --- | --- | --- | --- | --- | --- |
| 0 | [FILL] | initial | none | [FILL] | Initial approved baseline |

**Canonical update rule:** The release/integration owner updates this after accepting branch notes, and records substantial architecture decisions in `docs/DECISIONS.md`. The history remains in git; do not paste full agent conversations here.
