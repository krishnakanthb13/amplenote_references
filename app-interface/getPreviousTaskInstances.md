# `app.getPreviousTaskInstances`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface#app.getPreviousTaskInstances)

**Category:** Tasks

## Description
Get previous instances of a repeating task, newest first. The given task itself is not included.

Note that this function can return a large amount of data, so it's highly recommended to use an async iterator to reduce the potential for performance impact.

## Signature
`app.getPreviousTaskInstances(taskUUID: string) → Promise<task[]>` (supports async iteration)

## Parameters
- `taskUUID` (`String`) — UUID string identifying the task.

## Returns
`Promise<Array<`[`task`](../appendices/types.md#task)`>>` — array of [`task`](../appendices/types.md#task) objects representing previous instances of repeating tasks, newest first. The return value is also an async iterable, so it can be consumed lazily via `for await` to minimize memory and performance impact.

## Types & references
- [`task`](../appendices/types.md#task) — shape of each returned task
- [App Interface index](./index.md)

## Example
```javascript
{
  async appOption(app) {
    const taskUUID = "TASK_UUID";
    for await (const task of app.getPreviousTaskInstances(taskUUID)) {
      console.log("previous task: " + task.uuid);
    }
  }
}
```

## Related
- [`app.getTask`](./getTask.md)
- [`app.getNoteTasks`](./getNoteTasks.md)
- [`app.getCompletedTasks`](./getCompletedTasks.md)
- [`app.getTaskDomainTasks`](./getTaskDomainTasks.md)
