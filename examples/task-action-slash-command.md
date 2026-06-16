# Task Action via Slash Command

> Part of [Examples](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/examples)

A common pattern is to offer a command that only appears when the user is acting on a
task. This is done with an `appOption` action whose `check` method returns the current
task's UUID (truthy) when a task is in context, so the command shows up only then. The
`run` method then loads the full task with `app.getTask()`.

- `app.context.taskUUID` — the UUID of the task currently in context, or falsy if none.
  Returning it from `check` both gates the command and hands the UUID to `run`.
- `app.getTask(taskUUID)` — resolves to the full task object, exposing all of the
  properties described in the task definition.

```javascript
(() => {
  const plugin = {
    appOption: {
      "My Task Command": {
        check: async function(app) {
          return app.context.taskUUID;
        },
        run: async function(app, noteUUID) {
          const task = await app.getTask(app.context.taskUUID);
          console.log("Now we can act upon task", task);
        }
      }
    }
  };
  return plugin;
})()
```

Because `check` returns `app.context.taskUUID`, the command is hidden whenever there is
no task in context. Once `run` has the task object, it can read or modify any of the
task's properties.
