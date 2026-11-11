# Take the Baton

[Русский](README.ru.md)

Take the Baton helps your coding agent work through a task, from investigation to opening a pull request. The agent carries out the agreed steps and asks for your decision when a choice would change the expected behavior, expand the scope, or require accepting a significant risk.

If you need to move the work to a new chat, the agent saves a task record with what changed, how the checks went, and what to do next. To resume, start Take the Baton using the method you set up and include the path to the record. For manual startup, use the [resume prompt](SETUP.md#manual-startup).

## Getting started

Open a chat with your coding agent in your project and send this message.

```text
Set up Take the Baton for this project.
https://github.com/AidarKhusainov/take-the-baton
```

After setup, use the prompt from your agent’s report. The examples below are for projects configured to start Take the Baton with the keyword `baton`.

To investigate a task:

```text
Baton: investigate PROJ-123
```

To take a task through to a pull request:

```text
Baton: look into PROJ-123, make the fix, and open a pull request.
```

[Setup guide](SETUP.md) · [Workflow](WORKFLOW.md) · [MIT License](LICENSE)
