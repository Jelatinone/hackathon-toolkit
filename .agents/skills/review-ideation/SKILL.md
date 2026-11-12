---
name: "review-ideation"
description: "Compare hackathon concepts and track fit before committing scope; identify feasibility risks and the first technical proof."
---

# review-ideation

## Purpose and triggers

Use for concept selection or reconsideration, not project implementation.

## Inputs and prerequisites

Required: official rules/judging criteria, team capacity, time window, and candidates or permission to generate them. Discover existing event facts from PLAN if present. Defaults: playbook rubric; no project baseline required.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read official sources, PLAN if present, and playbook section 2. Report only; do not change a baseline or implement a spike.

## Workflow

1. Verify rule sources, code window, and unknown eligibility/AI restrictions before recommending action.
2. Normalize existing or permitted forward/backward candidates using the playbook brief.
3. Apply the existing weighted scorecard, declaring any event-specific changes, uncertainty and veto risks. Scores do not forecast awards.
4. Recommend one candidate, honest core demo, capacity cuts, and the smallest critical-path proof with pass/fail criteria.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Concepts

Structured briefs: user, decision, promise, demo, MVP, differentiator, track role, unknown dependencies, cuts.

### Scorecard

Per-criterion scores, weights, totals, source of weights, and confidence.

### Risks

Vetoes, unknown rules, dependencies, and earliest proof.

### Recommendation

Preferred concept with rationale or conditional recommendation.

### Core demo

Starting state, action, observable result, and reduced-capacity cuts.

### First technical test

Smallest proof, prerequisites, expected result, and stop/cut decision. Describe, do not execute.

## Acceptance criteria

Each candidate is traceable to user value and official criteria; uncertainties remain visible. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Missing rules allow conditional analysis but block claims of eligibility and dependent action. Selecting a recommendation does not approve PLAN or authorize pre-event code. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

