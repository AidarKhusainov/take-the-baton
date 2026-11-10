# Take the Baton

An agent-assisted development workflow you can set up by sharing this repository link. Your agent discovers the tools in your project and handles routine work between your decisions.

## Start with your project

Open your agent in the project you want to work on and send:

> Set up Take the Baton for my current project using https://github.com/AidarKhusainov/take-the-baton. Read SETUP.md and show me the project profile you propose.

The agent inspects project tools and checks, shows a short plan with any recommended improvements, then saves a private profile after you confirm. It reports what changed, what it verified, and what still needs attention. Any agent that can read Markdown can use the instructions. With workspace and tool access, it can also run the steps. The profile records which steps it can run and where a separate session or a manual handoff is needed.

[Setup instructions](SETUP.md) · [Workflow](WORKFLOW.md)

During setup, the agent can [recover context from recent project chats](SETUP.md#recover-context-from-recent-chats-if-approved) with your permission.

## Give it an idea or a task

- **Start from a task you have.** “Take PROJ-123 through the Take the Baton workflow.”
- **Assess an idea.** “Use Take the Baton to check whether this is worth filing. Show the reason when a document retry is rejected.”
- **Register an idea.** “Use Take the Baton to file a task for this idea. Show the reason when a document retry is rejected.”
- **Register and implement.** “Use Take the Baton to file that task and start work on it.”

An assessment gives you the evidence and a recommended next step. For registration, the agent uses your project's tracker or other agreed destination. A request to register a task ends with its reference or a draft when registration is unavailable. For implementation, a clear request can supply the acceptance criteria. The agent asks you to agree on a spec when a material decision remains or the project requires it.

## Remember a decision

> Use Take the Baton to remember that we keep the current API response format until the client migration is complete. The decision is in PROJ-123.

The agent records the decision and its source in a private project journal. It brings up relevant decisions when assessing an idea or preparing a spec.

## Follow the work

A straightforward change can stay in one session with focused checks. The agent saves a task record when work needs to pass to another session or resume later, and arranges independent review when you ask for it or the project requires it. You can inspect the diff while review proceeds. You resolve disputed findings, decide when to open the PR, and merge it.

To resume in a new session, ask the agent to use this workflow and give it the task record path, or the task key and the profile path if the profile lives outside its default location. The agent uses the record to reach the assigned developer and reviewer or replace an unavailable session when authorized. It checks the agreed spec and exact change before reusing test or review evidence.

## Optional skills

- [use-case-spec](https://github.com/AidarKhusainov/skills/blob/master/use-case-spec/SKILL.md) gives the agent a format for a full use-case spec when the task needs one.
- [clear-explanations](https://github.com/AidarKhusainov/skills/blob/master/clear-explanations/SKILL.md) guides how the agent writes reports, asks questions, and explains code.

[Project profile template](templates/profile.md) · [Task record template](templates/task.md) · [MIT License](LICENSE)
