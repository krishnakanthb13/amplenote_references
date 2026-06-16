# `app.getTaskDomainTasks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Gets the list of tasks that belong to the given task domain. Note that this includes tasks that are not scheduled (on the calendar).

This function can return a large amount of data, so it's highly recommended to use an async iterator to reduce the potential for performance impact.

## Signature
`app.getTaskDomainTasks(taskDomainUUID: string) → Promise<task[]>` (supports async iteration)

## Parameters
- `taskDomainUUID` (`String`) — task domain `uuid`

## Returns
`Promise<Array<`[`task`](../appendices/types.md#task)`>>` — array of [`task`](../appendices/types.md#task) objects in the task domain. The return value is also an async iterable, so it can be consumed lazily via `for await` to limit memory/performance impact.

## Types & references
- [`task`](../appendices/types.md#task) — shape of each returned task
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const taskDomains = await app.getTaskDomains();
  const taskDomainUUID = taskDomains[0].uuid;
  for await (const task of app.getTaskDomainTasks(taskDomainUUID)) {
    console.log("task: " + task.uuid);
  }
}
```

## Related
- [`app.getTaskDomains`](./getTaskDomains.md)
- [`app.addTaskDomainNote`](./addTaskDomainNote.md)
