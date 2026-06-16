# `note.insertTask`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tasks

## Description
Inserts a new task at the beginning of a note. See `app.insertTask` for more details.

## Signature
`note.insertTask(taskData)`

## Parameters
- `taskData` (`Object`) — a task-like object describing the task to insert. Accepts the writable fields of a [task](../appendices/types.md#task), such as `content` (markdown String), `startAt`, `deadline` (Integer Unix UTC seconds), `important`, and `urgent` (Booleans).

## Returns
`Promise<String>` — the `uuid` of the newly created [task](../appendices/types.md#task).

## Equivalent `app` method
`app.insertTask(noteHandle, taskData)`

## Example
```javascript
const taskUUID = await note.insertTask({ content: "Follow up with the team" });
```

## Types & references
- [task](../appendices/types.md#task) — the shape of the accepted object and of the returned `uuid`.
- [Note Interface index](./index.md)

## Related
- [`note.tasks`](./tasks.md)
- [`note.insertContent`](./insertContent.md)
