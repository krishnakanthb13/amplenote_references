# `suggestTaskTargetNotes`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Tasks

## Description
Given a task, allows the plugin to suggest an ordered set of notes that the task could be added to.

## Signature
`async suggestTaskTargetNotes(app, task, suggestedNoteHandles)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `task` ([task](../appendices/types.md#task)) — The task being added (exposes `uuid`, `content`, `noteUUID`, scheduling fields, etc.).
- `suggestedNoteHandles` (`Array` of [noteHandle](../appendices/types.md#notehandle)) — The array of currently suggested note handles.

## Returns
`Array` of [noteHandle](../appendices/types.md#notehandle) objects or `String` uuids (the shorthand note handle form), ordered by preference.

## The `check` function
Standard check behavior — return falsy to skip suggesting. The check function receives the same `(app, task, suggestedNoteHandles)` arguments as `run`.

## Example
```javascript
async suggestTaskTargetNotes(app, task, suggestedNoteHandles) {
  return suggestedNoteHandles.toReversed();
}
```

## Types & references
- [task](../appendices/types.md#task) — the object passed as `task`.
- [noteHandle](../appendices/types.md#notehandle) — element type of `suggestedNoteHandles` and the return array (a `String` uuid is the accepted shorthand).
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its optional `check`/`run` form.

## Related
- [taskOption](./taskOption.md)
- [eventOption](./eventOption.md)
