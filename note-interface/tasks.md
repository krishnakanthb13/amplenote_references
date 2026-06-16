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
`Promise<task[]>` — an array of task objects belonging to the note.

## Equivalent `app` method
`app.getNoteTasks(noteHandle, options?)`

## Example
```javascript
const tasks = await note.tasks();
app.alert(`Note has ${tasks.length} tasks.`);
```

## Related
- [`note.insertTask`](./insertTask.md)
