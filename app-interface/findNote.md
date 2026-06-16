# `app.findNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Returns a noteHandle identifying a note, with additional note metadata attributes populated, if the note is extant and not marked as deleted. Can be used to verify a note's existence and to fill in additional details.

## Signature
`app.findNote(noteHandle: object) → Promise<noteHandle | null>`

## Parameters
- `noteHandle` (`object`) — identifying object with properties:
  - `uuid` (`string`) — UUID (if provided, other attributes are ignored)
  - `name` (`string`) — note name (required if `uuid` not provided)
  - `tags` (`string[]`, optional) — array of tag filter strings

## Returns
`Promise<noteHandle | null>` — a note handle with metadata attributes populated, or `null` if the note is not found.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteHandle = await app.findNote({ uuid: noteUUID });
  app.alert(noteHandle.name);
}
```

## Related
- [`app.createNote`](./createNote.md)
- [`app.filterNotes`](./filterNotes.md)
- [`app.notes` object](./notes-object.md)
