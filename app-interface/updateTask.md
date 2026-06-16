# `app.updateTask`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Update the properties or content of a single task.

## Signature
`app.updateTask(taskUUID: string, updates: object) → Promise<boolean>`

## Parameters
- `taskUUID` (`String`) — `uuid` identifying the task
- `updates` (`Object`) — any writable [`task`](../appendices/types.md#task) fields to apply (everything except read-only fields like `uuid`, `createdAt`, and `noteUUID`):
  - `content` (`String`) — [markdown](../guides/markdown-reference.md)-formatted task content
  - `startAt` (`Integer | null`), `endAt` (`Integer | null`, after `startAt`, requires `startAt`), `hideUntil` (`Integer | null`), `deadline` (`Integer | null`) — Unix timestamps (UTC seconds)
  - `completedAt` (`Integer | null`), `dismissedAt` (`Integer | null`) — Unix timestamps (UTC seconds)
  - `important` (`Boolean`), `urgent` (`Boolean`) — flags
  - `repeat` (`String | null`) — an RRULE recurrence string

## Returns
`Promise<Boolean>` — whether the task could be updated; returns `false` if the UUID doesn't correspond to an existing task.

## Types & references
- [`task`](../appendices/types.md#task) — writable fields accepted in `updates`
- [Markdown reference](../guides/markdown-reference.md) — formatting allowed in `content`
- [App Interface index](./index.md)

## Example
```javascript
async insertText(app) {
  const taskUUID = app.context.taskUUID;
  if (!taskUUID) return null;
  await app.updateTask(taskUUID,
    { completedAt: Math.floor(Date.now() / 1000) });
  return "";
}
```

## Related
- [`app.getTask`](./getTask.md)
- [`app.insertTask`](./insertTask.md)
