---
name: "test-build"
description: "Test an identified build or integrated revision using configured checks, live integrations and the core demo; report evidence without repairing source."
---

# test-build

## Purpose and triggers

Use for build/integration verification, distinct from code review or implementation.

## Inputs and prerequisites

Required: exact subject revision/artifact, PLAN acceptance and commands, fixtures, designated test environment. Discover required integrations and prior evidence. Default: no source changes.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN sections 3–7, relevant notes/tests and playbook section 4. Write test artifacts and an assigned evidence note only. Inspect commands for source rewriting or external side effects first.

## Workflow

1. Resolve exact commit/artifact and environment. If dirty, record a reproducible diff/artifact identity; HEAD alone is insufficient.
2. Run applicable configured build/static/unit checks, then integration and core journey checks in the designated environment. Mark unavailable required checks not_run, never not_applicable.
3. Exercise representative inputs and meaningful failure cases. Verify required live services; mocked success cannot establish live integration.
4. Record expected/observed outcomes, commands, environment and revision. Reuse prior results only after confirming matching code, environment and scope.
5. Issue the gate verdict; do not fix source, approve a merge, tag or deploy.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Build identity

Commit/artifact, dirty-state identity, runtime/service configuration and fixtures.

### Check results

Required and optional checks with actual outcomes and commands.

### Integration evidence

Cross-boundary and required real-service results, plus representative/failure scenarios.

### Gate verdict

Start with ready, not_ready, or incomplete; name unmet gates and evidence.

## Acceptance criteria

A ready verdict has all required evidence for the exact subject; failures and unavailable tests remain visible. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Failed checks yield not_ready; unavailable evidence yields incomplete. Do not rewrite source through formatters or run destructive/live operations without applicable authorization. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

