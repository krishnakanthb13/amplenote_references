# `app.addTaskDomainNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Ensure the specified note is included in the specified task domain. If the note is already included in the task domain by virtue of a tag the note has, the note will be included directly in the task domain such that removing the tag from the note will leave it in the task domain. Throws if the given task domain UUID doesn't correspond to any task domain.

## Signature
`app.addTaskDomainNote(taskDomainUUID: string, noteHandle: object) → Promise<boolean>`

## Parameters
- `taskDomainUUID` (`String`) — task domain `uuid` (obtainable via `getTaskDomains`)
- `noteHandle` ([`noteHandle`](../appendices/types.md#notehandle)) — object identifying the note to add to the task domain (e.g. `{ uuid }`)

## Returns
`Promise<Boolean>` — whether the note was added or already included; returns `false` for an invalid note handle.

## Types & references
- [`noteHandle`](../appendices/types.md#notehandle) — note identifier accepted as the second argument
- [App Interface index](./index.md)

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
