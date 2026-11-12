---
name: "review-integration"
description: "Review task changes, contract approvals, consumers and verification evidence before integration or release assessment."
---

# review-integration

## Purpose and triggers

Use for integration readiness; test-build owns execution evidence, this skill owns review.

## Inputs and prerequisites

Required: candidate/base revisions, task IDs/notes, approved contracts, decision approvals and test evidence. Discover changed consumers, ownership and target baseline. Default: review only.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN, DECISIONS, task notes, diff/tests and playbook section 4. Write assigned review fields only; no automatic merge or canonical approval.

## Workflow

1. Resolve exact candidate/base and inspect the actual diff against assignment, scope and ownership.
2. Inspect affected consumers, dependency availability and proposed versus accepted deviations; confirm PLAN/DECISIONS agree.
3. Assess evidence against current revision, environment and scope. Use the test-build procedure if execution is authorized and needed; do not duplicate or invent stale test results.
4. Review secrets, allowed dependencies/licenses, claim accuracy and rollback; report concrete findings.
5. Issue verdict and merge conditions, including required integrated-commit rechecks. Passing review is not execution authority.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Scope findings

Owned paths, behavioral completion, dependencies and out-of-scope changes.

### Contract findings

Affected contracts/consumers and approval references or blockers.

### Evidence assessment

Current versus stale/missing evidence and additional checks.

### Verdict

Start with ready, not_ready, or incomplete and justify.

### Merge conditions

Authorized integrator actions, integrated checks, canonical updates and rollback.

## Acceptance criteria

No required stale/missing check or unapproved contract change yields readiness. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Unapproved deviations or ownership conflicts block integration; missing evidence is incomplete. Review invocation never authorizes merge, deployment, tag or acceptance of architecture. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

