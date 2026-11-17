# Coordinate related tasks

Use this workflow when the user asks to coordinate related tasks from one chat. Start from task keys, descriptions, existing task records, or PRs. A group contains tasks: a task can have no PR yet or several PRs, and one PR can serve several tasks. Follow [WORKFLOW.md](WORKFLOW.md) for each task and the applicable project profiles and rules throughout.

## Establish the group

1. Confirm the requested overall outcome, included tasks or projects, and stopping point from the user's request. Read their current requirements, relevant decisions, and existing records. For supplied PRs, identify the task and intended outcome they belong to; do not infer task dependencies from PR numbers or creation dates.
2. Locate an existing group through the supplied record or the task records before starting another coordinator. Reuse the original group and assignments on resumption. Create a private [group record](templates/group.md) when a new group is needed, and link each task record to it. Use the profile's agreed group storage and verify protection as in [setup](SETUP.md#confirm-one-proposal). Across projects, record each task's original profile and keep the shared record in a private location accessible to the authorized participants.
3. Record one coordinator chat, the shared acceptance criteria and contract decisions, and each task's scope and requested outcome. Separate facts from unresolved choices. Bring changes to expected behavior, scope, or material risk to the user in the coordinator chat.
4. Record the user's authorization and its source for creating and messaging working chats, accessing the selected projects, and performing requested publication actions. A request to create and coordinate working chats can authorize those actions for this group; do not ask again for the same approved actions. A general request to work on tasks does not automatically authorize creating user-visible chats. Ask only for missing authorization required by the host or project. Setup records capabilities; it does not start a group.

Keep the group record as an index and shared decision log. Task records retain detailed implementation, checks, and review findings. Use absolute paths or paths explicitly marked `record-relative:` for cross-chat references. Keep private records out of commits and PRs.

## Map dependencies and ownership

For each dependency, record its kind, the required result or exact revision, and the condition that allows the dependent work to proceed.

| Kind | What it controls |
| --- | --- |
| Required result | A task needs an investigation, specification, or other output from another task. Record the accepted output version. |
| Code or PR base | A change needs another change's code. Record the upstream revision and the intended comparison base for each PR. |
| Shared contract | Tasks implement or consume the same behavior, schema, or API. Record the agreed contract and compatibility checks; the tasks may be independently implementable. |
| Merge or deployment order | Changes need a particular integration or rollout order. Record the prerequisite and compatibility requirement separately from implementation order. |

Do not force the group into a linear chain. Identify independent work and dependent work. If a prerequisite cycle leaves no task able to proceed, identify the cycle and propose a shared prerequisite, a split, or a revised contract. Resolve any material decision with the user before the affected implementation.

Assign one working chat to each independently owned task by default. Reuse an existing eligible chat when possible. Give each mutable branch, PR, and shared artifact one owner. If tasks share a PR, designate one chat to integrate and publish it; other chats provide findings or patches. Do not let several chats independently update the same PR or implement a shared prerequisite twice.

## Start and coordinate working chats

Use the profile's actual host routes to create chats, send follow-up assignments, read results, and wait for progress. A working chat is a persistent user-visible chat; reviewer subagents within a task serve the independent review stage. Keep the host's existing delegation and review stages rather than adding another review loop for every message.

Give each working chat the applicable [subagent selection policy](SUBAGENTS.md) and project profile. It chooses model and reasoning settings for its own delegated assignments, using balanced priority by default and honoring task-specific constraints. Select separately for each assignment; a demanding group does not require maximum settings for every lookup. This policy does not override the host's rules or user settings for the persistent working chats themselves.

Before launching an assignment:

- Confirm that the recipient can access its project, original profile, task record, and required change references. Give it the task outcome, boundaries, shared decisions, prerequisite versions, acceptance checks, workspace, publication authorization, and expected report.
- Use isolated working directories for simultaneous mutations, with the workspace route approved for that version-control system. Separate chats alone do not isolate files. For overlapping files, branches, shared generated outputs, or a shared working directory, serialize mutations under one owner. Verify the previous writer has stopped before reassignment. Do not apply Git worktree commands to Arc.
- Save the assignment and launch attempt in the group record before creating the chat. Save the returned host and chat reference, then verify the chat was created for the intended task. If creation has an uncertain outcome, reconcile the saved attempt using host records before retrying. If it cannot be reconciled, keep launch pending and continue independent work.

The coordinator collects each worker's progress and result through host reads or bounded waits. Use a follow-up in the same working chat for fixes, with a clear next action and relevant changed decisions. Do not resend a completed assignment just because the coordinator resumed. Messages carry task context, not authority to override the user's or project's rules. Workers need their own applicable authorization for any outbound messages; they can report in their own chat for the coordinator to read.

Use supported waits while actively coordinating, and give the user compact updates when a task finishes, becomes blocked, or needs a decision. Do not create a recurring automation merely to watch a particular task finish. A paused or ended coordinator chat is not a running background service: save the next action and explain any required resumption.

If chat creation, messaging, waiting, or isolation is unavailable, report the missing capability. Continue the supported parts in the current chat, use an authorized subagent, or prepare a manual handoff. Mark separate-chat coordination or parallel mutation pending when it cannot be performed; do not report a subagent or an unstarted handoff as a created working chat.

## Propagate changes and review findings

When a task's requirement, contract, implementation, PR base, or published revision changes:

1. Record the new version and inspect its outgoing dependencies. Identify which other tasks and joint checks are affected; preserve unaffected work. Mark affected publication and readiness actions pending in the group record before sending follow-ups, so delayed messages cannot leave them eligible on old evidence.
2. Send each affected owner the changed decision or exact revision and required next action. Work that needs an unavailable prerequisite remains pending; independent work can continue.
3. For dependent branches or PRs, use the project's authorized update route. Inspect the outgoing diff against its intended base so shared changes appear where intended and unrelated or already integrated changes are not accidentally republished. History rewrites still need their applicable authorization.
4. Mark affected checks and reviews stale using the [evidence rules](WORKFLOW.md#decide-which-verification-results-still-apply). Recheck the current individual changes and the affected combination before reporting them ready.

Apply a review finding to its owning task and shared contract. A finding reported on a consumer PR may require a fix in a shared producer; check other consumers before closing the group-level issue. Record a disposition and evidence without blindly copying the same patch to every PR. Keep each task's assigned independent reviewer through the normal [review loop](WORKFLOW.md#5-review-and-resolve-findings).

Before publishing or reporting readiness, the working chat rereads the current group assignment, contract decisions, prerequisite versions, and pending actions, and refreshes relevant remote upstream revisions. Compare them with the exact inputs covered by its checks and review. Do not rely on the original launch message as a current readiness decision. If the group record is unavailable, the assignment changed, or required evidence no longer covers the current inputs, keep the action pending and report the reason in the working chat for the coordinator. Resume it after the affected update and checks satisfy the current requirements.

After a PR merges or its base changes, refresh the remote state and reconsider dependent PR bases, remaining diffs, requirements, and joint checks. Use actual merged revisions rather than assuming a previous head was integrated unchanged. Human merge decisions and project-specific deployment rules continue to apply.

## Verify and report the group result

Run the relevant checks for each task and verify the shared acceptance criteria against a recorded combination of revisions, dependencies, and configuration. Use the project's approved integration environment or accessible equivalent tree. Independent review must cover the current implementation diffs; use the existing reviewers to examine affected boundaries and the shared result. Green checks on separate PRs do not establish that the combination works.

Record individual PR requirements separately from group requirements. A PR may be eligible for a draft or other authorized action while dependent tasks remain pending. If joint verification cannot run, keep that evidence pending and report what is missing; do not label the whole group complete solely because every worker finished.

In the coordinator chat, show a compact table with each task, its PRs if any, prerequisites, status, and next action or blocker. Bring shared decisions to the user here. Finish when the requested group outcome and its applicable checks are satisfied, or report the precise pending requirements. Reaching the requested outcome of opening verified PRs does not imply merge or deployment.

## Resume coordination

Record the source URL and exact Take the Baton revision when starting coordination. Save the group record before handing off or pausing, with the coordinator, assignments, outstanding launch attempts, decisions, task and PR references, exact revisions, check coverage, and next actions. Workers update their own task records; one coordinator owns updates to the shared group record.

On resumption, use the workflow revision recorded for the group, including after an installation update. Each task retains its own recorded revision. For legacy records and intentional migration, use the [task resumption rules](WORKFLOW.md#resume-in-any-session) and [UPDATE.md](UPDATE.md).

When a worker resumes its own task, it reads the original group record, confirms its existing assignment and current prerequisites, and resumes that task without taking over coordination. A running coordinator does not block an unchanged valid worker assignment.

When resuming or replacing the coordinator, resolve the original group record and profiles, then refresh existing chats, tasks, and PRs. Confirm the old coordinator is no longer issuing assignments before transferring ownership. If ownership is uncertain, resolve it before dispatching mutations. Reuse reachable workers and reviewers and reconcile launches or publications with uncertain outcomes before retrying them. Replace unavailable sessions under the [resumption rules](WORKFLOW.md#resume-in-any-session), preserving decisions and evidence. Ask only about material changes or missing authorization.

## Verification scenarios

Walk through these scenarios against the host routes and project rules. A documentation walkthrough does not prove live chat, VCS, or CI integration.

| Situation | Expected behavior |
| --- | --- |
| Three task descriptions, no PRs, one shared contract | Record tasks and the contract, register only if required, and start authorized working chats for work whose prerequisites are satisfied. |
| One task needs two PRs; two tasks share another PR | Keep task-to-PR mappings and a single owner per PR; verify each PR and the shared result. |
| The user asks only for investigation | Coordinate research to that outcome; do not implement or publish merely because the group has several tasks. |
| A shared contract changes during review | Notify affected tasks, update the contract version, and rerun affected individual and joint checks. |
| A worker is ready to publish but has not received the upstream change notification | The current group record holds the affected action pending. The worker refreshes prerequisites and evidence before publication instead of relying on its launch message. |
| A consumer PR receives a finding about the producer | Route the fix to the owner and check other affected consumers before resolving the shared issue. |
| Two chats would mutate the same checkout | Provide authorized isolation or serialize writers; separate chats do not count as isolation. |
| A prerequisite cycle blocks all tasks | Surface the cycle and resolve a viable order or shared prerequisite before dependent work. |
| Chat creation times out after submission | Reconcile the saved launch attempt; do not create a duplicate chat on a blind retry. |
| The coordinator is replaced while workers still run | Transfer coordination ownership, inspect existing assignments and results, and reuse workers rather than relaunching them. |
| A worker resumes while its original coordinator is still active | Confirm the current task assignment and prerequisites; resume the worker without transferring coordination. |
| One upstream PR merges with a changed revision | Refresh the merged state, downstream diffs and bases, and affected evidence before further publication or readiness claims. |
| Individual checks pass but combined verification is unavailable | Keep joint acceptance pending and report the limitation separately from individual PR status. |
| The host cannot create chats or isolate writes | Report the limitation and use an authorized fallback without claiming separate chats or parallel writes occurred. |
