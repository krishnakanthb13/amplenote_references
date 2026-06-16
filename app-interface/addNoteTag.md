# `app.addNoteTag`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tags & Organization

## Description
Add a tag to a note. The tag text is normalized (to lowercase, dashes) to conform to allowed tag names. Returns `false` if a shared tag cannot be added.

## Signature
`app.addNoteTag(noteHandle: object, tag: string) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `tag` (`String`) — text of the [tag](../appendices/types.md#tag) to add (normalized to lowercase, dashes, with `/` as a hierarchy delimiter).

## Returns
`Promise<Boolean>` — whether the tag was added.

## Example
```javascript
async noteOption(app, noteUUID) {
  const added = await app.addNoteTag({ uuid: noteUUID }, "some-tag");
  await app.alert(added ? "Tag added" : "Failed to add tag");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [tag](../appendices/types.md#tag) — the `tag` argument is the tag's `text` (lowercase, dashes, `/` delimiter).
- [App Interface index](./index.md)

## Related
- [`app.removeNoteTag`](./removeNoteTag.md)
- [`app.getTags`](./getTags.md)
