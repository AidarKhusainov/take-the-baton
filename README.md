# Take the Baton

An agent-assisted development workflow you can set up by sharing this repository link. Your agent discovers the tools in your project and handles routine work between your decisions.

## Start with your project

Open your agent in the project you want to work on and send:

> Set up Take the Baton for my current project using https://github.com/AidarKhusainov/take-the-baton. Read SETUP.md and show me the project profile you propose.

The agent inspects project tools and checks, shows a short plan with any recommended improvements, then saves a private profile after you confirm. It reports what changed, what it verified, and what still needs attention. Any agent that can read Markdown can use the instructions. With workspace and tool access, it can also run the steps. The profile records which steps it can run and where a separate session or a manual handoff is needed.

[Setup instructions](SETUP.md) · [Workflow](WORKFLOW.md)

## Give it a task

- **Start from a task you have.** “Take PROJ-123 through the Take the Baton workflow.”
- **Register an idea.** “Use Take the Baton to file a task for this idea. Show the reason when a document retry is rejected.”
- **Register and implement.** “Use Take the Baton to file that task and start work on it.”

The agent uses your project's tracker or other agreed destination. A request to register a task ends with its reference or a draft when registration is unavailable. A request to implement starts with a spec for you to agree on.

## Follow the work

The analyst prepares a spec. The developer implements and tests it. You inspect the diff, then an independent reviewer examines it. The developer checks each finding and fixes the confirmed issues within scope. You resolve disputed findings, decide when to open the PR, and merge it.

The project profile and task record let a new session pick up the work. To resume, tell the new agent to use this repository's workflow and give it the task record path, or the task key and the profile path if the profile lives outside its default location. It will check the agreed spec and exact change before reusing test or review evidence.

[Project profile template](templates/profile.md) · [Task record template](templates/task.md) · [MIT License](LICENSE)
