---
name: "implement-next-checkpoint"
description: "Implement assigned eligible work within exactly one approved checkpoint, verify it, and hand off without automatic integration."
---

# implement-next-checkpoint

## Purpose and triggers

Use for requested checkpoint execution, not indefinite roadmap execution or automatic task claiming.

## Inputs and prerequisites

Required: approved PLAN/checkpoint, explicit assignment, owned paths, approved base refs, task notes and acceptance. Discover commands, dependencies, freeze state and environment. Default: earliest eligible checkpoint in PLAN order.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN, DECISIONS, assigned notes and relevant code. Write owned application paths and task notes only; never the toolkit or unrelated workers' paths.

## Workflow

1. Select the earliest approved unfinished checkpoint with complete checkpoint dependencies; verify baseline approval, assignment and coding-window/freeze permission.
2. Determine eligible assigned tasks in listed order. Each needs its own branch/note and available approved dependency base. Do not merge unmerged predecessors, claim unassigned tasks, or delegate automatically.
3. Write the strict implementation plan in each task note before edits. Implement the bounded vertical outcome and relevant tests while preserving neighbors.
4. Run configured relevant checks and representative/edge behavior; record exact subject/environment and actual outcomes. Use the test-build procedure for whole-build evidence when applicable.
5. Update owned notes and hand off. Report unavailable dependencies/other-owned tasks as remaining work; stop at this checkpoint. Implementation reaches ready_for_review, never complete solely from edits.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Selected checkpoint

ID, selection reason, approval/assignment/base references; embed the seven H4 plan sections here.

### Task outcomes

Per task: state, branch/base, owned changes, acceptance evidence and blockers.

### Delivered behavior

What works with representative input versus unverified work.

### Remaining gate work

Integration, other-owned/blocked tasks and whole-checkpoint acceptance still required.

## Acceptance criteria

Only one approved checkpoint and assigned tasks were touched; required checks are honest; no automatic merge/release/next checkpoint. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Unapproved checkpoint, ownership conflict, missing dependency, unavailable access or freeze exception blocks affected work. Continue independent assigned work within the same checkpoint; return incomplete if any requested work remains. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

