---
name: "submission-preflight"
description: "Check official submission requirements against release, video, access and artifacts, and distinguish readiness from confirmed submission."
---

# submission-preflight

## Purpose and triggers

Use before submission or after relevant artifact changes; not automatic submission.

## Inputs and prerequisites

Required: official rules/deadline, selected tracks, release/artifacts, links and submission owner. Discover evidence, access requirements and receipt if already submitted. Default: inspect only.

Resolve the host project root from the invoking adapter/user, not this file's repository. Read project instructions, [shared contract](../../../docs/PROJECT_CONTRACT.md), [formats](../../../docs/FORMATS.md), and relevant approved project records. Source guidance lives in this toolkit; project state stays in the host. If invoked directly without a clear host, resolve it before dependent work.

## Read and write boundaries

Read PLAN event/release/submission sections and playbook sections 6–10. Write authorized submission-evidence fields only; no implicit upload, publication or visibility change.

## Workflow

1. Map every official requirement and track clause to current artifacts, deadline/offset and responsible owner.
2. Compare claims, video and deployment with the identified release and verified live integrations; flag mismatches.
3. Test allowed link access with an appropriate fresh session, video playback/duration and demo journey; report inaccessible resources.
4. Produce readiness verdict and remaining buffer. A draft form is not submission.
5. If submission was explicitly authorized and performed, inspect receipt/confirmation identity and time; otherwise report not submitted or confirmation unavailable.

## Outputs

Return the strict common report from FORMATS. Use the following H3 subsections inside Result, in order; retain them even for blocked outcomes. Do not create a report file unless a destination is assigned.

### Requirement matrix

Requirement/source, artifact/proof, status, owner and gap.

### Artifact checks

Release/video/text consistency, access, playback and demo results.

### Readiness verdict

Start with ready, not_ready, or incomplete; list blocking requirements and time buffer.

### Submission confirmation

Observed platform receipt/ID/link and timestamp, or explicitly not submitted/unverified.

## Acceptance criteria

Readiness is requirement-backed; submitted is used only with observed receipt evidence. All required report sections, metadata and verification rows are present; distinguish observations from assumptions.

## Failure and approval behavior

Inaccessible required links, unknown official requirements or missing proof prevent ready. Publishing/uploading/submitting need applicable authorization. A missing receipt never becomes confirmed submission. Preserve prior explicit authorization and continue independent authorized work where possible. Missing prerequisites receive a concrete blocked/incomplete report, not fabricated success.

