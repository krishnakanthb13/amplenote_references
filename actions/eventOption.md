# `eventOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds an option to the popup menu shown for events (tasks and scheduled bullets) on the calendar.

## Signature
`async eventOption(app, taskUUID)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `taskUUID` (`String` uuid) — The `uuid` of the [task](../appendices/types.md#task) (or scheduled bullet) the option was invoked on. Pass it to `app.getTask(taskUUID)` to retrieve the full [task](../appendices/types.md#task) object.

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

## Types & references
- [task](../appendices/types.md#task) — `taskUUID` is the `String` uuid of a task; `app.getTask` returns the full object.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its optional `check`/`run` form.

## Related
- [taskOption](./taskOption.md)
- [noteOption](./noteOption.md)
