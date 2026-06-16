# `app.setNoteName`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Sets a new name for the given note. Generally only fails if the note handle doesn't identify an extant note.

## Signature
`app.setNoteName(noteHandle: object, name: string) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `name` (`String`) — the new name for the note.

## Returns
`Promise<Boolean>` — whether the name change succeeded.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteHandle = await app.findNote({ uuid: noteUUID });
  await app.setNoteName(noteHandle, noteHandle.name + " more");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.findNote`](./findNote.md)
- [`app.createNote`](./createNote.md)
