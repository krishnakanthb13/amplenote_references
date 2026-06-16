# `app.getNoteOpenCounts`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Returns the number of times a note has been opened over recent rollup periods (week, month, and quarter).

## Signature
`app.getNoteOpenCounts(noteHandle: object) → Promise<object | null>`

## Parameters
- `noteHandle` (`object`) — object identifying the note

## Returns
`Promise<object | null>` — an object with numeric properties (`week`, `month`, `quarter`), or `null` if the UUID is invalid.

## Example
```javascript
async noteOption(app, noteUUID) {
  const counts = await app.getNoteOpenCounts({ uuid: noteUUID });
  app.alert(`Opens — week: ${counts.week}, month: ${counts.month}, quarter: ${counts.quarter}`);
}
```

## Related
- [`app.getNoteSettings`](./getNoteSettings.md)
- [`app.getNoteURL`](./getNoteURL.md)
