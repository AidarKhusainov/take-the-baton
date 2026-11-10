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

Identify a route for each action in the profile template. A single tool can cover several actions. Record the actual command or tool, working directory or destination, access status, and fallback. Use `verified`, `unverified`, or `unavailable` for tool access. Use `manual` for a deliberate handoff.

Reuse tools that fit the project rules. Where a service is unfamiliar or unavailable, propose a manual handoff or describe the adapter that would be needed. Direct required sign-in to the service's normal interface and keep credentials out of the profile.

Find existing hooks, linters, formatters, validators, and CI checks. Record their commands or configuration, when they run, and which changes they cover. Also find the project's conventions for branch names and descriptions, commit subjects and bodies, and PR titles and templates. Record which checks or reviews are required before pushing, opening a PR, or marking a draft ready. Separately record what must be complete before merge, including reviews and CI that need an open PR. Keep personal check commands separate from required team checks.

Record the project's existing decision sources in the profile when they are known. Add a private decision journal only when the developer asks to keep decisions across tasks.

If check coverage or automation has a gap, propose up to three improvements that fit the project. For each one, say what it catches, when it would run, and whether it needs a local change or a team configuration change. Keep recommendations separate from discovered checks. Apply hook, tool, or CI changes only when separately requested and allowed by project rules.

## Recover context from recent chats if approved

Before proposing the profile, offer to review the ten most recent chats for this project, or all of them if there are fewer. Confirm permission and the scope before reading messages. Review more only if the user agrees to a broader scope. Verify that each chat belongs to the selected project or module using project or workspace information from the host. If the host cannot read or reliably identify the chats, use task records or ask the user for selected excerpts.

Look for confirmed decisions, useful project commands, and unfinished work. Verify project facts against current sources and distinguish confirmed decisions from suggestions or assumptions. Show the relevant findings and their sources in the setup proposal, including how many chats were reviewed and any access gaps. Propose only durable, relevant entries for the profile or an existing private decision journal. Surface unfinished task references in the report. Keep source excerpts and chat links within the agreed private scope.

## Choose how to start the workflow

Ask the following two questions together before preparing the setup proposal. Use the user's language, keep the order and option codes, and use the default keyword `эстафета` in Russian and `baton` otherwise. Reuse any answer the user has already given. Ask only for missing choices on a rerun.

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
> Reply with both choices, for example `1A, 2A`. To choose another keyword, include it with `1B`.

Treat the answers as preferences for the proposal. Confirm any file changes after showing the proposal. Keep permission to read chat history separate.

Find an instruction location that the host already loads for the selected project. Scope the rule to that project or module, and identify the profile and workflow source. Follow existing shared project rules and surface any conflict with the requested mode or scope. In default mode, start the workflow for development task requests. In keyword mode, match the chosen keyword at the start of the user's own message, ignoring case and allowing whitespace or punctuation after the keyword. Either mode can also start when the user explicitly asks to use Take the Baton.

- **Personal setup.** Propose a rule in the user's existing personal instructions, scoped to the project. Point it to the agreed profile path and use the source URL and revision stored in the profile.
- **Team setup.** Show the proposed change to the shared project instructions. Give the team a common way to find each developer's private profile, such as the same project-relative ignored path or a personal pointer for external storage. Keep personal paths and private profile contents in personal storage. Apply the shared instruction edit only if the user approves that exact edit and project rules allow it.

If no supported instruction location or profile lookup can be established, keep the user's choices and offer manual startup. Report the activation route as `manual` when manual startup is the agreed route. Fill in the placeholders in this copyable prompt.

> Use Take the Baton for this project. Read the workflow from `<source URL and revision>` and the profile at `<profile path>`. Work on `<task description or tracker key>`.

## Confirm one proposal

Keep the profile and task records private. Use `.take-the-baton/profile.md` and `.take-the-baton/tasks/` in the selected project only when the directory is untracked and a local VCS exclusion can be verified. Check for any tracked or staged files under that path. For Git, resolve the local exclude file with `git rev-parse --git-path info/exclude` and match the actual directory relative to the repository root, including any module prefix. A tracked or staged path, or an exclusion that cannot be verified, calls for an agreed private location outside the checkout for both the profile and task records. Preserve existing tracked or staged files.

If using a private decision journal, keep it in the agreed private location. For an in-project journal, verify that its path is untracked, unstaged, and covered by the local exclusion before writing. If that cannot be verified, agree on a private path outside the checkout.

Give a short **before** report with the project, exact paths and proposed changes, key tool routes, and gaps that need a handoff. Include the chosen mode, scope and keyword if used, the profile lookup, and the exact instruction change or manual startup prompt. List any check recommendations separately. Ask for one confirmation of the proposed changes and include any material unresolved choices in that request.

## Save and check

After confirmation, apply any agreed local exclusion and verify it before writing private files. In Git, check both tracking status and whether the intended profile and task paths are ignored. If the exclusion fails, agree on a private location outside the checkout before saving there. Preserve existing content and record the source URL and revision or tag when available. Read the profile back and check the paths and routes against the project. Apply the agreed activation instruction edit, if any, and preserve the existing instructions. Use read-only checks to verify the instruction location and profile lookup. If startup behavior can only be confirmed in a new session and has yet to be checked, report that verification as pending.

Give a short **after** report in the chat. Use one line per checklist item with its status and one brief confirmation or reason. Use **Done** for changes made, **Verified** for confirmed facts, **Proposed** for suggestions awaiting a decision, **Pending** for blocked or manual steps, and **Not applicable** with a reason when an item does not apply. Keep suggestions marked **Proposed** separately from discovered checks. State the overall setup result, profile path, activation mode, scope, instruction location or manual route, and the next prompt. For default mode, show an ordinary task request. For keyword mode, show that request with the selected keyword first. If the selected mode is still pending or startup is manual, give the full manual prompt. Report partial changes accurately. If the workspace cannot save the profile, return its completed contents and intended path for manual saving. The setup confirmation covers the agreed profile, local exclusion, and activation instruction changes. Workflow actions follow the user's task request and the project's approval rules.

On rerun, compare the existing profile, storage protection, activation instructions, tools, and rules. If no changes are needed, report the current checklist status. If changes are needed, present them together and preserve confirmed preferences.

## Offer an optional reflection run

After the initial setup, offer the developer a [manual reflection run](REFLECTION.md) to look for recurring friction in their work with agents. Confirm the sources and private notes location before reading chat history. Setting up the project profile only authorizes the agreed setup changes. A daily schedule requires a separate request. The developer can skip reflection and use the workflow immediately.
