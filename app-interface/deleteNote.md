# `app.deleteNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Delete a note. Users can restore deleted notes for 30 days after they are first deleted.

## Signature
`app.deleteNote(noteHandle: object) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note to delete (accepts a String `uuid` shorthand).

## Returns
`Promise<Boolean>` — whether the note existed and was deleted.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.deleteNote({ uuid: noteUUID });
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.createNote`](./createNote.md)
- [`app.findNote`](./findNote.md)
