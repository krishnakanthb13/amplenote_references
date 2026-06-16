# `app.getTask`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Get the details of a single task.

## Signature
`app.getTask(taskUUID: string) → Promise<task | null>`

## Parameters
- `taskUUID` (`string`) — UUID identifying the task

## Returns
`Promise<task | null>` — the task object, or `null` if no task with the given UUID exists.

## Example
```javascript
async noteOption(app, noteUUID) {
  const taskUUID = "e6adcbcb-04dc-4fbd-857e-dbf63a253e7e";
  const task = await app.getTask(taskUUID);
  app.alert(JSON.stringify(task));
}
```

## Related
- [`app.updateTask`](./updateTask.md)
- [`app.getNoteTasks`](./getNoteTasks.md)
