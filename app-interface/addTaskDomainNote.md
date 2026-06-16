# `app.addTaskDomainNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Ensure the specified note is included in the specified task domain. If the note is already included in the task domain by virtue of a tag the note has, the note will be included directly in the task domain such that removing the tag from the note will leave it in the task domain. Throws if the given task domain UUID doesn't correspond to any task domain.

## Signature
`app.addTaskDomainNote(taskDomainUUID: string, noteHandle: object) → Promise<boolean>`

## Parameters
- `taskDomainUUID` (`string`) — task domain UUID (obtainable via `getTaskDomains`)
- `noteHandle` (`object`) — object identifying the note to add to the task domain

## Returns
`Promise<boolean>` — whether the note was added or already included; returns `false` for an invalid note handle.

## Example
```javascript
async noteOption(app, noteUUID) {
  const taskDomains = await app.getTaskDomains();
  const taskDomain = taskDomains[0];
  const added = await app.addTaskDomainNote(taskDomain.uuid,
    { uuid: noteUUID });
  await app.alert(added ? "Note added to first task domain"
    : "Failed to add note");
}
```

## Related
- [`app.getTaskDomains`](./getTaskDomains.md)
- [`app.getTaskDomainTasks`](./getTaskDomainTasks.md)
