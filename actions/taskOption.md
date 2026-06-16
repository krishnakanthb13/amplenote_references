# `taskOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds options to the task commands menu (invoked when typing `!` in the body of a task).

## Signature
`taskOption(app, task)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `task` (`Object`) — The task the option was invoked on.

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. The check function receives the same `(app, task)` arguments as `run`.

## Example
```javascript
taskOption(app, task) {
  app.alert(JSON.stringify(task));
}
```

## Related
- [eventOption](./eventOption.md)
- [suggestTaskTargetNotes](./suggestTaskTargetNotes.md)
- [noteOption](./noteOption.md)
