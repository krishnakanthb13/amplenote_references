# `app.insertTask`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Inserts a new task at the beginning of a note. Throws if the provided content is invalid in a task context or if the note is readonly/locked.

## Signature
`app.insertTask(noteHandle: object, taskObject: object) → Promise<string>`

## Parameters
- `noteHandle` ([`noteHandle`](../appendices/types.md#notehandle)) — object identifying the note to insert the task into (e.g. `{ uuid }`)
- `taskObject` (`Object`) — a task-like object. `content` is the only required field; the rest are optional writable [`task`](../appendices/types.md#task) fields:
  - `content` (`String`) — [markdown](../guides/markdown-reference.md)-formatted content for the task
  - `startAt` (`Integer | null`) — Unix timestamp (UTC seconds) for the "Start at" time
  - `endAt` (`Integer | null`) — Unix timestamp (UTC seconds) for the end time; must be after `startAt` and requires `startAt`
  - `hideUntil` (`Integer | null`) — Unix timestamp (UTC seconds) for the "Hide until" time
  - `deadline` (`Integer | null`) — Unix timestamp (UTC seconds) for the deadline
  - `important` (`Boolean`) — whether the task is flagged important
  - `urgent` (`Boolean`) — whether the task is flagged urgent
  - `repeat` (`String | null`) — an RRULE recurrence string

## Returns
`Promise<String>` — the `uuid` of the newly created [`task`](../appendices/types.md#task).

## Types & references
- [`task`](../appendices/types.md#task) — writable fields accepted in `taskObject`
- [`noteHandle`](../appendices/types.md#notehandle) — note identifier accepted as the first argument
- [Markdown reference](../guides/markdown-reference.md) — formatting allowed in `content`
- [App Interface index](./index.md)

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
