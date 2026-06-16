# `app.createNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Create a new note, optionally specifying a name and/or tags to apply. The returned UUID may be local-prefixed initially but will change upon remote persistence. It can be used immediately on the same client.

## Signature
`app.createNote(name?: string, tags?: string[], options?: object) → Promise<string>`

## Parameters
- `name` (`String`, optional) — name for the new note.
- `tags` (`Array<String>`, optional) — array of [tag](../appendices/types.md#tag) text strings to apply (lowercase, dashes, `/` delimiter).
- `options` (`Object`, optional) — keys include `archive` (`Boolean`, defaults to `false`).

## Returns
`Promise<String>` — the `uuid` of the newly created note (the `uuid` of a [noteHandle](../appendices/types.md#notehandle)). The returned UUID may be `local-` prefixed initially (unsynced) and will change upon remote persistence; it can be used immediately on the same client.

## Example
```javascript
async noteOption(app, noteUUID) {
  const uuid = await app.createNote("some new note", ["some-tag"]);
  app.alert(uuid);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the returned UUID is a noteHandle `uuid`; accepts a String uuid as shorthand elsewhere.
- [tag](../appendices/types.md#tag) — tag text format applied via the `tags` argument.
- [App Interface index](./index.md)

## Related
- [`app.findNote`](./findNote.md)
- [`app.deleteNote`](./deleteNote.md)
- [`app.notes` object](./notes-object.md)
