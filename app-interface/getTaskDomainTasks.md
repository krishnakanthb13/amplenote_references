# `app.getTaskDomainTasks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Gets the list of tasks that belong to the given task domain. Note that this includes tasks that are not scheduled (on the calendar).

This function can return a large amount of data, so it's highly recommended to use an async iterator to reduce the potential for performance impact.

## Signature
`app.getTaskDomainTasks(taskDomainUUID: string) → Promise<task[]>` (supports async iteration)

## Parameters
- `taskDomainUUID` (`string`) — task domain UUID

## Returns
`Promise<task[]>` — array of task objects in the task domain (iterable via `for await`).

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
