# Set up Take the Baton

Use this guide in the work project where the user asked to set up Take the Baton. Read [WORKFLOW.md](WORKFLOW.md) and [the profile template](templates/profile.md) from the supplied source. Keep the work project and the source of these instructions separate.

## Setup checklist

Use this checklist throughout setup.

| Item | Completion criterion |
| --- | --- |
| Project scope | The exact project or module path and its applicable instructions are identified. |
| Private storage | The agreed private location for both the profile and task records is confirmed. Inside a checkout, verify that the intended paths are untracked and the local exclusion applies. |
| Profile | A saved profile has been read back and contains the selected paths, commands, and tool routes. |
| Activation | The selected mode and scope are recorded. The instruction location and profile lookup are verified, or the remaining step or manual route is reported. |
| Tools and project rules | Each action has a recorded access status and any required fallback. Branch names and descriptions, commit subjects and bodies, PR titles and templates, and requirements before publication and merge are recorded, with any unavailable or inapplicable items identified. |
| Code checks | Existing hooks, linters, formatters, validators, and CI checks are recorded with their triggers. Any recommendations for gaps are listed separately. |

Setup is complete when project scope, private storage, and the saved profile meet their criteria. Report a complete setup with outstanding activation, tool, or check limitations as ready with limitations. A profile supplied for manual saving leaves setup incomplete.

## Inspect the project

1. Identify the project or module from the current directory. Read its applicable instructions, README, build entry points, and version control metadata. Keep discovery scoped to that project.
2. Read the existing `.take-the-baton/profile.md` or the profile path supplied by the user or configured in the activation instructions. Keep explicit choices and flag conflicts with current project rules or access.
3. Inspect connectors, CLI tools, and capabilities already exposed to the agent. Use scoped read-only checks where available. Distinguish a detected tool from verified access to the intended project. Establish write access through read-only permission information when available.

Identify a route for each action in the profile template. A single tool can cover several actions. Record the actual command or tool, working directory or destination, access status, and fallback. Mark a route `verified` only for the action, destination, and environment confirmed by a scoped check during setup. For write actions, use read-only permission information when it is available. Record prior chat evidence as context and leave current access `unverified` until confirmed. Use `unavailable` when the route cannot be used in this environment and `manual` for a deliberate handoff. If a route covers only part of an action, record what it can confirm and the fallback for the rest. For example, reading CI failures does not by itself confirm the status of every required check.

For a manual developer handoff, use the [resumption prompts](#manual-startup). Use the original record path when available, or the task key and the original profile if needed for lookup. For manual independent review, record who can receive the [review inputs](WORKFLOW.md#4-hand-off-the-diff-for-review) and how they return findings. Keep required review pending until an independent reviewer completes it.

Reuse tools that fit the project rules. Where a service is unfamiliar or unavailable, propose a manual handoff or describe the adapter that would be needed. Direct required sign-in to the service's normal interface and keep credentials out of the profile.

Find existing hooks, linters, formatters, validators, and CI checks. Record their commands or configuration, when they run, which changes they cover, and how to tell that each required check passed. Use project evidence for prerequisites and success criteria, such as required test counts or fresh reports. Also find the project's conventions for branch names and descriptions, commit subjects and bodies, and PR titles and templates. Record which checks or reviews are required before pushing, opening a PR, or marking a draft ready. Separately record what must be complete before merge, including reviews and CI that need an open PR. For required PR CI, record whether each check must cover the head alone or the base and outgoing change together. Keep personal check commands separate from required team checks.

Record the project's existing decision sources in the profile when they are known. Add a private decision journal only when the developer asks to keep decisions across tasks.

If check coverage or automation has a gap, propose up to three improvements that fit the project. For each one, say what it catches, when it would run, and whether it needs a local change or a team configuration change. Keep recommendations separate from discovered checks. Apply hook, tool, or CI changes only when separately requested and allowed by project rules.

## Recover context from recent chats if approved

Before proposing the profile, use this prompt in the user's language when offering chat review. Keep the option codes and reuse any choice the user has already made.

> May I review up to ten of the most recent chats in `<project or module>` to find confirmed decisions, useful commands, and unfinished tasks?
>
> - **H1. Allow.** Review the ten most recent project chats, or all of them if there are fewer.
> - **H2. Skip.** Continue setup without reading chats.
> - **H3. Selected chats only.** Review the chats or excerpts I identify.

Confirm permission and scope before reading messages. For `H3`, ask for the selection if it is missing. Review more than ten only if the user agrees to a broader scope. Verify that each chat belongs to the selected project or module using project or workspace information from the host. If the host cannot read or reliably identify the chats, use task records or ask for selected excerpts within the approved scope.

Look for confirmed decisions, useful project commands, and unfinished work. Verify project facts against current sources and distinguish confirmed decisions from suggestions or assumptions. Show the relevant findings and their sources in the setup proposal, including how many chats were reviewed and any access gaps. Propose only durable, relevant entries for the profile or an existing private decision journal. Surface unfinished task references in the report. Keep source excerpts and chat links within the agreed private scope.

## Choose how to start the workflow

Before asking about activation, check which instruction locations the host can load for this project and how they can find the private profile. If only manual startup is available and the user has not requested a feasible shared team rule, go straight to the setup proposal with the [manual prompt](#manual-startup). Preserve any preferences already given and record `manual` as the route. Use **Not applicable** for choices skipped because they cannot affect the setup.

For supported routes, ask only the applicable, unanswered questions before preparing the setup proposal. Ask them together when both apply. Use the user's language, keep the order and option codes, and use the default keyword `эстафета` in Russian and `baton` otherwise. Reuse any answer the user has already given. Ask only for missing choices on a rerun.

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

- **Personal setup.** Propose a rule in the user's existing personal instructions, scoped to the project. Point it to the agreed profile path and use the source URL and revision stored in the profile.
- **Team setup.** Show the proposed change to the shared project instructions. Give the team a common way to find each developer's private profile, such as the same project-relative ignored path or a personal pointer for external storage. Keep personal paths and private profile contents in personal storage. Apply the shared instruction edit only if the user approves that exact edit and project rules allow it.

### Manual startup

Fill in the source URL and revision and the paths needed for the request.

**Start work on a task**

> Use Take the Baton for this project. Read the workflow from `<source URL and revision>` and the profile at `<profile path>`. Work on `<task description or tracker key>`.

**Resume from a record**

> Use Take the Baton for this project. Read the workflow from `<source URL and revision>`. Resume from `<original task record path>`.

**Resume by task key**

> Use Take the Baton for this project. Read the workflow from `<source URL and revision>`. Resume `<task key>` using the original profile at `<original profile path>`.

## Confirm one proposal

Keep the profile and task records private. Use `.take-the-baton/profile.md` and `.take-the-baton/tasks/` in the selected project only when the directory is untracked and a local VCS exclusion can be verified. Check for any tracked or staged files under that path. For Git, resolve the local exclude file with `git rev-parse --git-path info/exclude` and match the actual directory relative to the repository root, including any module prefix. A tracked or staged path, or an exclusion that cannot be verified, calls for an agreed private location outside the checkout for both the profile and task records. Preserve existing tracked or staged files.

If the workflow registers tasks, record where this developer's registration records live for the project and tracker destination. One worktree can use its task directory. When setting up another worktree, reuse the original private registration records or the agreed coordinator that can reconcile prior attempts. Record how a new session can look up an original task record by tracker key or URL. Propose a separate private location only if it is needed and preserves access to earlier attempts. If the route cannot be verified, report registration as pending.

If using a private decision journal, keep it in the agreed private location. For an in-project journal, verify that its path is untracked, unstaged, and covered by the local exclusion before writing. If that cannot be verified, agree on a private path outside the checkout.

Fill in this **before** report in the user's language. Give the full proposed paths to the profile and task records. If a path in the profile is relative, state what it is relative to. Show the proposed profile and the exact changes to any activation instructions, or link to the diff. For manual startup, give a copyable prompt. If the proposal covers several working copies or environments, say how each finds the same private records and how commands run in the working copy selected for the task. Mark unverified routes as such. Include material unresolved choices and keep check recommendations separate from the changes being approved.

> **Proposed setup**
>
> - Project and scope — `<project or module and path>`
> - Private storage — `<full profile path and task record directory, local exclusion if needed, and shared registration route across your worktrees if applicable>`
> - Startup — `<mode, personal or team scope, keyword if used, and the instruction file and profile lookup for the chosen route>`
> - Changes — `<exact proposed edits, or the manual startup prompt>`
> - Tools and checks — `<main routes, what access was verified, and when required checks run and how they are confirmed>`
>
> - **S1. Confirm the proposal.**
> - **S2. Change the proposal.** Tell me what to change.

Apply the proposed changes after `S1` or an equivalent explicit confirmation. For `S2`, show the revised proposal and wait for the user's confirmation before applying the changes.

## Save and check

After confirmation, apply any agreed local exclusion and verify it before writing private files. In Git, check both tracking status and whether the intended profile and task paths are ignored. If the exclusion fails, agree on a private location outside the checkout before saving there. Preserve existing content and record the source URL and revision or tag when available. Read the profile back and check the paths and routes against the project. Apply the agreed activation instruction edit, if any, and preserve the existing instructions. Use read-only checks to verify the instruction location and profile lookup. If startup behavior can only be confirmed in a new session and has yet to be checked, report that verification as pending.

Fill in this **after** report in the user's language. Use one line per checklist item with its status and a brief confirmation or reason.

> **Setup result** — `<ready / ready with limitations / incomplete>`
>
> - Project scope — `<status and project or module path>`
> - Private storage — `<status, paths and protection>`
> - Profile — `<status and profile path>`
> - Activation — `<status, mode, scope, and instruction location or manual route>`
> - Tools and project rules — `<status, key routes and limitations>`
> - Code checks — `<status and discovered checks>`
>
> **Next request** — `<copyable prompt>`

Use **Done** for changes made, **Verified** for confirmed facts, **Proposed** for suggestions awaiting a decision, **Pending** for blocked or manual steps, and **Not applicable** with a reason when an item does not apply. Keep suggestions marked **Proposed** separate from discovered checks. For default mode, show an ordinary task request. For keyword mode, put the selected keyword first. For pending or manual startup, give the full manual prompt. If the activation rule was saved and still needs a fresh-session check, also give a short read-only request to try in a new session without supplying the profile path. Report partial changes accurately. If the profile could not be saved, return its completed contents and intended path. Ask a follow-up only when the user needs to act to finish setup. The confirmation covers the agreed profile, local exclusion, and activation instruction changes. Workflow actions follow the user's task request and the project's approval rules.

On rerun, compare the existing profile, storage protection, activation instructions, tools, and rules. If no changes are needed, report the current checklist status. If changes are needed, present them together and preserve confirmed preferences.

Optional: [reflect on recurring problems in how you work with agents](REFLECTION.md).
