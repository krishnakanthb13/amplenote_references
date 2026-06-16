# `noteOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds options to the per-note menu, shown when editing a specific note.

## Signature
`noteOption(app, noteUUID)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `noteUUID` (`String` uuid) — The UUID of the note the option was invoked on. A bare uuid `String` is the shorthand form of a [noteHandle](../appendices/types.md#notehandle), so it can be passed anywhere a note handle is accepted to look the note up.

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

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — `noteUUID` is a `String` uuid that resolves to a note handle.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its optional `check`/`run` form.

## Related
- [appOption](./appOption.md)
- [dailyJotOption](./dailyJotOption.md)
- [taskOption](./taskOption.md)
