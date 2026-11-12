---
name: "recap-project"
description: "Summarize current project intent, actual implementation, evidence and next eligible work for orientation, handoff or retrospective."
---

# recap-project

## Purpose and triggers

Use to recover context or recap an event without silently changing the project.

## Inputs and prerequisites

Required: target project and available records. Discover PLAN, DECISIONS, notes, repository state and evidence. Default: read-only factual recap; missing records are reported.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read canonical records, relevant code/history and playbook section 11 for retrospectives. No writes by default, including no memory updates.

## Workflow

1. Reconcile approved intent with repository state and actual evidence; mark stale or unavailable facts.
2. Separate delivered/verified work from implemented-but-unverified, proposed and deferred work.
3. Surface decision conflicts, blockers, ownership gaps and remaining gates.
4. Identify the next eligible action using checkpoint approval/dependencies and actual capacity; do not execute it.
5. For retrospectives, separate observations, proposed explanations and actionable lessons; do not infer award causation.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Project state

Baseline, current branch/revision, checkpoint and event phase.

### Delivered and verified

Observed behavior and matching evidence; distinguish unverified implementation.

### Pending work

Proposed, blocked, deferred and remaining gate work.

### Decisions and blockers

Accepted versus pending decisions, ownership/access constraints.

### Next action

One eligible action, responsible owner and prerequisites.

### Lessons

Observed facts, hypotheses, proposed improvements and next validation; None outside retrospective.

## Acceptance criteria

Claims link to actual sources and unknowns; next action respects approval and dependencies. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Missing records produce an incomplete recap, never reconstructed approval. No PLAN rewrite, task execution or memory persistence follows automatically. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

