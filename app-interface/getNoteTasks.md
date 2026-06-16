# `app.getNoteTasks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Returns the tasks that are present in the specified note.

## Signature
`app.getNoteTasks(noteHandle: object, options?: object) → Promise<task[]>`

## Parameters
- `noteHandle` (`object`) — object identifying the note to get tasks from
- `options` (`object`, optional) — keys include:
  - `includeDone` (`boolean`) — whether completed and dismissed tasks should be returned (defaults to `false`)

## Returns
`Promise<task[]>` — array of task objects.

## Example
```javascript
async noteOption(app, noteUUID) {
  const tasks = await app.getNoteTasks({ uuid: noteUUID });
  app.alert(`Note has ${ tasks.length } tasks`);
}
```

## Related
- [`app.insertTask`](./insertTask.md)
- [`app.getTask`](./getTask.md)
- [`app.updateTask`](./updateTask.md)
