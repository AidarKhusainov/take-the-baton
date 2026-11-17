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

Assign one working chat to each independently owned task by default. Reuse an existing eligible chat when possible. Give each mutable branch, PR, and shared artifact one owner. If tasks share a PR, designate one worker to integrate the candidate. Other workers provide findings or patches. The coordinator owns publication under the [group publication rule](#publish-through-the-coordinator).

Record planned publication targets in the [group record](templates/group.md#publication-targets-and-pr-mapping) as soon as they are known, before the first push. Use the remote repository and destination branch even when there is no tracker key or PR. Attach the PR reference when one exists. For a shared target, link all contributing tasks to the same entry and keep one publication owner. When the target changes, reconcile existing attempts and update its recorded owner and references before publishing.

## Start and coordinate working chats

Use the profile's actual host routes to create chats, send follow-up assignments, read results, and wait for progress. A working chat is a persistent user-visible chat; reviewer subagents within a task serve the independent review stage. Keep the host's existing delegation and review stages rather than adding another review loop for every message.

Give each working chat the applicable [subagent selection policy](SUBAGENTS.md) and project profile. It chooses model and reasoning settings for its own delegated assignments, using balanced priority by default and honoring task-specific constraints. Select separately for each assignment; a demanding group does not require maximum settings for every lookup. This policy does not override the host's rules or user settings for the persistent working chats themselves.

Before launching an assignment:

- Confirm that the recipient can access its project, original profile, task record, group record, and required change references. Give it the task outcome, boundaries, shared decisions, prerequisite versions, acceptance checks, workspace, and expected report. Include the [group publication rule](#publish-through-the-coordinator) in every assignment, including when the task uses an older workflow revision. Ask a reused worker to acknowledge the rule before treating it as an active group worker. Confirm any outstanding publication by the previous owner before sending an assignment that depends on the handoff.
- Use isolated working directories for simultaneous mutations, with the workspace route approved for that version-control system. Separate chats alone do not isolate files. For overlapping files, branches, shared generated outputs, or a shared working directory, serialize mutations under one owner. Verify the previous writer has stopped before reassignment. Do not apply Git worktree commands to Arc.
- Save the assignment and launch attempt in the group record before creating the chat. Include the stable assignment ID in the opening prompt. Save the returned host and chat reference, then verify the chat was created for the intended task. If creation has an uncertain outcome, reconcile the saved attempt using host records before retrying. If it cannot be reconciled, keep launch pending and continue independent work.

The coordinator collects each worker's progress and result through host reads or bounded waits. Use a follow-up in the same working chat for fixes, with a clear next action and relevant changed decisions. Use the [delivery procedure](#track-assignment-delivery) for each follow-up. Workers need their own applicable authorization for any outbound messages and can report in their own chat for the coordinator to read.

### Track assignment delivery

Give each distinct assignment a stable ID within the group. Before sending a follow-up, record the ID, destination host and chat, intended action and inputs, and delivery attempt. Include the same ID in the message and record the host's delivery reference or the worker's acknowledgment. Keep delivery status separate from work status. Workers record acceptance by ID before editing or running a side effect. If the same ID arrives again, return its existing progress or result without starting it again.

After a timeout or resumption, check the destination and the recorded attempt for evidence of delivery or acceptance of that ID. A failed tool response or a missing entry in an incomplete chat view does not prove non-delivery. If the assignment was delivered or accepted, track it in that chat while the worker can continue. Retry delivery to that chat with the same ID only when the earlier attempt definitely did not deliver. Keep unknown delivery pending and continue independent work.

Before reassigning an interrupted or uncertain mutation, confirm the previous worker can no longer perform it. Check the result associated with the assignment ID against the intended workspace, revision, or remote target. Reuse a completed result or assign only the remaining work. If the effect cannot be determined, repeat the specific action only when the project route guarantees it is safe to repeat. Otherwise keep that action pending. A stopped worker does not establish that its action never ran.

Use supported waits while actively coordinating, and give the user compact updates when a task finishes, becomes blocked, or needs a decision. Do not create a recurring automation merely to watch a particular task finish. A paused or ended coordinator chat is not a running background service: save the next action and explain any required resumption.

If chat creation, messaging, waiting, or isolation is unavailable, report the missing capability. Continue the supported parts in the current chat, use an authorized subagent, or prepare a manual handoff. Mark separate-chat coordination or parallel mutation pending when it cannot be performed; do not report a subagent or an unstarted handoff as a created working chat.

## Propagate changes and review findings

When a task's requirement, contract, implementation, PR base, or published revision changes:

1. Record the new version and inspect its outgoing dependencies. Identify which other tasks and joint checks are affected; preserve unaffected work. Mark affected publication and readiness actions pending in the group record before sending follow-ups, so delayed messages cannot leave them eligible on old evidence.
2. Send each affected owner the changed decision or exact revision and required next action. Work that needs an unavailable prerequisite remains pending; independent work can continue.
3. For dependent branches or PRs, use the project's authorized update route. Inspect the outgoing diff against its intended base so shared changes appear where intended and unrelated or already integrated changes are not accidentally republished. History rewrites still need their applicable authorization.
4. Mark affected checks and reviews stale using the [evidence rules](WORKFLOW.md#decide-which-verification-results-still-apply). Recheck the current individual changes and the affected combination before reporting them ready.

Apply a review finding to its owning task and shared contract. A finding reported on a consumer PR may require a fix in a shared producer; check other consumers before closing the group-level issue. Record a disposition and evidence without blindly copying the same patch to every PR. Keep each task's assigned independent reviewer through the normal [review loop](WORKFLOW.md#5-review-and-resolve-findings).

### Publish through the coordinator

The coordinator is the sole publisher for grouped work and the sole writer of group conditions that govern its publication. This rule applies when adding or resuming a task on an older workflow revision. Give workers the rule and group record reference directly. Workers prepare and hand off the exact reviewed candidate and verification evidence. They do not push grouped changes, open or update grouped PRs, or mark them ready. An earlier task assignment or permission to publish does not designate a second publisher. Before adopting a PR or reusing a worker, confirm that previous publication activity has stopped and reconcile any outstanding attempts. If authority, access, or handoff remains unresolved, the affected publication stays pending.

When adopting or transferring a task, save and read back the handoff in the original shared task record before dispatching grouped work. State directly in its existing PR and publication status that earlier worker publication permission for this task is superseded and only the authorized coordinator may publish it. Record the group and coordinator references, applicable authorization, and effective handoff. Preserve earlier permission as history with its superseded status. A link to the group alone is insufficient for a workflow that predates group rules. If the shared record cannot be updated or read back, keep the publication handoff pending.

Check the installation's known startup routes that can work on or publish the adopted task, including separate rules in other worktrees. A route is ready when it applies the [publication owner check](WORKFLOW.md#verify-the-publication-owner), or when the coordinator verifies that it resolves the same up-to-date task record and honors the handoff before publication for both resumed and ordinary requests. An independently verified project control that prevents that route from publishing also resolves the risk. Updating the shared profile or obtaining an acknowledgment from one worker does not verify a different route. If a known relevant route is stale, inaccessible, or its behavior cannot be verified, record why in the group and keep the affected publication pending until the route is verified or prevented from publishing. Continue preparation, checks, and unrelated tasks that can proceed independently.

For each publication action or report of readiness, the coordinator records the target, authorized action, exact candidate and relevant remote revisions, current shared contract and prerequisite versions, and matching verification and review evidence. Inspect current records and remote state before acting. Treat a newly known decision or prerequisite change as a reason to recheck the evidence. The same coordinator processes changes to the governing group conditions and the check, request, and outcome of publication in sequence. Hold affected actions pending when conditions change. Do not dispatch publication as a background worker action or release the publication slot to a replacement coordinator while the outcome is unknown. For an uncertain remote result, reconcile the attempt and current remote state before retrying that action or publishing a dependent change. Record the observed outcome, then recheck any evidence affected by intervening external changes.

After a PR merges or its base changes, refresh the remote state and reconsider dependent PR bases, remaining diffs, requirements, and joint checks. Use actual merged revisions rather than assuming a previous head was integrated unchanged. Human merge decisions and project-specific deployment rules continue to apply.

## Verify and report the group result

Run the relevant checks for each task and verify the shared acceptance criteria against a recorded combination of revisions, dependencies, and configuration. Use the project's approved integration environment or accessible equivalent tree. Independent review must cover the current implementation diffs; use the existing reviewers to examine affected boundaries and the shared result. Green checks on separate PRs do not establish that the combination works.

Record individual PR requirements separately from group requirements. A PR may be eligible for a draft or other authorized action while dependent tasks remain pending. If joint verification cannot run, keep that evidence pending and report what is missing; do not label the whole group complete solely because every worker finished.

In the coordinator chat, show a compact table with each task, its PRs if any, prerequisites, status, and next action or blocker. Bring shared decisions to the user here. Finish when the requested group outcome and its applicable checks are satisfied, or report the precise pending requirements. Reaching the requested outcome of opening verified PRs does not imply merge or deployment.

## Resume coordination

Record the source URL and exact Take the Baton revision when starting coordination. Save the group record before handing off or pausing, with the coordinator, assignments, outstanding launch attempts, decisions, task and PR references, exact revisions, check coverage, and next actions. Workers update their own task records; one coordinator owns updates to the shared group record.

On resumption, use the workflow revision recorded for the group, including after an installation update. Each task retains its own recorded revision. For legacy records and intentional migration, use the [task resumption rules](WORKFLOW.md#resume-in-any-session) and [UPDATE.md](UPDATE.md).

When a worker resumes its own task, follow the [task resumption entry check](WORKFLOW.md#check-group-membership-before-resuming) before loading the task's recorded revision. Confirm its existing assignment and current prerequisites and carry the [group publication rule](#publish-through-the-coordinator) into the resumed session, including when it starts directly at the user's request. A running coordinator does not block an unchanged valid worker assignment.

When resuming or replacing the coordinator, resolve the original group record and profiles, then refresh existing chats, tasks, and PRs. Confirm the old coordinator is no longer issuing assignments or publishing before transferring ownership. If ownership is uncertain, resolve it before dispatching mutations. Reuse reachable workers and reviewers. Reconcile launches, follow-up deliveries, and publications with uncertain outcomes before retrying them. Replace unavailable sessions under the [resumption rules](WORKFLOW.md#resume-in-any-session), preserving decisions and evidence. Ask only about material changes or missing authorization.

## Verification scenarios

Walk through these scenarios against the host routes and project rules. A documentation walkthrough does not prove live chat, VCS, or CI integration.

| Situation | Expected behavior |
| --- | --- |
| Three task descriptions, no PRs, one shared contract | Record tasks and the contract, register only if required, and start authorized working chats for work whose prerequisites are satisfied. |
| One task needs two PRs; two tasks share another PR | Keep task-to-PR mappings and a single owner per PR; verify each PR and the shared result. |
| The user asks only for investigation | Coordinate research to that outcome; do not implement or publish merely because the group has several tasks. |
| A shared contract changes during review | Notify affected tasks, update the contract version, and rerun affected individual and joint checks. |
| A worker has an old task revision and earlier permission to publish | Confirm handoff before using the worker. Give it the group publication rule and have it hand off the candidate. The coordinator alone can publish grouped work. |
| The contract changes after a worker hands off a verified candidate | The coordinator records the updated conditions and holds the affected publication pending. It verifies the candidate against those conditions before publishing. Changes to group conditions and publication run under the same owner in sequence. |
| A publication request times out while a new contract decision is waiting | Keep the action pending. Reconcile the remote result before a retry or dependent publication. Record the new conditions and reassess the evidence before the next action. |
| A consumer PR receives a finding about the producer | Route the fix to the owner and check other affected consumers before resolving the shared issue. |
| Two chats would mutate the same checkout | Provide authorized isolation or serialize writers; separate chats do not count as isolation. |
| A prerequisite cycle blocks all tasks | Surface the cycle and resolve a viable order or shared prerequisite before dependent work. |
| Chat creation times out after submission | Reconcile the saved launch attempt; do not create a duplicate chat on a blind retry. |
| A follow-up times out after the working chat accepts the assignment | Read the recorded ID in the destination. Keep tracking the accepted assignment. If acceptance cannot be established, leave delivery pending. The worker executes a given ID once. |
| A worker stops after a timeout and the change it was assigned is already present | Reconcile the assignment with the actual workspace or remote target. Carry forward the completed result and assign only remaining work. |
| The coordinator is replaced while workers still run | Transfer coordination ownership, inspect existing assignments and results, and reuse workers rather than relaunching them. |
| A worker resumes while its original coordinator is still active | Confirm the current task assignment and prerequisites; resume the worker without transferring coordination. |
| The user directly resumes an old grouped task by record path or tracker key | Resolve the task and group in the current workflow before loading the old task revision. Preserve coordinator-only publication without relying on an earlier handoff message. If the known group record is unavailable, leave publication pending. |
| Two worktrees share a profile, but one is inaccessible and pins a workflow that predates groups | Save the publication handoff in the shared task's existing status. Keep the affected publication pending despite the first worktree and profile being updated. When the old route returns, verify its publication owner check, its use of the current shared record, or its inability to publish before clearing the hold. |
| An ordinary request asks to fix a grouped PR from another worktree | Check ownership by PR and its source repository and branch before publication. A route that checks only explicit resumption does not clear the hold. If the shared record cannot be reached, leave publication pending. |
| A task from a description has a planned remote branch but no tracker key or PR | Match the remote repository and destination branch against the planned group target before the first push. The coordinator remains the publisher. |
| A newly added task references a key that is missing from the existing shared PR entry | Resolve ownership using the PR and its source repository and branch. Link the task to that target without changing the publication owner. |
| An ordinary PR update has no group or handoff in the applicable shared records | Proceed under the ordinary publication rules after verifying the lookup. |
| One upstream PR merges with a changed revision | Refresh the merged state, downstream diffs and bases, and affected evidence before further publication or readiness claims. |
| Individual checks pass but combined verification is unavailable | Keep joint acceptance pending and report the limitation separately from individual PR status. |
| The host cannot create chats or isolate writes | Report the limitation and use an authorized fallback without claiming separate chats or parallel writes occurred. |
