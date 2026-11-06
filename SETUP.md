# Set up Take the Baton

Use this guide in the work project where the user asked to set up Take the Baton. Read [WORKFLOW.md](WORKFLOW.md) and [the profile template](templates/profile.md) from the supplied source. Keep the work project and the source of these instructions separate.

## Inspect the project

1. Identify the project or module from the current directory. Read its applicable instructions, README, build entry points, and version control metadata. Keep discovery scoped to that project.
2. Read the existing `.take-the-baton/profile.md` or the profile path supplied by the user. Keep explicit choices and flag conflicts with current project rules or access.
3. Inspect connectors, CLI tools, and capabilities already exposed to the agent. Use scoped read-only checks where available. Distinguish a detected tool from verified access to the intended project. Establish write access through read-only permission information when available.

Identify a route for each action in the profile template. A single tool can cover several actions. Record the actual command or tool, working directory or destination, access status, and fallback. Use `verified`, `unverified`, or `unavailable` for tool access. Use `manual` for a deliberate handoff.

Reuse tools that fit the project rules. Where a service is unfamiliar or unavailable, propose a manual handoff or describe the adapter that would be needed. Direct required sign-in to the service's normal interface and keep credentials out of the profile.

## Confirm one proposal

Show the detected project, setup location, proposed tool routes, and the steps that need user input or a handoff. If the environment is clear, ask one question to confirm the proposal. Include any choice that materially affects the setup in the same request. For example, ask which tracker owns the project's tasks when both GitHub Issues and a separate tracker are present.

Default to a personal profile at `.take-the-baton/profile.md` and task records under `.take-the-baton/tasks/`. Use the project's local exclusion mechanism if needed and available. Include any required exclusion change in the proposal. If the project needs a separate private location, agree on that location and record it in the profile. Share a profile in the project only when the user chooses to do so. Keep task records in the agreed private location even with a shared profile.

## Save and check

After confirmation, save the profile. If the workspace cannot save it, return the completed profile and its intended path for a manual handoff. Preserve existing content and record the source URL and revision or tag when available. Read the profile back and check the resolved paths and routes against the project. Use read-only checks for setup verification.

Return the profile path, the next prompt the user can give any agent, and any capability that still needs attention. The setup confirmation applies to the profile and the changes shown in the proposal. Workflow actions use the user's task request and the project's approval rules.

On rerun, compare the existing profile with current tools and rules. Report a current profile as ready. If it needs changes, present them together and preserve confirmed preferences when saving.
