# `app.updateTask`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Update the properties or content of a single task.

## Signature
`app.updateTask(taskUUID: string, updates: object) → Promise<boolean>`

## Parameters
- `taskUUID` (`string`) — UUID identifying the task
- `updates` (`object`) — updates to apply (all task properties supported except `uuid`)

## Returns
`Promise<boolean>` — whether the task could be updated; returns `false` if the UUID doesn't correspond to an existing task.

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
