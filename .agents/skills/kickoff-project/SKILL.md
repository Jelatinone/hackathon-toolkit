---
name: "kickoff-project"
description: "Establish project planning records in an existing starter with an initialized toolkit; do not scaffold an application."
---

# kickoff-project

## Purpose and triggers

Use at kickoff, not to regenerate an existing starter or silently replace its baseline.

## Inputs and prerequisites

Required: target starter, selected concept, event constraints, accountable owners, and authorization to create planning records. Discover manifests, commands, architecture and toolkit pin. Defaults: proposed baseline and proposed checkpoints.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read starter configuration, official rules, playbook sections 2–4 and 8, and toolkit templates. Create missing project PLAN and DECISIONS only when requested. Preserve existing instructions, application files and Git configuration.

## Workflow

1. Inspect the existing starter and instructions; confirm project and toolkit roots. Do not initialize Git, install dependencies, or scaffold an app.
2. Discover actual commands, modules and test environments; record unknowns instead of inventing a stack.
3. Prepare product promise, contracts, event sources/clock, owners, scope tiers, first risk proof and checkpoint gates.
4. Populate missing PLAN/DECISIONS from templates within authorization. Leave checkpoints proposed; use only allocated IDs. If IDs are unavailable, propose allocation rather than create task notes.
5. Present unresolved decisions and identify who approves the baseline.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Baseline

Proposed product, architecture, event constraints, and file creation/preservation results.

### Owners

Accountable roles, capacity and unresolved assignments.

### Commands

Discovered commands and their sources; distinguish inspected from executed.

### Checkpoints

Proposed ordered goals, dependencies, acceptance and cuts; embed the seven H4 plan sections here.

### Unresolved decisions

Approvals, missing facts, rules and access needed before execution.

## Acceptance criteria

The baseline describes the existing starter, is marked proposed, and stores canonical values once. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Do not overwrite an existing PLAN or allocate colliding task IDs. Missing rules/access remain blockers. Only explicit owner approval promotes baseline or checkpoints. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

