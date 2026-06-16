# `app.getCompletedTasks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Gets tasks completed in the given time range, which includes standard completed, dismissed, and crossed-out tasks. Throws if an invalid `taskDomainUUID` is provided.

## Signature
`app.getCompletedTasks(fromTimestamp: number, toTimestamp: number, options?: object) → Promise<task[]>`

## Parameters
- `fromTimestamp` (`Integer`) — Unix timestamp (UTC seconds); only tasks completed on or after this time
- `toTimestamp` (`Integer`) — Unix timestamp (UTC seconds); only tasks completed before this time (non-inclusive)
- `options` (`Object`, optional) — keys include:
  - `taskDomainUUID` (`String`) — `uuid` of a task domain (filters to that domain only)

## Returns
`Promise<Array<`[`task`](../appendices/types.md#task)`>>` — array of [`task`](../appendices/types.md#task) objects describing completed, dismissed, and crossed-out tasks.

## Types & references
- [`task`](../appendices/types.md#task) — shape of each returned task
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const to = Math.floor(Date.now() / 1000);
  const from = to - (60 * 60 * 24);
  const completedTasks = await app.getCompletedTasks(from, to);
  await app.alert("Completed task count: " + completedTasks.length);
}
```

## Related
- [`app.getTaskDomainTasks`](./getTaskDomainTasks.md)
- [`app.getNoteTasks`](./getNoteTasks.md)
