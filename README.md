# Take the Baton

[Русский](README.ru.md)

Take the Baton helps your coding agent work through a task, from investigation to opening a pull request. The agent carries out the agreed steps and asks for your decision when a choice would change the expected behavior, expand the scope, or require accepting a significant risk.

You can also coordinate related tasks from one chat. The agent tracks dependencies, assigns work to separate working chats when authorized and supported, and checks the combined result. Tasks can start before any PR exists and can produce multiple PRs.

If you need to move the work to a new chat, the agent saves a task record with what changed, how the checks went, and what to do next. To resume, start Take the Baton using the method you set up and include the path to the record. For manual startup, use the [resume prompt](SETUP.md#manual-startup).

## Getting started

Open a chat with your coding agent in your project and send this message.

```text
Set up Take the Baton for this project using SETUP.md.
https://github.com/AidarKhusainov/take-the-baton
Ask me the applicable setup questions for this project. Reuse another project's answers only if I explicitly ask you to.
Show me the exact proposed file changes and wait for my confirmation before writing them.
```

After setup, use the prompt from your agent’s report. The examples below are for projects configured to start Take the Baton with the keyword `baton`.

Setup also offers optional daily reflection. If you accept, the agent agrees the sources, time, and private storage with you, then sets up and verifies the schedule when the host supports it. Reflection proposes improvements based on recurring problems; you approve specific instruction changes. Manual reflection and opting out are also available.

Subagent model and reasoning selection uses **balanced** priority by default. Each assigning chat considers the task's difficulty, uncertainty, consequences, and available checks, then chooses supported settings within your constraints. You can choose quality or economy priority in the project profile. The policy covers subagents and preserves the settings and host rules for your working chats.

To investigate a task:

```text
Baton: investigate PROJ-123
```

To take a task through to a pull request:

```text
Baton: look into PROJ-123, make the fix, and open a pull request.
```

To coordinate related tasks through to PRs:

```text
Baton: take on related tasks PROJ-123, PROJ-124, and PROJ-125. Create working chats and coordinate them from this chat. Work out the dependencies, implement and verify the changes, and open or update the PRs. Bring decisions about shared behavior here.
```

You can supply task descriptions or existing PRs as well. The agent records the relationships between tasks and PRs and reports any unavailable chat, publication, or verification capabilities. To resume a group, start Take the Baton and supply the original group record path.

## Update an installation

Send this in the project you want to update.

```text
Update Take the Baton in this project using UPDATE.md from https://github.com/AidarKhusainov/take-the-baton. Use the latest revision of the default branch and preserve this project's settings and task records. Show the proposed changes and wait for my confirmation.
```

To update all known installations, send the following from a chat with access to those projects.

```text
Update Take the Baton in all accessible projects where it is installed using UPDATE.md from https://github.com/AidarKhusainov/take-the-baton. Preserve each project's settings and task records. Show which installations you found and the proposed changes, then wait for my confirmation. Report the result for each installation.
```

Setup records installations in a private registry. For older installations or a registry at a custom location, include known project or profile paths or the registry path if needed.

[Setup guide](SETUP.md) · [Update guide](UPDATE.md) · [Task workflow](WORKFLOW.md) · [Related tasks](GROUPS.md) · [Subagent selection](SUBAGENTS.md) · [Reflection](REFLECTION.md) · [MIT License](LICENSE)
