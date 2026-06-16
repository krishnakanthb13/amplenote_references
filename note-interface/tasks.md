# `note.tasks`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tasks

## Description
Gets the tasks in the note. See `app.getNoteTasks` for more details.

## Signature
`note.tasks()`

## Parameters
None.

## Returns
`Promise<Array<task>>` — an array of [task](../appendices/types.md#task) objects belonging to the note. Each task carries fields such as `content` (markdown), `startAt`, `deadline`, `important`, `urgent`, and `uuid`; timestamp fields are Integer Unix UTC seconds.

## Equivalent `app` method
`app.getNoteTasks(noteHandle, options?)`

## Example
```javascript
const tasks = await note.tasks();
app.alert(`Note has ${tasks.length} tasks.`);
```

## Types & references
- [task](../appendices/types.md#task) — the element type of the returned array.
- [Note Interface index](./index.md)

## Related
- [`note.insertTask`](./insertTask.md)
