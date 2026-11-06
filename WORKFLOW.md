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

Hand the agreed spec, baseline, and acceptance checks to a fresh developer session. If you cannot start one, prepare the handoff for a separate session and mark implementation as pending. The developer who picks it up checks the workspace against the recorded baseline and follows the project's branch rules. Reuse the intended task branch when it fits those rules. Create a branch only when the project calls for one and the action is authorized. Follow project conventions for the task key in branch names and commit messages. Preserve unrelated changes and implement within the agreed scope. Bring any material change to the spec back to the human.

Run focused checks during development and the project's relevant final checks. Tie the results to the agreed spec version, comparison base, and exact change tested, such as a commit or a saved diff that includes the in-scope changes. Record test commands, outcomes, test counts when available, and any blocked or skipped checks. A run with zero relevant tests leaves those scenarios unverified.

## 4. Give the human the diff

Present the change, its verification evidence, and any remaining questions. Apply requested cleanup, then update the diff identity and rerun affected checks. Continue to independent review when the human hands off the diff. Record the identity of the diff they handed off.

## 5. Review and resolve findings

Give a fresh, independent reviewer the agreed spec, exact diff, project rules, and check results. Record the spec version, comparison base, and exact change they reviewed. Where the current agent cannot start one, prepare a handoff for a separate agent session or a person and keep review pending.

The reviewer describes each finding with a location, consequence, and evidence. The developer validates it against the current change and records one disposition for it:

- **Confirmed.** Fix within scope and record the evidence.
- **Dismissed.** Record the evidence that resolves the concern.
- **Needs a decision.** Bring the human the tradeoff when the finding is disputed, expands scope, or requires accepting a material risk.

Run affected checks after a fix and ask for targeted re-review of substantial changes. Finish the loop when each finding has a disposition, any required decisions are recorded, and substantial fixes have been rechecked. If a round leaves the same findings open without new evidence, show the human what remains and ask how to proceed.

## 6. Publish and respond to feedback

When the user asks for a PR, confirm that verification and independent review are complete for the agreed spec and the change you intend to publish. If review is pending or publication is unavailable, prepare the title, description, and diff for handoff and record publication as pending.

Follow the profile and project rules for commits and pushes. If a hook fails, inspect its output, fix the cause within scope, and rerun the affected check. Retry the authorized action once the issue is resolved. Before retrying a push, repeat the outgoing diff comparison below and any checks or review affected by the fix. If the failure remains or requires a decision, report it and keep the action pending. Keep required checks in effect.

After preparing the outgoing commits, compare their exact diff against the intended PR base with the reviewed change before pushing. If the diff or base changed, repeat the affected checks and review before publication. Use the project's PR template when available. Include the task reference, final behavior, how to verify it, and the observed check results. Apply the project's rules for linking or closing related tasks.

After publication, read back the PR's base and head and verify that its exact diff matches the reviewed change. Record the PR reference and both revisions. If they differ from what you verified, record what needs rechecking before reporting the PR ready. Report local checks and remote CI for the current head separately.

For colleagues' findings, refresh the PR's base, head, and feedback, then run the same validation and fix loop. Apply the same checks before sending updates and after they appear in the PR. Push verified fixes to the existing PR branch within the user's authorization. If a push is pending, record the fix as local and the PR update as pending. Confirm the new remote head before reporting the fix as published.

Before reporting the PR ready to merge, refresh its base and head. Check the current diff, required CI results for that head, required approvals, and any manual acceptance checks. Mark merge readiness as pending if required evidence is missing, stale, or failing. CI that starts after PR creation is checked at this stage. Give the human the final diff and check status. The human makes the merge decision and merges the PR.

## Resume in any session

Update the task record at each handoff with the stage, owner of the next action, spec approval, exact diff identity, checks, and review decisions. Use the location agreed in the profile.

To resume, read the record and refresh relevant task or PR updates, including the current PR base and head if there is a PR. Compare the agreed spec version, comparison base, and exact change with the recorded evidence. If any of them changed, mark affected evidence as stale and repeat the relevant checks or review. If the handed-off diff changed outside the recorded review fixes, return the new diff to the human before resuming independent review. If requirements changed, resolve any material differences with the human before continuing.
