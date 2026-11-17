# Reflect on work with agents

Use reflection to find recurring problems in how you and your agents work together. Run it alongside the [task workflow](WORKFLOW.md). A reflection run can propose a change for future work.

## Try one manual run

Start at the developer's request. Agree on the projects and sources to include, the period to review, and a private notes location. For a trial, suggest one day of work in the current project. Use the private storage rules in [SETUP.md](SETUP.md).

Use the task records, private task observations, chats, or excerpts the developer has approved for reflection. Check which project a chat belongs to before reading its messages when the host exposes that information. If you cannot verify the chat is in scope or the host cannot read it, use task records or ask for selected excerpts. Keep source excerpts, links, and notes in the agreed private location.

## Turn repeated friction into a proposal

1. Review new material in the agreed scope. Record each observation in the private notes with a source reference, what was expected, what happened, and the consequence. Keep a checkpoint for each source and a stable episode reference so the same episode is counted once even when it appears in several sources. Save the observations before advancing the checkpoint. Never advance past unread or inaccessible material. Report a source access issue when it requires the developer's action.
2. Wait for at least two independent episodes that point to the same problem and that one change could address. An isolated case stays in the notes. Check the current profile and project instructions before proposing a change.
3. Bring the developer at most one proposal per run. Include the evidence, the specific change and where it belongs, and what to look for in the next few tasks to see if it helped. Keep an open proposal in the notes and surface it again only when the evidence or proposal changes.

For example, if an agent runs the entire build on two tasks that only need a module check, look up the scoped command. Propose adding it to the project's verification instructions at the point where the agent chooses which checks to run. On later tasks, look for the agent choosing the scoped command when it fits.

For a manual run, tell the developer whether you found a proposal and mention any unavailable sources. The developer decides which proposals to adopt. Record that decision in the private notes. Apply a change to the profile or project instructions only after the developer approves that specific change and the project rules allow it.

For [subagent model selection](SUBAGENTS.md#improve-the-policy-through-reflection), compare similar assignments using their recorded settings, checks, escalations, and rework. Separate a poor selection from missing context, requirements, or tool access. Use measured resource data only when available; a single outcome or an agent's confidence does not establish comparative model quality. Apply the same evidence threshold and specific-change approval before adjusting model mappings or defaults.

## Enable a daily run if requested

Set up a once-daily run only with the developer's explicit approval. Approval of the daily settings in the setup proposal is sufficient. Confirm the project, sources and their scope, starting point, private notes location, run time, and time zone. Keep chat access within the specific approved recurring scope. If a scheduler or scheduled source access is unavailable, report the limitation and give the manual route.

Use one schedule per project profile. Assign one setup session as the owner of profile and schedule mutations; serialize other setup sessions through that owner, or use a scheduler-supported reservation or idempotency guarantee for the same stable profile identifier. If ownership cannot be established, keep schedule mutation pending. Before submitting a create, look up any existing schedule or unresolved attempt using the saved schedule reference or a stable identifier for the profile. Reuse the verified matching schedule, updating only settings the developer approved. Record the intended schedule and its lookup identifier in the profile's Reflection section before sending a create request. If the outcome is ambiguous, reconcile using that identifier and the scheduler. Retry only if you can establish that the earlier attempt did not create a schedule. If the scheduler cannot resolve the outcome or returns conflicting matches, report verification as pending.

The scheduled prompt must identify the original profile, the reflection instructions and their source revision, and the private state location. Each run reads the current profile before reading task or chat material. Proceed only while daily mode and the required source permissions remain explicitly approved. Use the current approved scope and recheck it before further reads or notifications when the profile changes; an old scheduler payload cannot expand or retain revoked access. If the profile or its authorization cannot be verified, stop source processing and report the blocker. Serialize manual and scheduled writes to the same notes and checkpoints so one run cannot overwrite another's progress or decisions.

Read back the saved schedule and verify its status, scope, cadence, and time zone. Record the schedule reference, actual status, and how to pause it in the profile's Reflection section. Report a schedule as active only after verification.

Each scheduled run reviews new material within the approved scope and updates the private notes. Save observations across runs and surface a new or changed proposal only when it meets the evidence threshold. Record the developer's decision in the private notes. Apply edits outside the scheduled run only after the developer approves the specific change and project rules allow it.

Keep scheduled reflection limited to reading approved sources, recording observations and decisions, and proposing improvements. It does not launch working chats, resume development tasks, publish changes, or change its own schedule or source permissions. The absence of a proposal does not require a notification; report material failures or required user action through the host's supported notification settings.

## Reflection verification scenarios

| Situation | Expected behavior |
| --- | --- |
| A task observation and a chat describe the same incident. The next run encounters the incident again. | Keep one episode in the notes. It does not meet the proposal threshold by itself. |
| The next run finds a second independent episode that one change could address. The following run has no new evidence. | Surface one proposal and keep it in the private notes. The following run does not repeat it. |
| A source cannot be read while another source is available. | Review the available source. Preserve the inaccessible source's checkpoint at the last reviewed point and retry it on a later run. |
| Daily mode is disabled, chat permission is narrowed, or the current profile cannot be read while an old schedule still fires. | Read the current profile first. Stop scheduled source processing when daily mode or authorization is unavailable; otherwise use only the current approved scope. |
| Two setup sessions attempt to enable reflection for the same profile. | Use one mutation owner or a scheduler-supported reservation/idempotency guarantee; do not issue competing creates. |
