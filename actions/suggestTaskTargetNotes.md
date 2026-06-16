# `suggestTaskTargetNotes`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Tasks

## Description
Given a task, allows the plugin to suggest an ordered set of notes that the task could be added to.

## Signature
`async suggestTaskTargetNotes(app, task, suggestedNoteHandles)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `task` (`Object`) — The task being added.
- `suggestedNoteHandles` (`Array<noteHandle>`) — The array of currently suggested note handles.

## Returns
`Array` of note handle objects or UUID strings, ordered by preference.

## The `check` function
Standard check behavior — return falsy to skip suggesting. The check function receives the same `(app, task, suggestedNoteHandles)` arguments as `run`.

## Example
```javascript
async suggestTaskTargetNotes(app, task, suggestedNoteHandles) {
  return suggestedNoteHandles.toReversed();
}
```

## Related
- [taskOption](./taskOption.md)
- [eventOption](./eventOption.md)
