# Hackathon Playbook — Reusable Competition Guide

**Document status:** Reusable baseline v1.2
**Audience:** Participants, team leads, idea-evaluation agents, implementation agents, and reviewers  
**Primary goal:** Deliver a reliable, demonstrable project under a strict deadline while targeting relevant awards without compromising the product.

## 0. How to use this guide

This is an operating guide, not a retrospective of one event or a particular team's project. It collects reusable practices drawn from common short-deadline project risks and makes them actionable. Distinguish three kinds of guidance:

- **Common failure modes:** Missed handoffs, unreliable integrations, overextended scope, rushed judging, and last-minute submission failures are risks to plan for.
- **Recommended safeguards:** Early scope gates, written interface contracts, branch-local change notes, stable releases, and dedicated presentation time can reduce those risks.
- **Working hypotheses:** The suggested idea-scoring weights, time allocations, and presentation structures are starting points—not verified predictors of awards.

Adapt these practices to the event's rules, format, duration, judging criteria, team size, and permitted tools. Check rules before coding or using AI. Do not infer why an entry won or lost solely from marketing materials or informal judge comments.

Use this guide from the pinned toolkit submodule in an existing starter. The starter owns application setup and Git; the toolkit supplies [workflows and adoption instructions](README.md). Project instructions adopt the [shared contract](docs/PROJECT_CONTRACT.md), and agents use the [strict formats](docs/FORMATS.md). Canonical project documents live outside the toolkit.

## 1. Core lessons

1. **Start with a user and a decision.** A project is stronger when someone can immediately see which meaningful outcome it enables.
2. **Ideate forward and backward.** Compare concepts rooted in real problems with concepts that naturally fulfill the exact requirements of target awards.
3. **Choose a defining demonstration early.** Build the smallest honest, complete user journey before expanding scope.
4. **Make sponsor integrations essential or meaningfully useful.** Show their actual role rather than treating them as checkboxes.
5. **Staff for reliable execution.** Assign work to people who can deliver it, communicate blockers, and be present for integration.
6. **Parallelize behind explicit contracts.** Share a stable baseline and keep one branch-local implementation note per task.
7. **Batch coherent agent work and verify whole behaviors.** Group related implementation and tests without letting agents rewrite unrelated systems.
8. **Preserve a demonstrable release.** New work should not endanger the known-good version close to submission.
9. **Present evidence, not aspirations.** Separate what is implemented and tested from what is possible or planned.
10. **Treat judging and submission as deliverables.** Plan short and long demos, record footage early, and reserve upload time.

## 2. The idea-selection process

### Two complementary approaches

1. **Forward ideation:** Start from a meaningful user problem, envision the solution, then find compatible sponsor tracks.
2. **Backward ideation:** Start with target awards and their exact criteria; define the demonstration and indispensable technical capability; work backward to a real problem that naturally requires them.

**Use both directions.** A promising idea should survive scrutiny as a real product **and** as an achievable, persuasive competition entry. Do not bolt on an unrelated AI chat box or database just to check a sponsor requirement.

### Pre-event idea brief — everyone brings at least one

Each teammate prepares this before the event, subject to event rules:

```text
Idea ID:
User / buyer / beneficiary:
Specific problem or decision improved:
One-sentence product promise:
30-second defining demonstration:
Core MVP (smallest honest end-to-end proof):
Potential sponsor fit (quote criteria, not just brand names):
Required technologies / dependencies:
Biggest unknown and how to test it quickly:
What could be cut without destroying the core demo:
```

Pre-event ideation, technical research and familiarity with SDKs are often valuable. **Never assume pre-event project coding is permitted**; check the specific hackathon rules.

### Scorecard (suggested weights, not objective truth)

Score each criterion from 1 to 5, then compute `sum(score / 5 × weight)`.

| Criterion | Weight | Question |
| --- | ---: | --- |
| Problem clarity and user impact | 20 | Can a judge understand *why it matters* almost immediately? |
| Demonstration / wow moment | 20 | Can the defining result be shown, not merely described? |
| Feasibility under deadline | 20 | Can the entire critical path be implemented, tested and recorded? |
| Technical distinction | 15 | Is the core engineering substantive and explainable? |
| Natural fit to target tracks | 15 | Does each chosen integration materially enable a central capability? |
| Design and narrative potential | 10 | Can the workflow be cohesive, legible and polished? |

**Veto conditions:** A required external service cannot be verified; the central demo relies on multiple unproven integrations; safety/compliance claims cannot be supported; teammates cannot cover the essential work; or the implementation would violate event rules.

### Sponsor-fit matrix

For each target track, capture:

| Field | Description |
| --- | --- |
| Exact challenge wording | Preserve every important clause, not just a theme |
| Product requirement | What in the product addresses that clause? |
| Technology's indispensable contribution | What breaks or materially worsens if the technology is removed? |
| Demonstrable proof | What exact screen/action/metric shows it working? |
| Reviewer question | What is the likely hard question, and what evidence answers it? |
| Unimplemented gap | What will be **explicitly** described as future work? |

Rate sponsor integrations **essential**, **meaningful**, or **decorative**. A decorative integration is a warning sign. If a track is strategically important, make its contribution visible in a testable scene.

### Start with one decision-oriented core demo

Don't only ask, “What can we build?” Ask, “What decision can someone make after using this?” A strong demonstration often follows **start with a real task → complete an observable action → show a useful result → compare or improve it**. Keep ambitious future applications separate from the tested core.

### Separate three levels of scope

- **Core MVP:** The simplest complete, truthful user journey. Ugly is acceptable; nonfunctional integration is not.
- **Competitive differentiator:** The smallest additional feature that makes the project distinct, sponsor-relevant and compelling in a demo.
- **Stretch:** Additional scenarios, models, visuals and conveniences; add only after release gates are met.

Estimate engineering uncertainty, not just surface feature count. A seemingly small interactive control may require much more underlying modeling than a new view. Cut features that cannot be made credible in time. A deterministic approximation is acceptable if assumptions and limitations are stated and its results are never sold as certified facts.

## 3. Team selection and responsibility

**Favor reliable builders.** In software-heavy tracks, prioritize developers who can independently complete and debug meaningful features. Full-stack capability across the team reduces handoff bottlenecks. Complementary design/game/3D skills help *when directly relevant*, but are not a substitute for critical implementation capacity.

**Before committing, verify:** availability, willingness to use/learn the team's tools, ability to ship a bounded feature, communication habits, and willingness to accept scope cuts. Do not assign critical-path tasks to someone known to be unavailable during the integration window.

**Suggested ownership for four developers:**

| Owner | Accountable for | Backup role |
| --- | --- | --- |
| Frontend lead | One coherent UI system and user experience | Supports other vertical features |
| Backend/platform lead | Core APIs, persistence, deploy and infrastructure | Assists integration |
| Differentiator lead | Main algorithm, AI or simulation | Designs test harnesses |
| Feature/integration lead | Full vertical features and cross-system tests | Demo/submission operations |

These are **accountabilities**, not permanent code silos. After the platform contract is established, assign vertical features end-to-end, so a feature owner delivers the working behavior rather than an unconnected component.

**Minimum team contract:** One owner and one acceptance test per task; scheduled review check-ins; short blocker reporting; backup owner; clear work window; release captain who decides what merges. If real capacity falls, **replan immediately** instead of preserving an obsolete roadmap. Keep video, submission page and submission ownership explicit rather than automatically assigning them to the primary programmer.

## 4. Architecture and agentic parallelization

### Agree on the integration contract first

At kickoff, inspect the existing starter and create its `PLAN.md` (template provided). Define the domain model, API/function contracts, responsibilities, data flow, external resources, environment setup, critical user journey and actual verification commands. Assign unique task IDs and branches from a common known-good base. Define approved checkpoints with dependencies, acceptance gates and cuts; do not regenerate the starter application.

**One code path to the shared system.** Where possible, build adapters/mock implementations so frontend work can render real-shaped data while backend services mature. This enables parallel progress without guessing interface shapes.

### The documentation protocol

- `PLAN.md` = **canonical, approved** scope, contracts, priorities, tasks, release gates. Updated by the integration owner at planned checkpoints; not casually rewritten on every branch.
- `AGENTS.md` = how people and agents operate; test, branching, security and documentation rules.
- `docs/changes/TASK-ID.md` = **one per task/branch**, describing actual changes, tests, departures from plan and required integration decisions. Each feature branch edits its own file. This replaces the proposed shared `DOCS.md` to avoid merge conflicts.
- `docs/DECISIONS.md` = accepted architectural deviations in an append-only record maintained during integration. Proposed deviations remain in the task note until reviewed.

A branch should carry its code **and** its task note, so a reviewer can understand what changed without replaying a long agent transcript.

### Batch related work; verify at useful boundaries

Coding agents can be effective when given coherent batches of related implementation and tests, reviewed holistically rather than through dozens of isolated edits. Preserve that benefit with guardrails:

1. Give the agent a **single bounded outcome** with affected contracts and acceptance tests.
2. Permit implementation + local refactoring + associated tests within that boundary.
3. Request an explicit verification summary and the new task-note entry.
4. Review the result as a **whole vertical behavior**, not just code diff snippets.
5. Integrate only after passing tests plus a complete user-flow smoke test.

Do not launch overlapping agents against the same modules without a clear ownership contract. Parallelism is useful only when merge/integration overhead stays smaller than the time saved.

Use separate worktrees/clones for simultaneous workers and coordinate shared test services, ports and data. If an owner becomes unavailable, the integration owner may record a reassignment after inspecting outstanding work. An unmerged dependency is not an approved baseline; stop dependent execution rather than silently merging it.

### Branches, releases and recovery

- The stable branch is configured in PLAN (`main` is a common example). No direct unverified changes or force-pushes.
- Branch by task (example `feat/HK-014-import-flow`). Rebase/merge from an agreed base as required by team rules.
- Commit changes with tests and the task note together.
- Run unit/type/lint checks appropriate to the change; run a full build, integration tests and core end-to-end demonstration before merging.
- Establish stable tags (e.g. `STABLE-V1`) at **verified user journeys**, not just completed subsystems.
- Preserve a known-good demo environment and a documented rollback path.
- Use a **feature cutoff**. Unready work stays on its branch and must not jeopardize submission.

Bind checks to the tested revision/artifact and environment. A review verdict does not authorize merge or promotion; recheck the integrated result. After freeze, the release owner can approve bounded critical fixes with rollback and renewed evidence. Implementation finishes ready for review; checkpoint completion requires its integrated acceptance gate.

**Continuity lesson:** An initial frontend/backend split may accelerate development, but it should not become a permanent dependency on specific individuals. If a contributor stops delivering, use stable tags, documented interfaces, task notes and a capacity-aware replan to keep the central demonstration viable.

## 5. Design and product quality

- Define the user, their starting state, the action they take and the decision/result they obtain.
- Plan the full UI journey before filling pages with features. Think about layout hierarchy, spacing, information density, feedback states and transitions.
- App screens produced rapidly with AI still require intentional visual direction; generated appearance alone is not a design system.
- Keep one frontend owner accountable for cohesion while feature developers implement agreed components.
- Prefer features that complete the **actual user journey**, even when they seem mundane. Import, save, onboarding, error feedback and export flows can be more valuable than an additional advanced feature.
- Never overclaim model validity: simulations, estimates and metrics depend on inputs, assumptions and validation. Regulatory checks require explicit, versioned rules and traceable calculations, not unsupported claims of certification.

## 6. Judging and award targeting

**One universal working demonstration; several sponsor emphases.** Show the same tested end-to-end user journey to every judge, then adapt the technical evidence and practical impact to each audience. Avoid switching to an untested workflow under pressure.

Prepare **three time budgets** for the same story:

| Time | Content |
| --- | --- |
| ~30 seconds | Problem + dramatic result + sponsor's visible contribution |
| ~3 minutes | End-to-end user journey, proof of technical distinction, measurable outcome, why it matters |
| Full slot | More architecture, design rationale, assumptions, multiple scenarios and Q&A |

For each sponsor, prepare one **proof scene**. For an AI track, show real tool use and verified outcomes rather than merely labeling a feature “AI.” For a real-time systems track, show clients synchronizing and correctly explain where computation occurs. For an industry track, show a concrete business or user decision and evidence for the claimed value. Qualify safety, compliance and financial claims.

**Never assume every judge will visit.** A complete submission page, readable architecture summary, 1–2 minute demo video and a self-explanatory live link should make sense without your spoken walkthrough. Test the live link from a fresh device/session.

Log judge questions separately from verdicts. Questions about missing features, standards, deployment or business impact may reveal useful product gaps, but they do not prove why an award was won or lost. Convert them into testable follow-up priorities rather than speculative conclusions.

## 7. Video and submission: start early

The final video is a deliverable with dependencies and failure modes, not leftover work after coding. A last-minute recording block is fragile: audio, screen recording, missing footage, export settings and uploads can consume it.

**Workflow:**

1. Draft a short, fixed script early. Identify **one primary result** and a maximum of three technical differentiators.
2. Create a shot list tied to every spoken claim. Use placeholder captures if a feature isn't ready.
3. Capture stable footage as soon as each feature becomes demonstrable. Keep raw clips named by scene and store backups.
4. Test mic, camera, screen capture, permissions, disk space, codecs, audio synchronization and export before the final hours. Prioritize clear sound over elaborate face-camera shots.
5. Use face-camera only where it strengthens the story; separately recorded narration and screen demo are a reliable fallback.
6. Assemble a rough cut before the final feature freeze. Replace clips; don't rebuild the narrative for every added feature.
7. Leave time for export, playback on another device, upload, links, forms and submission confirmation.

A 90–120-second baseline can allocate ~10–15 seconds to hook/problem, ~50–60 seconds to the working demonstration, ~20–30 seconds to technical differentiation and the rest to impact/closing. The event's actual rules override these defaults.

## 8. Time management: default allocation for a 24-hour build window

Adjust the schedule to the event's official clock, team availability and judging deadlines. The goal is **gates and buffers**, not rigidly filling hourly quotas.

| Window | Outcome/gate | Non-coding work happening in parallel |
| --- | --- | --- |
| 0–1 h | Review tracks; compare prepared concepts | Confirm attendance/availability; appoint owners |
| 1–2 h | Choose concept, core demo and scope tiers | Create script skeleton and sponsor-fit matrix |
| 2–3 h | Freeze contracts, repo/tool setup, major risk proof | Agree on Git/agent protocol and task IDs |
| 3–8 h | First end-to-end vertical slice | Capture initial demo clips; prep test fixtures |
| 8–14 h | Stable core MVP tag; validate essential integration | Rough video timeline; draft submission page |
| 14–18 h | Competitive differentiators; one real proof per track | Capture polished feature clips |
| 18–20 h | Feature freeze; full E2E, reliability and UX fixes | Record narration/talking head and rough final edit |
| 20–22 h | Release candidate; rollback only for critical bugs | Final video/export and submission page review |
| 22–24 h | Submission verification and contingency buffer | Upload/submit **before** the actual deadline |

This schedule is a **proposed template**, not a universal timetable. If the official clock differs, the team sleeps, or travel and venue logistics are significant, recalculate. Record absolute local submission deadlines and reserve a larger buffer if uploads or external platforms are unreliable.

**Escalation at every checkpoint:** Is the core demo working? Are contracts still accurate? What is at risk? Does any owner need help? What is cut if capacity drops 25%, 50% or 75%? Who owns the video and submission today?

## 9. Stop conditions and priority rules

Cut or defer a feature when any of these are true:

- It cannot be made trustworthy by the feature cutoff.
- It requires major architectural changes after contracts are frozen without demonstrable payoff.
- It threatens the stable primary demonstration.
- Its sponsor integration is ornamental rather than testably useful.
- The implementation cannot be validated and explained in the judging slot.
- It relies on an unavailable teammate, secret, external service, or long-running job.

**Priority order near deadline:** Preserve running demo → fix critical defects → verify sponsor proof → make video/submission page complete → polish UX → add new features only if risk is negligible.

## 10. End-of-event checklist

- [ ] A fresh clone can run by following documented commands (or a deployed URL works independently).
- [ ] The agreed core user journey works end-to-end without manual repair mid-demo.
- [ ] Sponsor integrations are demonstrably real and properly described.
- [ ] Release tag points to the version shown in the video.
- [ ] No keys, secrets, private tokens or personal data are committed or shown.
- [ ] Video has intelligible audio, accurate claims, working link and verified playback.
- [ ] submission page reflects shipped features separately from planned features, includes track-specific proof.
- [ ] Team has screenshots, architecture diagram, runbook, and emergency fallback.
- [ ] Submission confirmed before deadline with sufficient buffer.
- [ ] Judges' questions, failures, time sinks and surprising successes are recorded for the next retrospective.

## 11. After-event review and continuous improvement

Capture facts while the event is still fresh. Use those facts to improve the toolkit—not to build a permanent diary of one project.

1. Record the chosen idea, alternatives considered, original scope, delivered functionality and significant scope changes.
2. Record actual timing: first runnable demo, integration milestones, feature freeze, video completion and submission confirmation.
3. Identify missed commitments, unclear interfaces and ownership gaps. Raw commit counts alone do not measure individual effort.
4. Document what judges actually saw, the questions they asked and which award requirements were demonstrably satisfied. Separate firsthand observations from guesses.
5. List the largest avoidable time sinks, practices worth repeating and assumptions that still need testing.
6. For each lesson, propose a concrete change: update a checklist, refine a contract, adjust an integration gate or remove unnecessary overhead.

**Study winners critically:** Compare the clarity of their one-sentence promise, working demonstration, meaningful sponsor integration, technical depth and scope discipline using official results and submissions. Do not infer precise judging criteria or causal explanations from appearances alone.

**Output format:** Observed facts → proposed explanations → actionable toolkit updates → what to validate at the next event. Keep event-specific notes separate from this reusable playbook.
