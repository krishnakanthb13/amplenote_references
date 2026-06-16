# `app.createNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Create a new note, optionally specifying a name and/or tags to apply. The returned UUID may be local-prefixed initially but will change upon remote persistence. It can be used immediately on the same client.

## Signature
`app.createNote(name?: string, tags?: string[], options?: object) → Promise<string>`

## Parameters
- `name` (`string`, optional) — name for the new note
- `tags` (`string[]`, optional) — array of tag names to apply
- `options` (`object`, optional) — keys include `archive` (boolean, defaults to `false`)

## Returns
`Promise<string>` — the UUID of the newly created note.

## Example
```javascript
async noteOption(app, noteUUID) {
  const uuid = await app.createNote("some new note", ["some-tag"]);
  app.alert(uuid);
}
```

## Related
- [`app.findNote`](./findNote.md)
- [`app.deleteNote`](./deleteNote.md)
- [`app.notes` object](./notes-object.md)
