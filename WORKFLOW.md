# Take the Baton workflow

The human decides expected behavior, material tradeoffs, and when to publish or merge. Agents handle routine technical work within the approved scope.

Read the work project's instructions and the profile located through the activation instructions, supplied by the user, or referenced by the task record. The default profile is `.take-the-baton/profile.md`. Use [SETUP.md](SETUP.md) when a profile or a private storage location is needed. Verify that in-project storage is untracked and locally excluded before writing. Keep private profiles, task records, and decision journals out of staging, commits, and publication. Follow the project rules and the user's authorizations throughout.

Use the steps that apply to the request. A straightforward change can stay in the current session. Agree on material decisions before implementing the affected change, save a task record for work that needs to continue in another session, and run independent review when required. The user's instructions and project rules apply to every task.

## Assess an idea

When the user asks whether an idea is worth pursuing, start with the described problem and the outcome they want.

1. Check the relevant code, contracts, docs, and tests to establish current behavior. Identify who is affected and any existing workaround. Use a focused reproduction when it is available within the project's rules. Consult [relevant decisions](#remember-decisions-across-tasks).
2. Search the project's tracker or other agreed task source for related work. Link an existing task if it covers the idea. Name the sources searched and state any gaps.
3. Report what you confirmed, what remains unknown, and one recommended next step. Cite the revision examined and the evidence for the recommendation. Recommend using an existing task, running the smallest check that can settle the question, filing a task with a specific expected outcome, or deferring the idea with a reason.

An assessment on its own ends with the report in chat. Continue to [registration](#1-take-in-the-task) when the user has asked for it and any stated conditions are met. If the user asks to file only if the problem is confirmed, establish the problem, check for duplicates, and state the expected outcome before creating anything. Reuse a task that already covers the idea. If those checks are incomplete, report the gap and keep registration pending.

## 1. Take in the task

Look for an existing [task record](templates/task.md) in the profile's task directory. When given a tracker key or URL, match it against identifiers stored in existing records, including records named with a local ID. When given a local task ID or record path, use it to locate the record.

Before creating a record for registration or issuing a new remote create request, check unresolved registration attempts in the same destination even if the user supplied only a description. Compare the saved title, problem, and expected outcome with the request. Reuse the matching record and keep its filename. If several records could match, or a possible match cannot be resolved, ask which record to use before creating anything.

Create a record when registering a task, before handing off implementation or review to another session, before pausing for later resumption, or when the user or project requires one. Otherwise, keep relevant decisions, change references, and results in the current chat. When a record becomes necessary, carry forward the baseline, agreed behavior, exact change if one exists, check results, and next action.

Use a stable filename for a new record. Record the requested action and destination. Before a remote create call, save the submitted title, problem, expected outcome, and any stable request ID supported by the tool. Mark the attempt as started before sending the request. Treat an interrupted attempt with no confirmed outcome as uncertain. Keep one registration owner for the record. Any later session continues registration from that same record.

- **Existing task.** Read the task, its latest relevant comments, and linked requirements. Record its key or URL and surface any conflict that changes the work.
- **Register an idea.** Draft a title, problem, expected outcome, and any known acceptance criteria. Ask about gaps that affect what gets registered or where it belongs. Use the profile's destination when the user asks to register it. Carry findings from an earlier assessment into the task record when they are still supported by current sources. Confirm the created task, save its key or URL in the same task record, and return its reference. Registration alone ends here.
- **Implement from a description.** Continue to analysis. Register the task first if the user requests registration or the project requires it. If registration is pending, continue only with work the project allows.

When remote creation is unavailable, prepare the draft or use the agreed local destination. Record remote registration as pending when required. If a create request has an uncertain result, record it. Use the saved destination, submitted details, and request ID when available to check whether the task exists. If found, save and reuse its confirmed reference. Retry only when the first request is known to have created nothing or the tool guarantees that retrying with the same request ID cannot create a second task. If uncertainty remains, give the user the task record path and keep registration pending until the outcome is resolved. If the project requires a tracker key for a step, hold that step until the key is available and complete any analysis the project allows.

## 2. Agree on behavior

Check current code, contracts, project documentation, and tests. Consult [relevant decisions](#remember-decisions-across-tasks). Record the baseline examined, what already exists, and the behavior that should change.

When the user has asked for implementation and the desired behavior and acceptance checks are clear from the request and project sources, use them as the spec. Follow any project requirements for a formal spec or separate approval. Resolve routine questions from project sources. When an unresolved decision would materially affect behavior, scope, or risk, propose the expected outcome and acceptance checks, record the human's decision, and wait for agreement before implementing the affected change. For a task with significant alternative flows, use a use-case spec covering the actor or trigger, inputs, expected flow, observable outcome, alternatives, and acceptance checks.

Use these examples to decide when to ask the user about an open choice.

- **Behavior or scope.** Ask when reasonable options lead to different user-visible outcomes or expand the task.
- **Architecture.** Ask before changing a module boundary, public contract, shared data model, or deployment approach.
- **Dependencies and tooling.** Ask before adding a production dependency or external service, or changing shared tooling or CI.
- **Risk.** Ask when proceeding requires accepting a material risk, for example publishing with a known limitation that affects users.

Follow decisions already made in the project or by the user. Handle local implementation choices and selection among authorized tools using project conventions. When asking, explain the consequence, give the viable options, and recommend one when the evidence supports it. The user decides disputed review findings that require a decision, authorizes PR publication, and decides when to merge.

When an unresolved implementation choice would materially affect the project, have that discussion before editing the affected code. Record the selected approach and its rationale with the agreed behavior. Implement the selected approach in small increments that can be checked independently.

For a full use-case spec, optionally use [use-case-spec](https://github.com/AidarKhusainov/skills/blob/master/use-case-spec/SKILL.md) as the writing format. Keep acceptance checks in the task record or chat when the format leaves them outside the spec.

## Remember decisions across tasks

When the user asks to remember an agreed decision for future tasks, save it in the private journal referenced by the project profile. If a journal is needed, use the agreed private storage and [verify protection for its path](SETUP.md#confirm-one-proposal) before writing. Add the journal path to the profile so another session can find it.

Record the affected area, the agreed decision, its source, and the condition for revisiting it if one was agreed. For example, a team might keep the existing API response format until a client migration is complete. When a project decision already lives in an ADR, ticket, or PR, keep the journal entry short and point to that source. For a decision confirmed in chat, link the confirmation or record who confirmed it and when if a link is unavailable. Update an existing entry for the same decision when the user confirms a change.

When assessing an idea or preparing a spec, read the relevant decision sources and journal entries listed in the profile, if any. Check the source and the revisit condition before relying on a journal entry. If the condition has been met, the source is unavailable, or sources disagree, flag the decision for review. Bring material questions about the expected behavior to the human.

## 3. Implement and verify

The current session can implement once behavior and any required approach decisions are agreed. Use a separate developer session when the user or project requires one or when delegating implementation. Assign one developer, give it the spec, baseline, and acceptance checks, and record how to reach it when a reference is available. If a required separate session cannot be started directly, prepare a manual handoff and mark implementation as pending.

Check the workspace against the recorded baseline and follow the project's branch rules. Reuse the intended task branch when it fits those rules. Create a branch only when the project calls for one and the action is authorized. Use the [change history templates](#change-history-templates) for branch names and descriptions. Preserve unrelated changes and implement within the agreed scope. Bring any material change to the spec back to the human.

For a reproducible bug or new testable behavior, use the agreed acceptance criteria to define the expected result. Add or reuse a focused test before changing the implementation. Run it against the prior implementation and confirm that the failure demonstrates the bug or missing behavior. If it already passes, check that it covers the intended scenario and that a change is still needed. Make the smallest change that satisfies the criterion, then rerun the same test and confirm that it passes. Record the criterion, the test reference, and the observed before and after results.

For a refactor that preserves behavior, use existing tests that cover the affected behavior when available. If a run is unavailable, report which result is missing, what blocked it, and what other checks were possible. Follow the project's requirements for verification.

Run focused checks during development and the project's relevant final checks. Tie the results to the agreed spec version, comparison base, and exact change tested, such as a commit or a saved diff that includes the in-scope changes. Record test commands, outcomes, test counts when available, and any blocked or skipped checks. A run with zero relevant tests leaves those scenarios unverified.

## 4. Hand off the diff for review

Use independent review when the user requests it or project rules require it. If an independent check could resolve a material risk, bring that decision to the user. When review does not apply, report it as not required and still report the verification results.

For independent review outside a PR, assign one independent reviewer session when the first diff is ready. Record how to reach the session when a reference is available. The developer sends the reviewer the agreed spec, exact diff, project rules, and check results. Record the submitted diff. Keep the diff and check results available for the user to inspect during review. For review that requires an open PR, use the project's PR review route.

If the environment requires a manual handoff, use the route in the project profile. Keep required review pending until the reviewer completes it, including when the review route is unavailable.

## 5. Review and resolve findings

Keep any assigned developer and reviewer for every round on the task, following the [replacement rules](#resume-in-any-session) when an assigned session cannot be resumed. The reviewer records the spec version, comparison base, and exact change reviewed. The reviewer describes each finding with its location, consequence, and evidence. The developer checks the finding against the current change and records one of these dispositions:

- **Confirmed.** Fix within scope and record the evidence.
- **Dismissed.** Record the evidence that resolves the concern.
- **Needs a decision.** Bring the human the tradeoff when the finding is disputed, expands scope, or requires accepting a material risk.

After a fix or requested cleanup, the developer records the updated diff, reruns the affected checks, and sends the new diff and results back to the assigned reviewer. The reviewer checks the fixes against the original findings and examines any other changes in the new diff. Finish the loop when each finding has a disposition, any required decisions are recorded, and the current diff has been reviewed. If a round leaves the same findings open without new evidence, show the human what remains and ask how to proceed.

### Prepare the diff for human review

Before asking a human to review the diff, run the required checks available at that stage. Complete any applicable preliminary review and fix confirmed findings within scope, then rerun affected checks on the current diff. Bring decisions that block progress to the user when they arise.

Give the human a brief summary of what changed and why, the exact diff with links to the key code locations, the check results, and any questions that require their decision. For behavior changes, link the relevant acceptance criteria to the tests or other checks and report the before and after results when test-first verification applies. List any pending required checks or preliminary reviews and explain what is holding them up. Mark the handoff as pending while a prerequisite for this stage is incomplete or failing.

## 6. Publish and respond to feedback

Use the profile and current project rules to distinguish requirements for the next action, such as pushing, opening a PR, or marking a draft ready, from requirements before merge. If the profile does not specify when a requirement applies, check the current project rules and ask about any unresolved condition that affects the next action.

When the user asks for a PR, meet each action's prerequisites before taking it. Tie required checks and review to the agreed spec and exact change. If a prerequisite for the next action is incomplete or failing, or publication is unavailable, prepare the title, description, and diff for handoff and record publication as pending. A draft can start PR checks or review when the project allows it and the user has authorized publication. Meet the requirements for pushing and opening the draft, then check the requirements for marking it ready before changing its status.

Follow the profile and project rules for commits and pushes. Use the [change history templates](#change-history-templates) when preparing commit messages and PRs. If a hook fails, inspect its output, fix the cause within scope, and rerun the affected check. Retry the authorized action once the issue is resolved. Before retrying a push, repeat the outgoing diff comparison below and any checks or review affected by the fix. If the failure remains or requires a decision, report it and keep the action pending. Keep required checks in effect.

After preparing the outgoing commits, compare their exact diff against the intended PR base with the verified change before pushing. If the diff or base changed, repeat the affected checks and any independent review required before the next publication action. Apply the project's rules for linking or closing related tasks.

After publication, read back the PR's base and head and verify that its exact diff matches the verified change. Record the PR reference and both revisions. If they differ from what you verified, record what needs rechecking before reporting the PR ready. Report local checks and remote CI for the current head separately. Track checks and reviews that need an open PR as pending at their applicable stage, and use the project's review route once the PR is eligible.

For colleagues' findings, refresh the PR's base, head, and feedback, then run the same verification and fix steps. Use the assigned developer and reviewer where those roles apply. Apply the prerequisites for the push before sending updates. Push verified fixes to the existing PR branch within the user's authorization. If a push is pending, record the fix as local and the PR update as pending. Confirm the new remote head before reporting the fix as published. Check which reviews, CI results, and approvals still apply to the new head and which need to be obtained again.

Before reporting the PR ready to merge, refresh its base and head and confirm that the published diff matches the current verified change for the agreed spec. Confirm that any required independent review, CI for that head, approvals, and manual acceptance checks are complete. Keep merge readiness pending while required review or a PR update is pending, or while required evidence is missing, stale, or failing. At this stage include CI and approvals that can only be obtained after the PR is open. Share the final diff and check status using the [human review handoff](#prepare-the-diff-for-human-review). The human makes the merge decision and merges the PR.

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

Before pausing for later resumption or handing work to another session, create or update the task record with the stage, owner of the next action, agreed spec or acceptance checks, comparison base, check results, and any review decisions. Use the location agreed in the profile.

When there are changes to carry forward, record the checkout or worktree, the branch if there is one, and an exact change reference. Use an accessible commit or a complete saved patch that includes all in-scope changes, including new files. Use only the project's approved private storage or transfer route. Verify that the recipient can open the change before marking the handoff ready. If the next session is not known yet, record how it can open the change and verify access on resumption. If the recipient cannot access it, report the blocker and keep the handoff pending.

To resume, read the record and refresh relevant task or PR updates, including the current PR base and head if there is a PR. If requirements changed, resolve any material differences with the human before continuing. Compare the agreed spec version, comparison base, and exact change with the recorded evidence. If any of them changed, mark affected evidence as stale. The developer reruns the affected checks and returns the updated diff to the assigned reviewer when review needs to be repeated.

A new session can coordinate the task and continue work that does not require an assigned session. Use the recorded references or the profile's manual handoff route to reach the assigned developer and reviewer. If an assigned session cannot be resumed, reassign the role when the project rules and the user's authorization allow it. Record the previous and new assignments and the reason, preserving the prior decisions and findings. Give the replacement the agreed spec, exact change, check results, and open findings. A replacement reviewer independently reviews the current diff before that review is marked complete. If reassignment needs a decision or no eligible replacement is available, explain the blocker and keep the step pending.
