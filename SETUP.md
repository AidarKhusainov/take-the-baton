# Set up Take the Baton

Use this guide in the work project where the user asked to set up Take the Baton. Read [WORKFLOW.md](WORKFLOW.md) and [the profile template](templates/profile.md) from the supplied source. Keep the work project and the source of these instructions separate.

## Setup checklist

Use this checklist throughout setup.

| Item | Completion criterion |
| --- | --- |
| Project scope | The exact project or module path and its applicable instructions are identified. |
| Private storage | The agreed private location for both the profile and task records is confirmed. Inside a checkout, verify that the intended paths are untracked and the local exclusion applies. |
| Profile | A saved profile has been read back and contains the selected paths, commands, and tool routes. |
| Tools and project rules | Each action has a recorded access status and any required fallback. Branch names and descriptions, commit subjects and bodies, PR titles and templates, and requirements before merge are recorded, with any unavailable or inapplicable items identified. |
| Code checks | Existing hooks, linters, formatters, validators, and CI checks are recorded with their triggers. Any recommendations for gaps are listed separately. |

Setup is complete when project scope, private storage, and the saved profile meet their criteria. Report a complete setup with outstanding tool or check limitations as ready with limitations. A profile supplied for manual saving leaves setup incomplete.

## Inspect the project

1. Identify the project or module from the current directory. Read its applicable instructions, README, build entry points, and version control metadata. Keep discovery scoped to that project.
2. Read the existing `.take-the-baton/profile.md` or the profile path supplied by the user. Keep explicit choices and flag conflicts with current project rules or access.
3. Inspect connectors, CLI tools, and capabilities already exposed to the agent. Use scoped read-only checks where available. Distinguish a detected tool from verified access to the intended project. Establish write access through read-only permission information when available.

Identify a route for each action in the profile template. A single tool can cover several actions. Record the actual command or tool, working directory or destination, access status, and fallback. Use `verified`, `unverified`, or `unavailable` for tool access. Use `manual` for a deliberate handoff.

Reuse tools that fit the project rules. Where a service is unfamiliar or unavailable, propose a manual handoff or describe the adapter that would be needed. Direct required sign-in to the service's normal interface and keep credentials out of the profile.

Find existing hooks, linters, formatters, validators, and CI checks. Record their commands or configuration, when they run, and which changes they cover. Also find the project's conventions for branch names and descriptions, commit subjects and bodies, and PR titles and templates. Record any requirements before merge. Keep personal check commands separate from required team checks.

If check coverage or automation has a gap, propose up to three improvements that fit the project. For each one, say what it catches, when it would run, and whether it needs a local change or a team configuration change. Keep recommendations separate from discovered checks. Apply hook, tool, or CI changes only when separately requested and allowed by project rules.

## Confirm one proposal

Keep the profile and task records private. Use `.take-the-baton/profile.md` and `.take-the-baton/tasks/` in the selected project only when the directory is untracked and a local VCS exclusion can be verified. Check for any tracked or staged files under that path. For Git, resolve the local exclude file with `git rev-parse --git-path info/exclude` and match the actual directory relative to the repository root, including any module prefix. A tracked or staged path, or an exclusion that cannot be verified, calls for an agreed private location outside the checkout for both the profile and task records. Preserve existing tracked or staged files.

Give a short **before** report with the project, exact paths and proposed changes, key tool routes, and gaps that need a handoff. List any check recommendations separately. Ask for one confirmation of the setup and include material unresolved choices in that request.

## Save and check

After confirmation, apply any agreed local exclusion and verify it before writing private files. In Git, check both tracking status and whether the intended profile and task paths are ignored. If the exclusion fails, agree on a private location outside the checkout before saving there. Preserve existing content and record the source URL and revision or tag when available. Read the profile back and check the paths and routes against the project. Use read-only checks for setup verification.

Give a short **after** report in the chat. Use one line per checklist item with its status and one brief confirmation or reason. Use **Done** for changes made, **Verified** for confirmed facts, **Proposed** for suggestions awaiting a decision, **Pending** for blocked or manual steps, and **Not applicable** with a reason when an item does not apply. Keep suggestions marked **Proposed** separately from discovered checks. State the overall setup result, profile path, and next prompt. Report partial changes accurately. If the workspace cannot save the profile, return its completed contents and intended path for manual saving. The setup confirmation covers the agreed profile and local exclusion changes. Workflow actions follow the user's task request and the project's approval rules.

On rerun, compare the existing profile, storage protection, tools, and rules. If no changes are needed, report the current checklist status. If changes are needed, present them together and preserve confirmed preferences.

## Offer an optional reflection run

After the initial setup, offer the developer a [manual reflection run](REFLECTION.md) to look for recurring friction in their work with agents. Confirm the sources and private notes location before reading chat history. Setting up the project profile only authorizes the agreed setup changes. A daily schedule requires a separate request. The developer can skip reflection and use the workflow immediately.
