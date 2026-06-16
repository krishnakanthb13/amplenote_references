# `app.getNoteTasks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Returns the tasks that are present in the specified note.

## Signature
`app.getNoteTasks(noteHandle: object, options?: object) → Promise<task[]>`

## Parameters
- `noteHandle` ([`noteHandle`](../appendices/types.md#notehandle)) — object identifying the note to get tasks from (e.g. `{ uuid }`)
- `options` (`Object`, optional) — keys include:
  - `includeDone` (`Boolean`) — whether completed and dismissed tasks should be returned (defaults to `false`)

## Returns
`Promise<Array<`[`task`](../appendices/types.md#task)`>>` — array of [`task`](../appendices/types.md#task) objects present in the note.

## Types & references
- [`task`](../appendices/types.md#task) — shape of each returned task
- [`noteHandle`](../appendices/types.md#notehandle) — note identifier accepted as the first argument
- [App Interface index](./index.md)

## Example
```javascript
async noteOption(app, noteUUID) {
  const tasks = await app.getNoteTasks({ uuid: noteUUID });
  app.alert(`Note has ${ tasks.length } tasks`);
}
```

## Related
- [`app.insertTask`](./insertTask.md)
- [`app.getTask`](./getTask.md)
- [`app.updateTask`](./updateTask.md)
