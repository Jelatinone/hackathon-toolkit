---
name: "plan-checkpoint"
description: "Decompose an approved checkpoint objective into bounded owned tasks, dependencies, and acceptance gates."
---

# plan-checkpoint

## Purpose and triggers

Use when a checkpoint needs assignable work; do not implement tasks.

## Inputs and prerequisites

Required: approved objective/baseline, capacity, checkpoint owner and centrally allocated IDs. Discover consumers, existing tasks, contracts and commands. Default: proposed task allocation.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN, DECISIONS, relevant notes and playbook sections 3–4. Write assigned task notes; only the authorized canonical owner may update PLAN.

## Workflow

1. Resolve the objective and approved baseline; inspect existing ID allocations and ownership across known active work.
2. Break the outcome into coherent vertical tasks with owned paths, dependencies, branch/base, representative and edge-case acceptance.
3. Check dependency cycles, shared resources and capacity; define cut/fallback triggers.
4. Prepare strict plans and task notes using the template. Record proposed allocation and seek only missing approval; do not promote proposed work automatically.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Checkpoint contract

Objective, scope, baseline, owner, approval reference or pending decision; embed the seven H4 plan sections here.

### Task allocation

Table: Task ID, Owner, Branch/base, Owned paths, Acceptance, Cut/fallback.

### Dependency order

Ordered IDs, required base availability and resource coordination.

### Acceptance gate

Whole-checkpoint observed behavior, checks, integration evidence and completion conditions.

## Acceptance criteria

Task IDs are allocated, paths/accountabilities explicit, dependencies acyclic, and gates observable. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Missing IDs or ownership prevent creating ambiguous task notes. Proposed contracts require approval before dependent implementation; retain existing authorization. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

