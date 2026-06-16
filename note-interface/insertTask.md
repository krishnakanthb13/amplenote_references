# `note.insertTask`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tasks

## Description
Inserts a new task at the beginning of a note. See `app.insertTask` for more details.

## Signature
`note.insertTask(taskData)`

## Parameters
- `taskData` (`object`) — an object describing the task to insert (for example its `content`, and optional scheduling/flag attributes as supported by `app.insertTask`).

## Returns
`Promise<String>` — the UUID of the newly created task.

## Equivalent `app` method
`app.insertTask(noteHandle, taskData)`

## Example
```javascript
const taskUUID = await note.insertTask({ content: "Follow up with the team" });
```

## Related
- [`note.tasks`](./tasks.md)
- [`note.insertContent`](./insertContent.md)
