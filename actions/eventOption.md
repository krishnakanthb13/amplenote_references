# `eventOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds an option to the popup menu shown for events (tasks and scheduled bullets) on the calendar.

## Signature
`async eventOption(app, taskUUID)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `taskUUID` (`String`) — Identifier for the task or scheduled bullet the option was invoked on.

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. The check function receives the same `(app, taskUUID)` arguments as `run`.

## Example
```javascript
async eventOption(app, taskUUID) {
  const task = await app.getTask(taskUUID);
  if (task.startAt) {
    await app.updateTask(taskUUID, { startAt: task.startAt + 3600 });
  }
}
```

## Related
- [taskOption](./taskOption.md)
- [noteOption](./noteOption.md)
