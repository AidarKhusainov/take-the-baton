# Take the Baton workflow

The human decides expected behavior, material tradeoffs, and when to publish or merge. Agents handle routine technical work within the approved scope.

Read the work project's instructions and the profile supplied by the user or referenced by the task record. The default profile is `.take-the-baton/profile.md`. Use [SETUP.md](SETUP.md) when a profile or a private storage location is needed. Verify that in-project storage is untracked and locally excluded before writing. Keep personal profiles and task records out of staging, commits, and publication. Follow the project rules and the user's authorizations throughout.

## 1. Take in the task

Find the [task record](templates/task.md) in the profile's task directory before creating one. When given a tracker key or URL, match it against identifiers stored in existing records, including records named with a local ID. Reuse the matching record and keep its filename. If several records match, ask which to use.

Use a stable filename for a new record. Record the requested action and destination. Before a remote create call, save the registration attempt and any stable request ID supported by the tool.

- **Existing task.** Read the task, its latest relevant comments, and linked requirements. Record its key or URL and surface any conflict that changes the work.
- **Register an idea.** Draft a title, problem, expected outcome, and any known acceptance criteria. Ask about gaps that affect what gets registered or where it belongs. Use the profile's destination when the user asks to register it. Confirm the created task, save its key or URL in the same task record, and return its reference. Registration alone ends here.
- **Register and implement.** Register it, then continue to analysis. For an implementation request given as a description, use a local task record unless the user requests registration or the project requires a tracker task.

When remote creation is unavailable, prepare the draft or use the agreed local destination. Record remote registration as pending when required. If a create request has an uncertain result, record it and check whether the task exists before trying again. If uncertainty remains, give the user the task record path and ask them to resolve it. Reuse a confirmed task reference when retrying or resuming. If the project requires a tracker key for a step, hold that step until the key is available and complete any analysis the project allows.

## 2. Agree on behavior

The analyst checks current code, contracts, project documentation, and tests. Record the baseline examined, what already exists, and the behavior that should change. Write a use-case spec covering the actor or trigger, inputs, expected flow, observable outcome, significant alternatives, and acceptance checks.

Resolve routine questions from project sources. Bring the human questions that change behavior, scope, or risk, with options and a recommendation when possible. Record the answers. Begin implementation after the human agrees to the spec.

## 3. Implement and verify

Assign one developer session to the task after the spec is agreed. Give it the spec, baseline, and acceptance checks. Record how to reach the session when a reference is available. If you cannot start it directly, prepare the handoff for a separate session and mark implementation as pending. The assigned developer checks the workspace against the recorded baseline and follows the project's branch rules. Reuse the intended task branch when it fits those rules. Create a branch only when the project calls for one and the action is authorized. Use the [change history templates](#change-history-templates) for branch names and descriptions. Preserve unrelated changes and implement within the agreed scope. Bring any material change to the spec back to the human.

Run focused checks during development and the project's relevant final checks. Tie the results to the agreed spec version, comparison base, and exact change tested, such as a commit or a saved diff that includes the in-scope changes. Record test commands, outcomes, test counts when available, and any blocked or skipped checks. A run with zero relevant tests leaves those scenarios unverified.

## 4. Hand off the diff for review

When the first diff is ready, assign one independent reviewer session to the task. Record how to reach the session when a reference is available. The developer sends the reviewer the agreed spec, exact diff, project rules, and check results. Record the submitted diff and share it with the human along with the check results while review proceeds.

If the environment requires a manual handoff, use the route in the project profile. Keep review pending until the assigned reviewer can take the diff.

## 5. Review and resolve findings

Keep the assigned developer and reviewer for every round on the task. The reviewer records the spec version, comparison base, and exact change reviewed. The reviewer describes each finding with its location, consequence, and evidence. The developer checks the finding against the current change and records one of these dispositions:

- **Confirmed.** Fix within scope and record the evidence.
- **Dismissed.** Record the evidence that resolves the concern.
- **Needs a decision.** Bring the human the tradeoff when the finding is disputed, expands scope, or requires accepting a material risk.

After a fix or requested cleanup, the developer records the updated diff, reruns the affected checks, and sends the new diff and results back to the same reviewer. The reviewer checks the fixes against the original findings and examines any other changes in the new diff. Finish the loop when each finding has a disposition, any required decisions are recorded, and the current diff has been reviewed. If a round leaves the same findings open without new evidence, show the human what remains and ask how to proceed.

## 6. Publish and respond to feedback

When the user asks for a PR, confirm that verification and independent review are complete for the agreed spec and the change you intend to publish. If review is pending or publication is unavailable, prepare the title, description, and diff for handoff and record publication as pending.

Follow the profile and project rules for commits and pushes. Use the [change history templates](#change-history-templates) when preparing commit messages and PRs. If a hook fails, inspect its output, fix the cause within scope, and rerun the affected check. Retry the authorized action once the issue is resolved. Before retrying a push, repeat the outgoing diff comparison below and any checks or review affected by the fix. If the failure remains or requires a decision, report it and keep the action pending. Keep required checks in effect.

After preparing the outgoing commits, compare their exact diff against the intended PR base with the reviewed change before pushing. If the diff or base changed, repeat the affected checks and return the change to the assigned reviewer before publication. Apply the project's rules for linking or closing related tasks.

After publication, read back the PR's base and head and verify that its exact diff matches the reviewed change. Record the PR reference and both revisions. If they differ from what you verified, record what needs rechecking before reporting the PR ready. Report local checks and remote CI for the current head separately.

For colleagues' findings, refresh the PR's base, head, and feedback, then run the same validation and fix loop with the assigned developer and reviewer. Apply the same checks before sending updates and after they appear in the PR. Push verified fixes to the existing PR branch within the user's authorization. If a push is pending, record the fix as local and the PR update as pending. Confirm the new remote head before reporting the fix as published.

Before reporting the PR ready to merge, refresh its base and head and confirm that the published diff matches the current reviewed change for the agreed spec. Check required CI results for that head, required approvals, and any manual acceptance checks. Keep merge readiness pending while review or a PR update is pending, or while required evidence is missing, stale, or failing. CI that starts after PR creation is checked at this stage. Give the human the final diff and check status. The human makes the merge decision and merges the PR.

## Change history templates

Use the project's conventions for each branch, commit, and PR. Use these defaults for any part the project leaves open. When a task key is optional and unavailable, omit it from the format.

- **Branch.** Use `<kind>/<task-key>-<purpose>`, or `<kind>/<purpose>` when there is no task key. Use a short slug that describes the intended outcome.

  - `fix/ABC-123-retry-timeouts` for a bug fix.
  - `feature/ABC-12-export-reports` for a feature.
  - `refactor/ABC-45-extract-validation` for a refactor.
  - `docs/update-setup-guide` for documentation without a task key.
  - `feature/ABC-12` when the project uses the task key alone after the prefix.

  Where branch descriptions are supported, include the task reference when available and one sentence about the intended outcome. Otherwise keep that context in the task record.

- **Commit.** Use `<task-key>: <action>` for the subject. Name what this commit changes. In a brief body, explain why the change is needed and what changes as a result. Verify that the message matches the diff being committed.
- **Pull request.** Use `<task-key>: <outcome>` for the title. Fill the project's body template when available. The default body covers the problem, what changed, how to verify it, observed results and pending checks, and the related task when available. Compare the title and body with the final diff and verification evidence. If the scope changes, bring the PR title and body up to date.

## Resume in any session

Update the task record at each handoff with the stage, owner of the next action, spec approval, exact diff identity, checks, and review decisions. Use the location agreed in the profile.

To resume, read the record and refresh relevant task or PR updates, including the current PR base and head if there is a PR. If requirements changed, resolve any material differences with the human before continuing. Compare the agreed spec version, comparison base, and exact change with the recorded evidence. If any of them changed, mark affected evidence as stale. The assigned developer reruns the affected checks and returns the updated diff to the assigned reviewer when review needs to be repeated.

A new session can coordinate the task. Use the recorded references or the profile's manual handoff route to reach the assigned developer and reviewer. If an assigned session cannot be resumed, record the blocked handoff and keep that step pending.
