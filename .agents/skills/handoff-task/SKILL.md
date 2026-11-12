---
name: "handoff-task"
description: "Record a truthful task handoff or ownership-transfer package with branch, behavior, evidence, limitations and next steps."
---

# handoff-task

## Purpose and triggers

Use to finish or transfer an assigned task; do not infer reassignment or integration approval.

## Inputs and prerequisites

Required: allocated task ID, note, branch/base and current changes. Discover tests, environment prerequisites, outstanding work and receiver if assigned. Default: update owned note only.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read task note, PLAN, DECISIONS and actual diff/evidence. Update the assigned note; reviewer/integration fields only with delegated ownership.

## Workflow

1. Inspect current task branch/base and diff; reconcile claimed behavior and tests with actual state.
2. Record unfinished work, current environment, dependencies, recovery and receiver prerequisites.
3. Update owned note and identify explicit reassignment approval if transfer is requested; do not discard another worker's edits.
4. Emit the handoff inside the common report; use ready_for_review only when required task acceptance passes.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### TASK

Allocated ID and outcome title.

### STATUS

ready_for_review, blocked, or deferred with reason.

### BRANCH

Actual branch and base revision.

### DELIVERED

Observable behavior.

### CONTRACTS

None or IDs and proposed/approved state.

### FILES

Major changed paths.

### VERIFIED

Actual commands/actions, subject and outcomes.

### NOT VERIFIED

Missing checks and limits.

### RISKS

Failure modes and rollback.

### INTEGRATION

Merge requirements, env changes, owner decisions and receiver next step.

### NOTE

Project-relative task note path.

## Acceptance criteria

Handoff is evidence-heavy and sufficient without chat history; unknown tests/ownership stay explicit. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Missing acceptance blocks ready_for_review. Ownership transfer needs designated-owner approval; existing authorization is reused. Handoff does not authorize merge/release. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

