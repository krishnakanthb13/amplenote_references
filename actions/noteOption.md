# `noteOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds options to the per-note menu, shown when editing a specific note.

## Signature
`noteOption(app, noteUUID)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `noteUUID` (`String`) — The UUID of the note the option was invoked on.

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. The check function receives the same `(app, noteUUID)` arguments as `run`.

## Example
```javascript
noteOption(app, noteUUID) {
  app.alert(noteUUID);
}
```

## Related
- [appOption](./appOption.md)
- [dailyJotOption](./dailyJotOption.md)
- [taskOption](./taskOption.md)
