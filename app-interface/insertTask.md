# `app.insertTask`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Inserts a new task at the beginning of a note. Throws if the provided content is invalid in a task context or if the note is readonly/locked.

## Signature
`app.insertTask(noteHandle: object, taskObject: object) → Promise<string>`

## Parameters
- `noteHandle` (`object`) — object identifying the note to insert the task into
- `taskObject` (`object`) — task object with optional attributes:
  - `content` (`string`) — markdown-formatted content for the task
  - `hideUntil` (`number`) — unix timestamp in seconds for the "Hide until" time
  - `startAt` (`number`) — unix timestamp in seconds for the "Start at" time

## Returns
`Promise<string>` — the UUID of the newly created task.

## Example
```javascript
async noteOption(app, noteUUID) {
  const taskUUID = await app.insertTask({ uuid: noteUUID },
    { content: "this is a task" });
  app.alert(taskUUID);
}
```

## Related
- [`app.getNoteTasks`](./getNoteTasks.md)
- [`app.getTask`](./getTask.md)
- [`app.updateTask`](./updateTask.md)
