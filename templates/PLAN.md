# Project canonical baseline

Create in the starter at kickoff, never in the toolkit. Fill nulls from evidence; the example IDs are not allocations. Approved intent and contracts live here; branch evidence lives in task notes. Remove unused examples. Configuration is authoritative here only.

```yaml
schema_version: 2
project_name: null
event_name: null
project_status: "ideation"
plan_version: 0
approval: "proposed"
approval_ref: null
updated_at: null
timezone: null
code_start: null
code_end: null
feature_freeze: null
submission_deadline: null
release_owner: null
stable_branch: null
base_release: null
current_stable_release: null
```

## 1. Product contract

```yaml
primary_user: null
user_problem: null
user_decision_improved: null
one_sentence_promise: null
core_demo: null
demo_30_seconds: null
demo_3_minutes: null
claim_boundaries: null
```

Features support the core demonstration, meaningful track requirements, or explicitly approved stretch work. Separate implemented and hypothetical claims.

## 2. Event requirements and proofs

| Requirement ID | Official source and exact clause | Verified at | Constraint/proof | Owner | State | Evidence/limitation |
| --- | --- | --- | --- | --- | --- | --- |
| RULE-001 | Unresolved | null | Eligibility, AI/pre-existing code, license, judging, artifact and access rules | Unassigned | planned | Unverified |

| Track ID | Exact prompt clause/source | Essential technology/capability | Proof scene | Current state | Gap/limitation |
| --- | --- | --- | --- | --- | --- |
| SP-001 | Unresolved | Unresolved | Unresolved | planned | Unverified |

States: planned, in_progress, tested, demonstrated, deferred. Demonstrated needs real evidence. Use None with a reason when no sponsor track applies. Official dates appear only in header metadata and include offsets.

## 3. Scope tiers and release gates

| ID | Tier | Outcome | Dependencies | Measurable acceptance | Owner | State |
| --- | --- | --- | --- | --- | --- | --- |
| F-001 | CORE | Smallest complete user journey | None | Unresolved | Unassigned | planned |

Replace these examples with project-specific gates; stable promotion must name the exact gate and evidence:

- STABLE-V0: starter runs, contracts declared, test harness runs.
- STABLE-V1: core demo reproducible end-to-end.
- STABLE-V2: required differentiators and live integrations proven.
- RC-1: feature freeze, no demo-blocking bugs, footage captured.
- FINAL: release, video, submission artifacts and links verified.

## 4. System architecture

Describe the actual starter's modules, boundaries, and data flow. Do not impose a web architecture on another kind of application.

| Module/owner | Responsibility | Inputs/outputs | Public contract ID | Mock/live compatibility |
| --- | --- | --- | --- | --- |
| Unassigned | Unresolved | Unresolved | CT-001 | Unverified |

### CT-001

```yaml
version: 1
owner: null
consumers: []
input_schema: null
output_schema: null
errors: null
concurrency_semantics: null
tests: null
```

Propose deviations in task notes. Synchronize approved decisions and contracts before dependent implementation; coordinate consumers.

## 5. Work packages and checkpoints

| Task ID | Checkpoint ID | Branch | Owner | Owned paths | Dependency IDs | Acceptance / test | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HK-001 | CP-001 | feat/HK-001-foundation | Unassigned | Unresolved | None | Unresolved | planned |

IDs are centrally allocated. One owner, branch, isolated working directory, and note per task. The integration owner records reassignments after inspecting outstanding work. Coordinate shared runtime resources. Checkpoint order below is execution order; task_ids order breaks ties among eligible tasks.

### CP-001

```yaml
id: "CP-001"
objective: null
task_ids: ["HK-001"]
depends_on: []
owner: null
approval: "proposed"
approval_ref: null
status: "planned"
acceptance_gate: null
cut_fallback: null
evidence_ref: null
```

Approval: proposed, approved, rejected. Status: planned, in_progress, blocked, ready_for_review, complete, deferred. Complete requires approved integration and gate evidence. Ready-for-review implementation alone is insufficient.

## 6. Technical verification and deployment

```yaml
runtime_version: null
package_manager: null
install: null
unit_tests: null
typecheck: null
lint: null
build: null
integration_e2e: null
run_demo: null
external_services: []
secrets_location: null
test_environment: null
```

Discover commands from the starter. Use null plus a reason below for genuinely inapplicable checks; do not invent commands. Never store secrets here.

**Canonical demonstration:** starting condition → user action → observable result → differentiator → measured result and limitations.

**Release/rollback:** exact hosting target, known-good environment, revision/artifact, restore steps, and owner approval.

## 7. Known risks, unknowns and cuts

| Risk ID | Probability/impact | Earliest proof | Owner | Fallback/cut trigger |
| --- | --- | --- | --- | --- |
| R-001 | Unresolved | Test and deadline | Unassigned | Unresolved |

**Cut order:** unresolved. Replan when capacity changes. After freeze, only owner-approved critical fixes with rollback and renewed evidence.

## 8. Demo, video and submission

```yaml
presenter: null
video_owner: null
submission_owner: null
script_frozen_at: null
video_rough_cut_at: null
upload_start_at: null
```

| Scene ID | Claim to prove | Screen action | Recording owner | Footage path | Status |
| --- | --- | --- | --- | --- | --- |
| VID-001 | Unresolved | Unresolved | Unassigned | None | planned |

| Artifact | Requirement ID | Revision/version | Location | Access/playback check | Evidence |
| --- | --- | --- | --- | --- | --- |
| Submission | RULE-001 | None | None | not_run | Not submitted |

**Submission receipt:** record platform confirmation ID/location and timestamp after observing it. A draft is not submitted. Refer to header deadlines; do not repeat them here.

## 9. Approved updates and gate log

| Plan version | Date | Release | Accepted task IDs / ADR IDs | Updated by | Approval/evidence | Why |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | null | None | None | Unassigned | None | Proposed kickoff |

Only the authorized integration owner updates canonical status. Record significant accepted architecture decisions in DECISIONS; Git retains history. Do not paste agent transcripts.
