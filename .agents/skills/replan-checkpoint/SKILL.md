---
name: "replan-checkpoint"
description: "Reassess checkpoint scope, ownership, and timing after progress reviews, capacity changes, blockers, or deadline risks."
---

# replan-checkpoint

## Purpose and triggers

Use for checkpoint replanning; do not silently rewrite accepted intent.

## Inputs and prerequisites

Required: current approved PLAN, observed progress/evidence, remaining capacity and clock. Discover task states, blockers, contracts and cuts. Default: proposal only.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN, DECISIONS, task notes and playbook sections 8–9. Apply approved changes only as the authorized integration owner; preserve completed work and history.

## Workflow

1. Compare actual revisions, verification and delivery against checkpoint commitments; separate facts from estimates.
2. Identify critical-path blockers, changed capacity, unavailable owners and deadline/freeze effects.
3. Propose retain/cut/defer/reassign choices that preserve the core demo and measurable gate.
4. Present the strict revised plan, changed consumers, required approvals and next checkpoint timing. Apply only already-approved changes within delegated ownership.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Variance

Expected versus observed progress, evidence and capacity.

### Proposed changes

Retain/cut/defer/reassign decisions and impacts; embed the seven H4 plan sections here.

### Retained demo

Smallest honest journey and updated proof/cut triggers.

### Approval requirements

Exact owner decisions and existing approval references; proposed changes remain proposed.

## Acceptance criteria

Every change has an operational reason and preserves verified work; revised scope fits actual capacity. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

An unavailable owner cannot be assumed to consent. Reassignment is an explicit integration-owner decision after inspecting outstanding changes. Missing facts produce a conditional proposal. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

