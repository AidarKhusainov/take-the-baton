# Task record

## Current status

- Stage and status:
- Current revision or patch:
- PR reference and publication status:
- Publication handoff, if grouped (group and coordinator references, superseded worker permission, effective transfer and confirmation):
- Last verified PR base and head:
- Local verification status:
- Independent review status:
- Remote CI status for the published iteration:
- Next action and owner:

Update this summary when the revision, stage, or next action changes. Keep supporting evidence in the sections below.

When publication transfers to a group coordinator, record the restriction in the PR and publication status as well. State explicitly that any earlier worker permission for this task is superseded. Keep the existing status field readable by workflows that predate group records.

## Task and handoff

- Task title:
- Stable local ID:
- Confirmed tracker key or URL:
- Registration destination and status:
- Registration owner, submitted title, problem, and expected outcome:
- Registration attempt status and request ID, if available:
- Requested outcome (register, implement, or both):
- Assigned developer session reference:
- Assigned independent reviewer session reference:
- Session reassignments and reasons, if any:
- Profile reference (absolute path or `record-relative: <path>` from this record's directory):
- Take the Baton source URL and exact workflow revision used for this task:
- Group record reference and task ID within it, if grouped:
- Prerequisite output or contract versions and mutation ownership, if grouped:

## Agreed behavior

- Source requirements and later decisions:
- Spec text or path:
- Acceptance checks:
- Agreed spec version and user decision:
- Open questions:

## Change and checks

- Base revision:
- Checkout or worktree, branch, and accessible commit or complete patch for handoff:
- Exact source tree tested (commit or base plus diff) and any other inputs that affect the result:
- Spec version used for the checks:
- Latest diff sent to the reviewer:
- Commands and observed results, marked preliminary or final; for a before/after handoff, the baseline with the test-only patch or equivalent tree, and the candidate with the same test:
- Skipped or blocked checks:
- Remote CI check, run reference, and verified input (head alone, base and head, or exact integrated tree):
- Merge readiness and outstanding checks:

## Review

- Reviewed spec version, comparison base, and exact change:
- Human decisions:

| Finding and evidence | Disposition and reason | Fix and recheck |
| --- | --- | --- |
| | | |

## Multiple or shared PRs

For one PR, the summary above can hold its status and evidence. For several PRs, record each one's base/head, publication status, check and review evidence, and next action separately. For a grouped PR, link to the owning entry and verification evidence in the group record. The group coordinator owns publication, including for a shared PR.

| PR or planned change | Owner or group entry | Verified base/head | Check and review evidence | Status and next action |
| --- | --- | --- | --- | --- |
| | | | | |

## Reflection observations, if enabled

Record only task-affecting observations from approved sources: expected behavior, actual action, observable consequence, and stable evidence reference. Link an existing observation instead of duplicating the same episode across a task and group.

## Subagent selections, when delegated

Use a short entry per assignment or link to its existing chat entry. Record a change of settings or owner when one occurs. Distinguish requested settings from effective settings reported by the host.

| Assignment and agent reference | Priority and constraints | Requested model/effort; effective settings or unknown | Selection or escalation reason | Result and verification evidence |
| --- | --- | --- | --- | --- |
| | | | | |
