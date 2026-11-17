# Set up Take the Baton

Use this guide in the work project where the user asked to set up Take the Baton. Read [WORKFLOW.md](WORKFLOW.md) and [the profile template](templates/profile.md) from the supplied source. Keep the work project and the source of these instructions separate.

## Required setup sequence

1. Identify the current project or module and inspect it using read-only actions.
2. Ask the [applicable activation questions](#choose-how-to-start-the-workflow) and [offer reflection](#offer-reflection) for this project, then wait for the user's answers. These choices can be collected together. [Configure subagent selection](#configure-subagent-selection) with balanced priority by default in the same proposal. Use confirmed answers for this project. Reuse choices from another project only when the user explicitly asks to copy them to this project.
3. Show the exact proposed changes and wait for [explicit confirmation of that proposal](#confirm-one-proposal) before creating or editing setup files or directories. A request to set up Take the Baton, answers to setup questions, and permission to read chats each serve a different purpose. File changes require confirmation after the proposal is shown.

## Setup checklist

Use this checklist throughout setup.

| Item | Completion criterion |
| --- | --- |
| Project scope | The exact project or module path and its applicable instructions are identified. |
| Private storage | The agreed private location for both the profile and task records is confirmed. Inside a checkout, verify that the intended paths are untracked and the local exclusion applies. |
| Profile | A saved profile has been read back and contains the selected paths, commands, and tool routes. |
| Installation registry | A verified entry locates this installation in the private registry, or a pending registration and the manual lookup path are reported. |
| Activation | The selected mode and scope are recorded, or both are marked **Not applicable** for manual-only setup. The instruction location and profile lookup are verified, or the remaining step or manual route is reported. |
| Subagent selection | The priority, constraints, supported settings and evidence, and fallback are recorded in the profile. |
| Reflection | The approved mode and scope are recorded. Any daily schedule or requested pause is verified, or the manual route and remaining limitation are reported. |
| Tools and project rules | Each action has a recorded access status and any required fallback. Branch names and descriptions, commit subjects and bodies, PR titles and templates, and requirements before publication and merge are recorded, with any unavailable or inapplicable items identified. |
| Code checks | Existing hooks, linters, formatters, validators, and CI checks are recorded with their triggers. Any recommendations for gaps are listed separately. |

Setup is complete when project scope, private storage, and the saved profile meet their criteria. Report a complete setup with outstanding registration, activation, subagent selection, reflection, tool, or check limitations as ready with limitations. A profile supplied for manual saving leaves setup incomplete. For an existing installation whose instructions need a newer revision, use [UPDATE.md](UPDATE.md).

## Inspect the project

1. Identify the project or module from the current directory. Read its applicable instructions, README, build entry points, and version control metadata. Keep discovery scoped to that project.
2. Read the existing `.take-the-baton/profile.md` or the profile path supplied by the user or configured in the activation instructions. Keep choices the user confirmed for this project and flag conflicts with current project rules or access. Use the profile's confirmation entry as evidence for the approved values it lists when the project or module matches. Other evidence, such as an explicit instruction from the user for this project, can also establish confirmation. If a profile or activation rule only describes an existing choice, ask about it.
3. Inspect connectors, CLI tools, and capabilities already exposed to the agent. Use scoped read-only checks where available. Distinguish a detected tool from verified access to the intended project. Establish write access through read-only permission information when available.

Identify a route for each action in the profile template. A single tool can cover several actions. Record the actual command or tool, working directory or destination, access status, and fallback. Use `verified`, `unverified`, or `unavailable` for tool access. Use `manual` for a deliberate handoff.

For [task groups](GROUPS.md), inspect host support for persistent working chats, follow-up messages, result reads and waits, launch reconciliation, and workspace isolation for the project's VCS. Record the routes and limitations in the profile without starting chats or creating workspaces during setup. Keep any group records in agreed private storage accessible to the coordinator and authorized workers; verify protection for these paths before use. A group request supplies its own task scope and authorizations.

Reuse tools that fit the project rules. Where a service is unfamiliar or unavailable, propose a manual handoff or describe the adapter that would be needed. Direct required sign-in to the service's normal interface and keep credentials out of the profile.

Find existing hooks, linters, formatters, validators, and CI checks. Record their commands or configuration, when they run, and which changes they cover. Also find the project's conventions for branch names and descriptions, commit subjects and bodies, and PR titles and templates. Record which checks or reviews are required before pushing, opening a PR, or marking a draft ready. Separately record what must be complete before merge, including reviews and CI that need an open PR. For required PR CI, record whether each check must cover the head alone or the base and outgoing change together. Keep personal check commands separate from required team checks.

Record the project's existing decision sources in the profile when they are known. Add a private decision journal only when the developer asks to keep decisions across tasks.

If check coverage or automation has a gap, propose up to three improvements that fit the project. For each one, say what it catches, when it would run, and whether it needs a local change or a team configuration change. Keep recommendations separate from discovered checks. Apply hook, tool, or CI changes only when separately requested and allowed by project rules.

## Recover context from recent chats if approved

Before proposing the profile, use this prompt in the user's language when offering chat review. Keep the option codes. Reuse a previous answer only if it covers the project and chats you intend to read. If the user asked to copy another project's choices and you need its chat history, identify that source project in the permission request.

> May I review up to ten of the most recent chats in `<project or module>` to find confirmed decisions, useful commands, and unfinished tasks?
>
> - **H1. Allow.** Review the ten most recent project chats, or all of them if there are fewer.
> - **H2. Skip.** Continue setup without reading chats.
> - **H3. Selected chats only.** Review the chats or excerpts I identify.

Confirm permission and scope before reading messages. For `H3`, ask for the selection if it is missing. Review more than ten only if the user agrees to a broader scope. Verify that each chat belongs to the selected project or module using project or workspace information from the host. If the host cannot read or reliably identify the chats, use task records or ask for selected excerpts within the approved scope.

Look for confirmed decisions, useful project commands, and unfinished work. Verify project facts against current sources and distinguish confirmed decisions from suggestions or assumptions. Show the relevant findings and their sources in the setup proposal, including how many chats were reviewed and any access gaps. Propose only durable, relevant entries for the profile or an existing private decision journal. Surface unfinished task references in the report when reviewing chats for the current project. When reading another project's chats solely to copy setup choices, carry forward only the confirmed choices the user asked to copy. Keep source excerpts and chat links within the agreed private scope.

## Choose how to start the workflow

Before asking about activation, check which instruction locations the host can load for this project and how they can find the private profile. If only manual startup is available and the user has not requested a feasible shared team rule, skip the activation questions and show the [manual prompt](#manual-startup) with the setup proposal. In the profile, mark the active mode and scope **Not applicable**, record `manual` as the route, and give the profile path used in the prompt. Retain any previously confirmed activation preferences in the confirmation entry so they remain available if the host later supports them.

Apply choices explicitly given for the current project in the current request before considering previous choices. For supported routes, ask every applicable question that still needs an answer for the current project. Ask them together when both apply and wait for the answers before preparing the proposal. Use the user's language, keep the order and option codes, and offer `эстафета` in Russian and `baton` otherwise as the default keyword for option 1B.

- **New setup.** Ask about the choices still missing for this project. Preferences from memory, global instructions, and other projects' profiles or chats do not supply answers for this project on their own.
- **Explicit reuse from another project.** When the user asks to copy choices from a named or otherwise unambiguous project, check its matching private profile at the configured or default path, or at a path the user supplies. Limit source discovery to the requested choices. Use the confirmed choices covered by the request and identify the source and the choices carried over in the proposal. Resolve storage and tool routes for the current project. Ask separately for permission if you still need chat history. If chat access is denied or unavailable, use the source profile or other accessible evidence and ask only about choices that still lack confirmation or are unclear or incompatible. If the source profile cannot be located and confirmation is still missing, ask for its path or the missing choices.
- **Rerun in the same project.** Reuse choices previously confirmed for this project and ask about any choices that are still unanswered or affected by a conflict with the current setup. A matching profile confirmation entry lets a new session reuse those choices without reopening the setup chat.

> **1. When should Take the Baton start in this project?**
>
> - **1A. By default.** Use it for development task requests in this project.
> - **1B. By keyword.** Use it when I start a request with `baton`. I can supply a different keyword.
>
> **2. Who should this setup apply to?**
>
> - **2A. Just me.** Use personal instructions to find my private profile.
> - **2B. My team.** Prepare a shared project instruction for how each developer finds their own private profile.
>
> Reply with the requested choices, for example `1A, 2A` when both questions apply. To choose another keyword, include it with `1B`.

Treat the answers as preferences for the proposal. Confirm any file changes after showing the proposal. Keep permission to read chat history separate.

Find an instruction location that the host already loads for the selected project. Scope the rule to that project or module, and identify the profile and workflow source. Follow existing shared project rules and surface any conflict with the requested mode or scope. In default mode, start the workflow for development task requests. In keyword mode, match the chosen keyword at the start of the user's own message, ignoring case and allowing whitespace or punctuation after the keyword. Either mode can also start when the user explicitly asks to use Take the Baton.

For explicit task resumption, the startup rule must start with the [group check in the current installed workflow](WORKFLOW.md#check-group-membership-before-resuming). Resolve the original task record first and apply any group publication rules before loading its recorded task revision. For group resumption, use the group record and its recorded workflow revision. For a request to update the installation, follow [UPDATE.md](UPDATE.md) from the requested source before starting any task workflow.

- **Personal setup.** Propose a rule in the user's existing personal instructions, scoped to the project. Point it to the agreed profile path and use the source URL and revision stored in the profile.
- **Team setup.** Show the proposed change to the shared project instructions. Give the team a common way to find each developer's private profile, such as the same project-relative ignored path or a personal pointer for external storage. Keep personal paths and private profile contents in personal storage. Apply the shared instruction edit only if the user approves that exact edit and project rules allow it.

### Manual startup

Fill in the source URL and revision and the paths needed for the request.

**Start work on a task**

> Use Take the Baton for this project. Read the workflow from `<source URL and revision>` and the profile at `<profile path>`. Work on `<task description or tracker key>`.

**Resume from a record**

> Resume Take the Baton from `<original task record path>`. Read the group check in WORKFLOW.md from `<current installed source URL and revision>` before loading the recorded task revision. Apply the group's publication rules if the task belongs to a group. If the task has no recorded source, use `<original source URL and revision>` for the remaining task steps.

**Resume by task key**

> Resume Take the Baton for `<task key>` using the original profile at `<original profile path>`. Follow the record lookup and group check in WORKFLOW.md from `<current installed source URL and revision>` before switching to the original task's workflow revision.

**Coordinate related tasks**

> Use Take the Baton for this project. Read WORKFLOW.md and GROUPS.md from `<source URL and revision>` and the profile at `<profile path>`. Coordinate `<task keys or descriptions>` from this chat. Create working chats and send them assignments. Work toward `<requested outcome>` and bring shared decisions here.

**Resume a group**

> Resume Take the Baton coordination from `<original group record path>`. Use the workflow source and revision recorded for the group and reuse its original profiles and existing working chats.

If a legacy group record has no source revision, use its verified original source reference or follow the [update guide](UPDATE.md#prepare-one-update-proposal) to resolve compatibility.

## Configure subagent selection

Use [the subagent selection policy](SUBAGENTS.md). Propose `balanced` when the user has no explicit project preference. In the same setup proposal, offer `quality` and `economy` as optional changes. Use the existing proposal confirmation without an extra question about priority. On rerun, keep confirmed project preferences, including any fixed model, reasoning effort, or budget, and honor any explicit new choices for this project. Surface a conflict if the current host cannot honor a confirmed constraint.

Inspect current tool schemas and any read-only model catalog the runtime exposes. Record supported combinations of delegation surface, model ID, and reasoning effort with their evidence and date. Include model-specific defaults when exposed and the limits on overriding settings at launch or continuation, including any requirement for fresh context. Use the available evidence to map the policy's economical, standard, and deep-analysis options. Mark mappings that cannot be verified as `unverified`. Avoid test launches for model discovery.

The approved project profile guides selection for subagents during authorized delegation without a separate confirmation for each selection where the host allows it. The profile leaves global and working-chat settings as configured. If a working-chat launch requires a user-specified model for an override, apply an override only when the user supplies that model. Handle model and effort fallback separately: preserve a supported explicit value and inherit only the unsupported dimension if its compatibility and required constraints can be established. Unknown comparative mappings do not invalidate verified supported choices. If a required inherited value cannot be verified, keep the affected assignment pending or use a separately authorized compatible route. Report a capability or constraint that the available route cannot satisfy.

## Offer reflection

After resolving activation, including manual-only startup, offer reflection in the user's language. Reuse the choice already confirmed for this project on a rerun unless the user requests a change or a conflict needs a decision.

> **R1. Daily.** Review new material once a day and surface a proposal when evidence supports one.
>
> **R2. Manual.** Run reflection when I ask.
>
> **R3. Off.** Skip reflection.

For daily mode, propose the current project's task records and private task observations, where configured, as sources, starting with new material after setup. Show the project scope, sources, starting point, private notes path, run time, and time zone. Check scheduler availability and access from scheduled runs before proposing a schedule. If scheduled runs cannot access the approved sources or the host lacks a scheduler, show the manual route and explain the limitation. For manual mode, agree on the scope, sources, period, and notes path at each run unless already approved for that run.

Include a private observation location and capture scope in the proposal if future tasks should record material for reflection even without a full task record. The [task capture step](WORKFLOW.md#capture-material-for-reflection) uses only that approved location and scope. Keep the selected mode separate from the actual schedule status.

For daily setup and reruns, [reconcile existing schedules](REFLECTION.md#find-and-reconcile-schedules) before proposing creation. Include any verified legacy match and [profile settings to carry forward](REFLECTION.md#carry-forward-approved-daily-settings) in the same proposal. If the search cannot rule out a duplicate, report scheduling as pending and finish independent setup steps.

Ask for explicit recurring permission before including chats in a daily schedule. Identify which project and chats it may read on future runs. Permission to recover context during setup or to read chats for a manual run covers only that occasion. Keep all excerpts, links, and notes in the agreed private location.

## Confirm one proposal

Include the [private registry](UPDATE.md#private-installation-registry) path and the proposed entry in the same proposal. Keep the registry outside work checkouts. Reuse the entry for the same installation and add any newly verified startup rule or location, including a separate rule in the current worktree. Preserve the other known routes. Setup confirmation covers the displayed registry entry together with other approved edits.

Keep the profile and task records private. Use `.take-the-baton/profile.md` and `.take-the-baton/tasks/` in the selected project only when the directory is untracked and a local VCS exclusion can be verified. Check for any tracked or staged files under that path. For Git, resolve the local exclude file with `git rev-parse --git-path info/exclude` and match the actual directory relative to the repository root, including any module prefix. A tracked or staged path, or an exclusion that cannot be verified, calls for an agreed private location outside the checkout for both the profile and task records. Preserve existing tracked or staged files.

If the workflow registers tasks, record where this developer's registration records live for the project and tracker destination. One worktree can use its task directory. When setting up another worktree, reuse the original private registration records or the agreed coordinator that can reconcile prior attempts. Record how a new session can look up an original task record by tracker key or URL. Propose a separate private location only if it is needed and preserves access to earlier attempts. If the route cannot be verified, report registration as pending.

For reflection notes and optional task observations, use the same private storage rules as for task records. Include any private reflection paths and scheduler creation, update, or pause in the exact setup proposal. Confirm the reflection settings and scheduler changes with the rest of the proposal.

If using a private decision journal, keep it in the agreed private location. For an in-project journal, verify that its path is untracked, unstaged, and covered by the local exclusion before writing. If that cannot be verified, agree on a private path outside the checkout.

Fill in the [setup proposal form](templates/setup-report.md#proposed-setup) in the user's language. Include the proposed storage location in the same report. Show the exact file edits or link to the proposed diff. In the proposed profile's confirmation entry, list the project or module path and the specific mode, keyword if used, and scope that the user is being asked to confirm. Write that entry only after the user approves the displayed proposal. For copied choices, the approval confirms them for the destination project. For manual-only setup with no confirmed activation preferences, use **Not applicable** for the confirmation entry. Include unresolved tool, access, or verification limitations. Keep check recommendations separate from the changes being approved.

Apply the proposed changes after `S1` or an equivalent explicit confirmation. For `S2`, show the revised proposal and wait for the user's confirmation before applying the changes.

## Save and check

Use the [shared procedure for changing reflection settings](REFLECTION.md#change-reflection-settings) before writing the profile or schedule when setup changes reflection or rewrites its settings. Preserve the current settings when applying unrelated profile edits.

After confirmation, apply any agreed local exclusion and verify it before writing private files. In Git, check both tracking status and whether the intended profile and task paths are ignored.

If the exclusion fails, stop before writing the profile or activation instructions. Show the revised proposal for storage outside the checkout, including changed paths and instructions and any exclusion edit already made. If this setup added an exclusion entry, include its removal in the revised proposal. Wait for explicit confirmation before applying the revised changes. After confirmation, remove only the entry added by this setup and preserve unrelated entries. If you cannot identify the addition safely, leave the exclusion file as it is and report the remaining edit.

Preserve existing content and record the source URL and revision or tag when available. Read the profile back and check the paths, routes, and approved subagent preferences against the project. Apply the agreed activation instruction edit, if any, and preserve the existing instructions. Use read-only checks to verify the instruction location and profile lookup. If startup behavior can only be confirmed in a new session and has yet to be checked, report that verification as pending.

For an approved daily mode, use [the scheduler reconciliation steps](REFLECTION.md#enable-a-daily-run-if-requested). Save and verify approved settings in the profile before switching a legacy prompt to the current-profile checks. Record the actual schedule status in the profile's Reflection section. If no daily run can be scheduled, give a copyable prompt for a manual run. When switching to manual or off mode or narrowing source access, follow the [schedule access checks](REFLECTION.md#verify-access-after-a-schedule-change). Reconcile existing schedules and unresolved create attempts, including legacy prompts. Verify that the approved controls took effect for future and in-flight runs and record any unresolved access as pending.

After saving and verifying the profile and applicable source references, save and read back the approved registry entry. Include manual installations and use the same registry across this user's projects on the host.

Fill in the [setup result form](templates/setup-report.md#setup-result) in the user's language. Use one line per checklist item with its status and a brief confirmation or reason.

Use **Done** for changes made, **Verified** for confirmed facts, **Proposed** for suggestions awaiting a decision, **Pending** for blocked or manual steps, and **Not applicable** with a reason when an item does not apply. Keep suggestions marked **Proposed** separate from discovered checks. For default mode, show an ordinary task request. For keyword mode, put the selected keyword first. For pending or manual startup, give the full manual prompt. Report partial changes accurately. If the profile could not be saved, return its completed contents and intended path. Ask a follow-up only when the user needs to act to finish setup. The confirmation covers the displayed setup changes, including any approved reflection schedule change. Workflow actions follow the user's task request and the project's approval rules.

On rerun, compare the existing profile, registry entry, storage protection, activation instructions, subagent settings and available capabilities, reflection configuration and schedule, tools, and rules. If no changes are needed, report the current checklist status. If changes are needed, present them together and preserve confirmed preferences.

## Setup verification scenarios

Start each scenario with a host that supports personal and team activation, unless the row says otherwise. Project A has a user-confirmed personal setup triggered by `эстафета`. Project B has no confirmed choices unless the row supplies them.

| Request or situation | Expected behavior |
| --- | --- |
| “Set up Take the Baton for Project B.” | Ask questions 1 and 2 together and wait for the answers. Show the exact proposal. After `S1`, verify the saved profile records the approved choices for Project B. |
| “Set up Project B the same way as Project A.” Chat access is denied or unavailable, and Project A's profile records its confirmed choices. | Carry over keyword activation with `эстафета` and personal scope from the profile without reading chats or re-asking the confirmed questions. Identify Project A and both choices in the proposal. Use Project B's own profile and task-record paths. After `S1`, record confirmation for Project B. |
| “Set up Project B with the same activation mode and keyword as Project A.” | Carry over keyword activation with `эстафета` and ask question 2 about scope. |
| Project B can use a team rule but cannot use Project A's personal rule. The user asks to copy Project A's setup. | Explain the scope conflict and ask how to proceed. Carry over the compatible choices covered by the request. |
| “Set up Take the Baton for Project B. Use it by default.” | Record option 1A for Project B and ask question 2. |
| Rerun setup for Project A in a new session with no access to the original chat. Its profile records its confirmed choices and no changes are needed. | Reuse the recorded choices, report the existing setup and leave the files as they are. |
| “Switch Project A to default startup.” | Use option 1A and retain confirmed personal scope. Show the proposed changes and wait for confirmation. |
| Rerun setup for Project B with an existing profile but no evidence that the user confirmed its choices. | Ask questions 1 and 2. Treat the profile as a description of the current setup. |
| Only manual startup is available for Project B. | Skip the activation questions. Show the manual startup prompt and the profile and storage changes, with mode and scope marked **Not applicable** and route set to `manual`. |
| The local exclusion fails after the user confirms a proposal with in-project storage and the agent adds an entry. | Show the entry already added and its proposed removal along with the external storage changes. Wait for fresh confirmation, then remove only that entry and verify unrelated entries were preserved. |
| Manual-only startup is available and the user chooses R1, but the host has no scheduler. | Offer reflection, report daily mode with a manual fallback, and show how to run it on demand. |
| The user chooses R1 and granted only one-time setup chat access. | The approved schedule uses the project's task records. Include recurring chat access only with separate permission for that scope. |
| R1 was confirmed and schedule creation returned an ambiguous result. | Reconcile against the scheduler and saved attempt. If unresolved, report the status as pending and avoid submitting another create. A rerun reuses a single verified matching schedule. |
| A daily setup rerun finds a legacy job with only project or state paths in its prompt. | Use the scoped lookup before creating. Reuse the verified match and save approved settings in the profile before switching the prompt. When the search cannot rule out a duplicate, keep creation pending. |
| The user changes from daily to R2 or R3, including after an unresolved create or failed pause. | Save the confirmed mode, reconcile the schedule, and verify its pause or absence. Report shutdown pending while its state is unknown; existing runs check the current mode before reading sources. |
| Group coordination is supported but workspace isolation is unavailable. | Record chat routes and serialized mutation fallback. Do not launch chats or create workspaces as a setup check. |
| Setup is rerun for a verified manual installation that has no registry entry. | Show the entry in the setup proposal and record it after verification. Preserve the manual startup choice. |
| Setup is rerun from a second worktree with its own startup rule and the same installation profile. | Add the verified rule to the existing installation entry. Retain the other worktree's rule and its last verified revision. |
| New project setup has no subagent preference. | Propose `balanced` without another question. Offer `quality` and `economy` in the same proposal and save the approved choice after confirmation. |
| A rerun finds a confirmed fixed model or effort, or the user gives an explicit new choice for this project. | Preserve the confirmed choices and apply only the requested change. Flag unsupported constraints and keep the recorded choices until the user approves a change. |
| The delegation surface exposes partial overrides or cannot expose a current model catalog. | Mark unverifiable mappings `unverified`, retain supported explicit model or effort choices, and identify a compatible fallback for each unsupported dimension. Keep unmet required constraints pending. Skip discovery launches. |

In each new-project scenario, also offer reflection if its mode has not been confirmed. On reruns, reuse the confirmed reflection choice and reconcile an existing schedule rather than creating another.

For every scenario that proposes a write, check that the agent shows the exact changes and waits for `S1` or an equivalent explicit confirmation of the displayed proposal. Verify that the profile, task directory, activation instructions, and any local VCS exclusion stay untouched while the proposal is pending. Test chat access separately. The agent must obtain separate permission before reading chats, including when the user asks to copy setup choices from another project.

For the run instructions, see [Reflect on work with agents](REFLECTION.md).
