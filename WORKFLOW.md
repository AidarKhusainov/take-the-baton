# Take the Baton workflow

The human decides expected behavior, material tradeoffs, and when to publish or merge. Agents handle routine technical work within the approved scope.

Read the work project's instructions. For explicit resumption, resolve the original profile from the [task record](#resume-in-any-session) or the original profile path supplied by the user. For new work, use the profile supplied by the user or found through activation. The default profile is `.take-the-baton/profile.md`. Use [SETUP.md](SETUP.md) when a profile or a private storage location is needed. Verify that in-project storage is untracked and locally excluded before writing. Keep private profiles, task records, and decision journals out of staging, commits, and publication. Follow the project rules and the user's authorizations throughout.

Use the steps that apply to the request. A straightforward change can stay in the current session. Agree on material decisions before implementing the affected change, save a task record for work that needs to continue in another session, and run independent review when required. The user's instructions and project rules apply to every task.

## Assess an idea

When the user asks whether an idea is worth pursuing, start with the described problem and the outcome they want.

1. Check the relevant code, contracts, docs, and tests to establish current behavior. Identify who is affected and any existing workaround. Use a focused reproduction when it is available within the project's rules. Consult [relevant decisions](#remember-decisions-across-tasks).
2. Search the project's tracker or other agreed task source for related work. Link an existing task if it covers the idea. Name the sources searched and state any gaps.
3. Report what you confirmed, what remains unknown, and one recommended next step. Cite the revision examined and the evidence for the recommendation. Recommend using an existing task, running the smallest check that can settle the question, filing a task with a specific expected outcome, or deferring the idea with a reason.

An assessment on its own ends with the report in chat. Continue to [registration](#register-a-task) when the user has asked for it and any stated conditions are met. If the user asks to file only if the problem is confirmed, establish the problem, check for duplicates, and state the expected outcome before creating anything. Reuse a task that already covers the idea. If those checks are incomplete, report the gap and keep registration pending.

## 1. Take in the task

For explicit resumption, follow [the resumption steps](#resume-in-any-session). For new work, choose the route that matches the request.

- **Existing task.** [Look up the task record](#find-a-task-record), then read the task, its latest relevant comments, and linked requirements. Record the key or URL and surface any conflict that changes the work.
- **Register an idea.** Follow [the registration steps](#register-a-task). Return the confirmed task reference, or the draft and pending status if remote creation is unavailable. Stop after registration unless the user also asked for implementation.
- **Implement from a description.** Continue to [agree on behavior](#2-agree-on-behavior). Register the task first if the user requests registration or the project requires it. While registration is pending, continue only with work that project rules allow without a task key.

Create a [task record](templates/task.md) when registering a task, before handing off implementation or review to another session, before pausing for later resumption, or when the user or project requires one. Otherwise, keep decisions, change references, and results in the current chat. When a record becomes necessary, carry forward the baseline, agreed behavior, exact change if one exists, check results, and next action.

### Find a task record

When given a tracker key or URL, search the profile's task directory and the configured private registration records, directly or through the agreed coordinator. Match the saved identifier for the intended project and tracker destination, including in records named with a local ID. If both routes lead to the same record, use it once. If different records match, ask which one to use. When given a local task ID or record path, use it to locate the record.

### Register a task

1. Assign one owner for lookup and creation for this request and destination. Across worktrees, use the same private registration records or a coordinator with access to them. If the route is unknown or inaccessible, keep remote creation pending and ask for the original record, tracker reference, or agreed route. Account for relevant attempts in older locations before creating anything.
2. Draft a title, problem, expected outcome, and any known acceptance criteria. Carry forward earlier assessment findings that current sources still support. Ask about gaps that affect what gets registered or where it belongs. Search the shared registration records for completed and unresolved attempts, even when the request is just a description. Compare the title, problem, and expected outcome. Reuse a confirmed match, reconcile an unresolved attempt, and ask whether to reuse or create a distinct task if the match is ambiguous.
3. If several sessions can register the request, use a coordinator that reserves it before creation or a shared request ID with a tracker guarantee against duplicates. Otherwise, route registration through one designated session and leave other attempts pending. Other sessions use the same record and wait for the owner's result.
4. Before calling the tracker, save the requested action, destination, submitted details, and any supported stable request ID in a record with a stable filename. Mark the attempt as started. Read back the result and save the confirmed key or URL in the same record. If remote creation is unavailable, prepare a draft or use the agreed local destination and keep required remote registration pending.
5. Treat a call that ends without a confirmed outcome as uncertain. Use the saved destination, submitted details, and request ID to check whether the task exists. If found, save and reuse its reference. Retry only if the first call is known to have created nothing or the tracker guarantees that retrying with the same request ID cannot create a second task. If the outcome remains uncertain, give the user the record path and keep registration pending.

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

Check the workspace against the recorded baseline and follow the project's branch rules. Reuse the intended task branch when it fits those rules. Create a branch when it is needed for authorized work, including an authorized PR, and project rules permit it. Use the [change history templates](#change-history-templates) for branch names and descriptions. Preserve unrelated changes and implement within the agreed scope. Bring any material change to the spec back to the human.

For a reproducible bug or new testable behavior, use the agreed acceptance criteria to define the expected result. Add or reuse a focused test before changing the implementation. Run it against the prior implementation and confirm that the failure demonstrates the bug or missing behavior. If it already passes, check that it covers the intended scenario and that a change is still needed. Make the smallest change that satisfies the criterion, then rerun the same test and confirm that it passes. Record the criterion, the test reference, and the observed before and after results.

For a refactor that preserves behavior, use existing tests that cover the affected behavior when available.

If a required test run is unavailable, including the before or after run for a bug fix or new behavior, record which result is missing, what blocked it, and what other checks were possible. Use the handoff route in the profile or give the user the command and the exact inputs. For the before run, provide the original implementation revision and the test-only patch, including any fixtures, or an accessible equivalent tree with the test and without the fix. For the after run, provide the exact candidate with the same test and the fix. Continue only with steps that project rules allow while the run is pending. Record the outcome after the run actually takes place.

Run focused checks during development and the project's relevant final checks. Record each command, outcome, test count when available, and any blocked or skipped checks. A run with zero relevant tests leaves those scenarios unverified.

### Decide which verification results still apply

Tie each result to the agreed spec version and the revision or tree actually checked. If unrelated workspace changes could affect the result, mark it preliminary. Preserve the original workspace.

- **Checks of the integrated change.** For a PR, check the intended base with the exact outgoing change applied, using the project's prescribed environment. Use an isolated checkout, an equivalent committed tree, or PR CI when project rules allow it.
- **Checks of the head alone.** A check defined for the head alone, such as commit signature verification, applies to the exact head it checked.
- **PR CI.** Use the project's rules and CI configuration to establish the required inputs. Record the run reference and confirm the tested head for a head-only check, or the tested base and head or exact integrated tree for an integration check. A status attached to the head alone does not establish what CI ran against. Keep required evidence pending if its scope or inputs cannot be confirmed.

When the spec, base, or change moves, re-evaluate recorded results and mark any that no longer apply as stale. A head-only result can still count for the same head unless the project requires a fresh run. An integration result can carry over only if the project allows it and the tested tree is identical. For review, check the recorded spec version, comparison base, and exact diff. Confirm which approvals still apply under project rules. Repeat the affected checks and review required for the next action. Track requirements for later actions as pending until their results are available.

## 4. Hand off the diff for review

Use independent review when the user requests it or project rules require it. If an independent check could resolve a material risk, bring that decision to the user. When review does not apply, report it as not required and still report the verification results.

For independent review outside a PR, assign one independent reviewer session when the first diff is ready. Record how to reach the session when a reference is available. The developer sends the reviewer the agreed spec, exact diff, project rules, and check results. Record the submitted diff. Keep the diff and check results available for the user to inspect during review. For review that requires an open PR, use the project's PR review route.

If the environment requires a manual handoff, use the route in the project profile. Keep required review pending until the reviewer completes it, including when the review route is unavailable.

## 5. Review and resolve findings

Keep any assigned developer and reviewer for every round on the task, following the [replacement rules](#resume-in-any-session) when an assigned session cannot be resumed. The reviewer records the spec version, comparison base, and exact change reviewed. The reviewer describes each finding with its location, consequence, and evidence. The developer checks the finding against the current change and records one of these dispositions:

- **Confirmed.** Fix within scope and record the evidence.
- **Dismissed.** Record the evidence that resolves the concern.
- **Needs a decision.** Before changing the affected work, explain the finding, evidence, and tradeoff and ask the user to decide when it is disputed, expands scope, or requires accepting a material risk.

After a fix or requested cleanup, the developer records the updated diff, reruns the affected checks, and sends the new diff and results back to the assigned reviewer. The reviewer checks the fixes against the original findings and examines any other changes in the new diff. Finish the loop when each finding has a disposition, any required decisions are recorded, and the current diff has been reviewed. If a round leaves the same findings open without new evidence, show the human what remains and ask how to proceed.

### Report the change to the human

Give the human a brief summary of what changed and why, the exact diff with links to key code locations, the check results, and any questions that require their decision. For behavior changes, link acceptance criteria to checks and report before and after results when test-first verification applies. Report local checks, independent review, and remote CI separately, with the revisions or tree each covered. If no independent review took place, state that explicitly. A developer's check of their own diff and test results counts as local verification. List pending requirements and explain what is holding them up. Use the [action requirements](#action-requirements) to determine readiness.

Optionally use [clear-explanations](https://github.com/AidarKhusainov/skills/blob/master/clear-explanations/SKILL.md) when writing reports or questions for the human.

## 6. Publish and respond to feedback

### Action requirements

Use the profile and current project rules to determine the requirements for each action. If the profile leaves a requirement unclear, check the project rules and ask only about unresolved conditions that affect the next action.

Use the requested outcome to decide how far to proceed. One explicit request can authorize several actions, such as creating a branch, committing, pushing, and opening a PR. Carry out the authorized steps as their prerequisites are met. If the next in-scope action is ready and needs permission, name the action and its target and ask directly. Once the user approves it, continue to the next decision or the requested outcome. Ask separately for actions outside that authorization, such as rewriting published history.

| Next action | What must be true |
| --- | --- |
| Hand off the diff for human review | Run required checks available at this stage. Complete any applicable preliminary review, fix confirmed findings within scope, and rerun affected checks. If a prerequisite is incomplete or failing, mark the handoff pending and keep the diff available for inspection. |
| Push the branch | Confirm authorization and meet the project's push requirements. Compare the outgoing commits against the intended PR base and verify that the diff matches the checked change. Checks required at this stage must be final for that change. |
| Open a draft PR | Confirm authorization to publish and meet the project's requirements for pushing and opening a draft. Checks or reviews that require an open PR can follow publication unless the project requires an earlier equivalent check. |
| Open a PR as ready or mark a draft ready for review | Meet the applicable push and PR requirements and the project's requirements for entering review. For an existing draft, confirm its current base, head, and diff match the verified change before changing its status. |
| Report ready to merge | Refresh the PR base and head and confirm that the published diff matches the verified change for the agreed spec. Required CI, reviews, approvals, and manual acceptance checks must be complete for this revision, and any required PR update must be published. The human decides whether to merge and performs the merge. |

Before each publication action and before reporting merge readiness, [confirm that the evidence still applies](#decide-which-verification-results-still-apply). If a prerequisite is incomplete or failing, or publication is unavailable, prepare the title, description, and diff for handoff and record the affected action as pending. Bring decisions that block progress to the human when they arise.

### Publish and update the PR

Follow the profile and project rules for commits, pushes, and linking or closing related tasks. Use the [change history templates](#change-history-templates) for commit messages and PRs. If a hook fails, inspect the output, fix the cause within scope, and rerun the affected check. Before retrying an authorized push, repeat the comparison and recheck any evidence affected by the fix. If the failure remains or requires a decision, report it and keep the action pending.

After publication, read back the PR base and head, confirm that the diff matches the verified change, and record the PR reference and both revisions. If the diff differs, record what must be rechecked before reporting readiness. Use the project's PR review route once the PR is eligible.

Read the latest PR comments and refresh the PR base and head. Check each finding against the current diff using the [review and fix loop](#5-review-and-resolve-findings). Record which findings still apply and why. Keep the assigned developer and reviewer where applicable.

Push verified fixes to the existing PR branch within the user's authorization and apply the push requirements above. If the push is pending, record the fix as local and the PR update as pending. Confirm the new remote head before reporting the fix as published.

[Report the change and check status](#report-the-change-to-the-human) at review handoff and when reporting merge readiness.

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

To resume, locate the original task record. For a tracker key or URL, use the [task record lookup](#find-a-task-record) with the supplied original profile or the profile available in the current worktree. If that lookup cannot reach the original record, ask for the original record path or the original profile path and keep resumption pending. A new request to work on an existing tracker task can proceed under project rules when no prior record is found. Read the record's profile reference before using any profile found through activation. Resolve an absolute path as written and a path marked `record-relative:` from the directory containing the record. For a legacy relative path, use the original checkout only when its location and the intended profile can be confirmed. If the record's profile cannot be resolved or conflicts with a supplied profile, keep resumption pending until the user confirms the original profile path. Verify that the profile belongs to the intended project and scope before proceeding.

Once the record and profile are available, refresh relevant task or PR updates, including the current PR base and head if there is a PR. If requirements changed, resolve any material differences with the human before continuing. [Confirm that the recorded evidence still applies](#decide-which-verification-results-still-apply). The developer reruns affected checks and returns the updated diff to the assigned reviewer when review needs to be repeated.

A new session can coordinate the task and continue work that does not require an assigned session. Use the recorded references or the profile's manual handoff route to reach the assigned developer and reviewer. If an assigned session cannot be resumed, reassign the role when the project rules and the user's authorization allow it. Record the previous and new assignments and the reason, preserving the prior decisions and findings. Give the replacement the agreed spec, exact change, check results, and open findings. A replacement reviewer independently reviews the current diff before that review is marked complete. If reassignment needs a decision or no eligible replacement is available, explain the blocker and keep the step pending.
