# `app.findNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Returns a noteHandle identifying a note, with additional note metadata attributes populated, if the note is extant and not marked as deleted. Can be used to verify a note's existence and to fill in additional details.

## Signature
`app.findNote(noteHandle: object) → Promise<noteHandle | null>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — identifying object (or a String `uuid` shorthand) with properties:
  - `uuid` (`String`) — UUID (if provided, other attributes are ignored).
  - `name` (`String`) — note name (required if `uuid` not provided).
  - `tags` (`Array<String>`, optional) — array of [tag](../appendices/types.md#tag) filter strings.

## Returns
`Promise<`[noteHandle](../appendices/types.md#notehandle)`| null>` — a noteHandle with metadata attributes populated (`changed`, `created`, `name`, `tags`, `updated`, `uuid`, `vault`, plus `published`/`shared` only when true), or `null` if the note is not found.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteHandle = await app.findNote({ uuid: noteUUID });
  app.alert(noteHandle.name);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — both the argument and the return value; accepts a String uuid as shorthand. A `local-` prefixed uuid is unsynced.
- [tag](../appendices/types.md#tag) — tag text format used in the `tags` filter.
- [App Interface index](./index.md)

## Related
- [`app.createNote`](./createNote.md)
- [`app.filterNotes`](./filterNotes.md)
- [`app.notes` object](./notes-object.md)
