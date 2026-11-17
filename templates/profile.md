# Take the Baton project profile

- Project and scope:
- Project root or module:
- Project instructions:
- Existing project decision sources, if any:
- Private decision journal path, if used:
- Version control and default comparison base:
- Take the Baton source URL and revision:
- Private installation registry path on this host:
- Activation mode (default or keyword) and keyword, if used (Not applicable for manual-only setup):
- Activation scope (personal or team, or Not applicable for manual-only setup):
- User-confirmed activation choices for this project (project or module path and approved mode, keyword if used, and scope):
- Activation instruction location, profile lookup, and route status:
- Task record directory:
- Group record directory and shared private access route, if used:
- Private storage and verified local exclusion (if inside the checkout):

## Tool routes

For each row, fill in the actual tool or command, the destination or working directory, the evidence of access, and the fallback. Record `verified`, `unverified`, `unavailable`, or `manual` in the access column. Add any project rules that apply to the action.

| Action | Route and scope | Access and evidence | Fallback |
| --- | --- | --- | --- |
| Read tasks and comments | | | |
| Register tasks | | | |
| Identify revisions and obtain a diff | | | |
| Run focused local checks | | | |
| Run final local checks | | | |
| Start or resume the assigned developer session | | | |
| Start or resume the assigned independent reviewer session | | | |
| Create working chats for a task group, if authorized | | | |
| Send assignments, read results, and wait for working chats | | | |
| Isolate workspaces or serialize mutations for related tasks | | | |
| Find, create, inspect, or pause the reflection schedule, if authorized | | | |
| Read remote review feedback | | | |
| Read remote CI | | | |
| Create a commit, if requested | | | |
| Push a revision, if requested | | | |
| Create a PR, if requested | | | |

## Project rules

- Task destination, whether a tracker key is required, and private registration records or coordinator used across this developer's worktrees:
- Boundaries on edits and verification:
- Branch naming and description conventions:
- Commit subject and body conventions:
- PR title, body template, and task-linking rules:
- Existing hooks, check commands, and triggers:
- Required checks and reviews before publication (push, PR opening, or marking a draft ready, as applicable):
- Required reviews, CI, approvals, and manual checks before merge, including which checks run in the open PR and the revision or tree each CI check must cover:
- Decisions or actions reserved for the user:
- Where task records and review material may be stored:

## Subagent selection

Use SUBAGENTS.md from the Take the Baton source URL and revision recorded above; this private profile may live outside the source checkout.

- Priority (balanced by default, quality, or economy) and confirmation source:
- Explicit project constraints, fixed model or reasoning effort, and budget if set:
- Supported delegation surfaces and model ID/reasoning effort combinations, with evidence, status, and verification date:
- Economical, standard, and deep-analysis mappings by surface, with concrete model IDs and model-specific default efforts where verified:
- Launch and continuation overrides, including fresh-context constraints:
- Fallback per unsupported dimension (model or effort), retained supported choices, and any unverified or unmet required constraints:

## Task group coordination

- Host capabilities and limits for persistent working chats:
- Project/host lookup and working-chat launch reconciliation route:
- Workspace isolation or single-writer handoff route for this VCS:
- Shared contract sources and integration verification environment:

Record group-specific authorization and ownership in each group record.

## Reflection

- Mode (daily, manual, or off) and confirmation source:
- Approved project scope, sources, start boundary, and any recurring chat-reading permission:
- Private notes, per-source checkpoints, and enabled task observation capture scope and location:
- Local run time and time zone, if scheduled:
- Scheduler route, schedule reference, actual status, and last verification:
- Profile and schedule mutation owner and handoff route:
- Scheduler reservation or idempotency for duplicate creation, if supported:
- Unresolved schedule creation or update attempt and reconciliation evidence:
- Pause route or manual fallback:
