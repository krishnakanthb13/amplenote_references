# `app.setNoteName`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Sets a new name for the given note. Generally only fails if the note handle doesn't identify an extant note.

## Signature
`app.setNoteName(noteHandle: object, name: string) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — object identifying the note
- `name` (`string`) — the new name for the note

## Returns
`Promise<boolean>` — whether the name change succeeded.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteHandle = await app.findNote({ uuid: noteUUID });
  await app.setNoteName(noteHandle, noteHandle.name + " more");
}
```

## Related
- [`app.findNote`](./findNote.md)
- [`app.createNote`](./createNote.md)
