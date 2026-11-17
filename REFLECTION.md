# Reflect on work with agents

Use reflection to find recurring problems in how you and your agents work together. Run it alongside the [task workflow](WORKFLOW.md). A reflection run can propose a change for future work.

## Try one manual run

Start at the developer's request. Agree on the projects and sources to include, the period to review, and a private notes location. For a trial, suggest one day of work in the current project. Use the private storage rules in [SETUP.md](SETUP.md).

Use the task records, private task observations, chats, or excerpts the developer has approved for reflection. Check which project a chat belongs to before reading its messages when the host exposes that information. If you cannot verify the chat is in scope or the host cannot read it, use task records or ask for selected excerpts. Keep source excerpts, links, and notes in the agreed private location.

For manual and scheduled reflection, use the [reflection notes template](templates/reflection-notes.md) when creating notes. Continue existing notes at their configured path. If a new layout is required to continue, follow the [filled record rules](UPDATE.md#update-filled-records) and preserve the checkpoints and proposal history.

## Turn repeated friction into a proposal

1. Review new material in the agreed scope. Record each observation in the private notes with a source reference, what was expected, what happened, and the consequence. Keep a checkpoint for each source and a stable episode reference so the same episode is counted once even when it appears in several sources. Save the observations before advancing the checkpoint. Never advance past unread or inaccessible material. Report a source access issue when it requires the developer's action.
2. Wait for at least two independent episodes that point to the same problem and that one change could address. An isolated case stays in the notes. Check the current profile and project instructions before proposing a change.
3. Bring the developer at most one proposal per run. Include the evidence, the specific change and where it belongs, and what to look for in the next few tasks to see if it helped. Keep an open proposal in the notes and surface it again only when the evidence or proposal changes.

When using saved episodes or resurfacing a proposal, check each supporting observation against the current run's approved sources. Record the original source and scope for each evidence reference. A note copied from a chat retains that source and its access restrictions. Count an episode only when evidence within the current scope independently supports it. If an open proposal no longer meets the threshold with eligible evidence alone, leave it in the private notes without surfacing it in that run. When resurfacing a proposal, use only details and conclusions supported by eligible evidence.

For example, if an agent runs the entire build on two tasks that only need a module check, look up the scoped command. Propose adding it to the project's verification instructions at the point where the agent chooses which checks to run. On later tasks, look for the agent choosing the scoped command when it fits.

For a manual run, tell the developer whether you found a proposal and mention any unavailable sources. The developer decides which proposals to adopt. Record that decision in the private notes. Apply a change to the profile or project instructions only after the developer approves that specific change and the project rules allow it.

For [subagent model selection](SUBAGENTS.md#improve-the-policy-through-reflection), compare similar assignments using their recorded settings, checks, escalations, and rework. Separate a poor selection from missing context, requirements, or tool access. Use measured resource data only when available; a single outcome or an agent's confidence does not establish comparative model quality. Apply the same evidence threshold and specific-change approval before adjusting model mappings or defaults.

## Change reflection settings

Use one owner per project profile for changes to reflection settings in the profile and its schedule. Setup, update, and disabling reflection use that same owner. Transfer ownership only after the prior owner has stopped writing and passed on any unresolved attempt. Before writing either, the owner rereads the current profile and scheduler state and compares them with the approved change. Reconcile intervening changes or uncertain results before continuing the affected operation. Preserve any newer choice to disable reflection or narrow its sources. If ownership cannot be established, keep the affected change pending. A scheduler reservation or idempotency guarantee helps prevent duplicate creation and does not serialize profile writes.

## Enable a daily run if requested

Set up a once-daily run only with the developer's explicit approval. Approval of the daily settings in the setup proposal is sufficient. Confirm the project, sources and their scope, starting point, private notes location, run time, and time zone. Keep chat access within the specific approved recurring scope. If a scheduler or scheduled source access is unavailable, report the limitation and give the manual route.

Use one schedule per project profile and follow the [shared write procedure](#change-reflection-settings) when enabling it.

Before proposing creation or reuse, [reconcile existing schedules](#find-and-reconcile-schedules). Reuse the verified match and update only approved settings. When the existing job predates the current profile format, [carry forward its approved settings](#carry-forward-approved-daily-settings). Recheck the search before any create. Create only when the scoped search establishes there is no matching job or unresolved attempt. Record the intended schedule and its lookup identifier in the profile's Reflection section before sending a create request. If the result is ambiguous, reconcile it using that identifier and the scheduler before retrying.

The scheduled prompt must identify the original profile, the reflection instructions and their source revision, and the private state location. Each run reads the current profile before reading task or chat material. Proceed only while daily mode and the required source permissions remain explicitly approved. Use the current approved scope and recheck it before further reads or notifications when the profile changes; an old scheduler payload cannot expand or retain revoked access. If the profile or its authorization cannot be verified, stop source processing and report the blocker. Serialize manual and scheduled writes to the same notes and checkpoints so one run cannot overwrite another's progress or decisions.

### Find and reconcile schedules

Use this lookup before creating, updating, or pausing a schedule. Start with the recorded schedule reference, stable profile identifier, and any unresolved attempt. Check the known project scope for legacy jobs without those identifiers. Use scheduler records and inspect candidate prompts for details that tie them to this installation, such as the canonical project or profile path and the configured task records or private notes path. A similar name alone does not establish a match. Use only authorized scheduler records and the relevant project scope.

Return a verified match, verified absence, or pending with the reason. Reuse a verified match even if the installation previously lacked a schedule reference. If the search is incomplete, several candidates may match, or an attempt remains uncertain, preserve the available evidence and keep creation pending until reconciled. Retry a create only once evidence establishes the prior attempt created nothing. An empty lookup by profile ID cannot exclude a legacy job by itself.

### Carry forward approved daily settings

Before replacing a legacy schedule prompt with one that reads the current profile, verify that the profile contains a confirmed daily mode and approved source scope. If those fields are missing, recover prior approval from available authorized records or obtain explicit confirmation for this project. The existing prompt can show configured sources and time. It does not by itself establish consent, especially for recurring chat access. Honor newer settings and revocations when older evidence conflicts.

Include the exact profile additions, confirmation evidence, and schedule edit in the setup or update proposal. After confirmation, save and reread the profile before switching the schedule. Verify that the new prompt resolves that profile with approved daily mode and source scope, and preserve its time, state paths, checkpoints, and active or paused status unless the user approves a change. If approval or the profile cannot be verified, keep the reflection migration pending. Report the existing schedule state and handle any revoked or unverified access through the [schedule access checks](#verify-access-after-a-schedule-change). A scheduler reporting an active job only verifies its scheduler state.

### Verify access after a schedule change

Use the [shared schedule lookup](#find-and-reconcile-schedules). Inspect the effective prompt and how it loads the profile, including legacy schedules with copied instructions or no source revision. Treat a schedule as compatible only when it is clear that its runs enforce the current mode and approved sources before reading them. A change to the profile alone cannot establish compliance for a legacy or unverified prompt.

When permission narrows or daily mode is disabled, follow the [shared write procedure](#change-reflection-settings) to save the approved change and use the authorized scheduler or source controls to enforce it. Verify that future runs cannot read the revoked sources. Use confirmed pausing or removal, confirmed source access restrictions, or a verified prompt that enforces the current profile. Check in-flight runs separately. A pause or prompt update may apply only to future runs. For any run that could still read a revoked source, verify that it ended, was cancelled, or can no longer access that source. If enforcement remains unknown, report that the old job or in-flight run may still read those sources, keep the change pending in the profile, and name the action needed to confirm it.

Read back the saved schedule and verify its status, scope, cadence, and time zone. Record the schedule reference, actual status, and how to pause it in the profile's Reflection section. Report a schedule as active only after verification.

Each scheduled run reviews new material within the approved scope and updates the private notes. Save observations across runs and surface a new or changed proposal only when it meets the evidence threshold. Record the developer's decision in the private notes. Apply edits outside the scheduled run only after the developer approves the specific change and project rules allow it.

Keep scheduled reflection limited to reading approved sources, recording observations and decisions, and proposing improvements. It does not launch working chats, resume development tasks, publish changes, or change its own schedule or source permissions. The absence of a proposal does not require a notification; report material failures or required user action through the host's supported notification settings.

## Reflection verification scenarios

| Situation | Expected behavior |
| --- | --- |
| A task observation and a chat describe the same incident. The next run encounters the incident again. | Keep one episode in the notes. It does not meet the proposal threshold by itself. |
| A legacy daily job has no profile identifier or saved schedule reference | Find it from verified project and state paths. Reuse the same job. If coverage or identity remains uncertain, leave creation pending. |
| An active legacy job uses confirmed sources but its profile has no Reflection section | Record and verify the confirmed mode and scope in the profile before replacing the prompt. If approval cannot be established, leave reflection migration pending even if the scheduler shows the job as active. |
| The next run finds a second independent episode that one change could address. The following run has no new evidence. | Surface one proposal and keep it in the private notes. The following run does not repeat it. |
| A source cannot be read while another source is available. | Review the available source. Preserve the inaccessible source's checkpoint at the last reviewed point and retry it on a later run. |
| Daily mode is disabled, chat permission is narrowed, or the current profile cannot be read while an old schedule still fires. | Read the current profile first. Stop scheduled source processing when daily mode or authorization is unavailable; otherwise use only the current approved scope. |
| A legacy schedule reads from a stored chat list and pausing it fails, or the pause succeeds while a run is active. | Saving the new profile alone does not establish that access stopped. Verify future executions and any in-flight run separately, and report remaining access as pending until enforced. |
| Setup and disabling reflection overlap for one profile. | Use one owner for profile and scheduler writes. An earlier daily approval cannot replace a newer off mode or narrower source scope. |
| A daily run finds an episode or open proposal supported only by a chat approved for one manual run. | Exclude that evidence from the scheduled run. Surface a proposal only if evidence from currently approved sources still meets the threshold. |
