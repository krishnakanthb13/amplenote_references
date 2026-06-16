# `app.deleteNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Delete a note. Users can restore deleted notes for 30 days after they are first deleted.

## Signature
`app.deleteNote(noteHandle: object) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — object identifying the note to delete

## Returns
`Promise<boolean>` — whether the note existed and was deleted.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.deleteNote({ uuid: noteUUID });
}
```

## Related
- [`app.createNote`](./createNote.md)
- [`app.findNote`](./findNote.md)
