# `app.removeNoteTag`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tags & Organization

## Description
Removes a tag from a note. Returns `true` even if the note didn't have the tag; only a removal failure returns `false`.

## Signature
`app.removeNoteTag(noteHandle: object, tag: string) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `tag` (`String`) — text of the [tag](../appendices/types.md#tag) to remove (lowercase, dashes, `/` delimiter).

## Returns
`Promise<Boolean>` — whether the tag was removed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const removed = await app.removeNoteTag({ uuid: noteUUID }, "some-tag");
  app.alert(removed ? "Tag removed" : "Failed to remove tag");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [tag](../appendices/types.md#tag) — the `tag` argument is the tag's `text` (lowercase, dashes, `/` delimiter).
- [App Interface index](./index.md)

## Related
- [`app.addNoteTag`](./addNoteTag.md)
- [`app.getTags`](./getTags.md)
