---
name: "create-stable"
description: "Promote an exact verified integrated revision to a unique stable tag within explicit local or remote publication authorization."
---

# create-stable

## Purpose and triggers

Use for a named stable promotion, not automatic tagging after reviews.

## Inputs and prerequisites

Required: exact integrated commit, gate, unique tag, matching evidence, previous stable/rollback and authorized publication scope. Discover current tags and project repository. Default: assess only unless the named action is authorized.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN gate/log, integration notes and playbook release guidance. Write authorized project tag operations and canonical release metadata only; never change the toolkit pin.

## Workflow

1. Verify project repository and exact integrated commit, approval, clean/reproducible evidence, gate and rollback. Reassess if code/environment/scope changed.
2. Check local and intended remote tag availability. If remote cannot be inspected, publication cannot be claimed safe or completed.
3. Prepare the promotion result. When already authorized for the named action, create a new annotated tag at the verified commit; never retarget an existing tag.
4. Publish only if remote publication is explicitly covered. Inspect resulting refs and record actual local and remote outcomes separately.
5. Authorized integration owner records stable metadata/gate evidence, identifying the tagged code commit even if a later documentation-only commit records promotion.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Candidate

Exact integrated commit, gate, previous stable and approval scope.

### Gate evidence

Matching verification and limitations.

### Tag result

Requested name, actual target/annotation, created or not created, and reason.

### Publication result

Remote/name/target and observed result, or not authorized/not attempted.

### Rollback

Previous known-good code/environment and recovery instructions.

## Acceptance criteria

No collision, stale evidence or unverified gate is promoted; local success is not reported as remote publication. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Missing authorization produces a proposed promotion, not a repeated permission request if authorization exists. Colliding tags block creation. Publication failure retains the local result and reports incomplete; never force-push. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

