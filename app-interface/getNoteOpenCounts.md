# `app.getNoteOpenCounts`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Returns the number of times a note has been opened over recent rollup periods (week, month, and quarter).

## Signature
`app.getNoteOpenCounts(noteHandle: object) → Promise<object | null>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).

## Returns
`Promise<Object | null>` — an object with numeric properties (`week`, `month`, `quarter`), or `null` if the UUID is invalid.

## Example
```javascript
async noteOption(app, noteUUID) {
  const counts = await app.getNoteOpenCounts({ uuid: noteUUID });
  app.alert(`Opens — week: ${counts.week}, month: ${counts.month}, quarter: ${counts.quarter}`);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.getNoteSettings`](./getNoteSettings.md)
- [`app.getNoteURL`](./getNoteURL.md)
