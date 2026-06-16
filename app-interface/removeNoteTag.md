# `app.removeNoteTag`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tags & Organization

## Description
Removes a tag from a note. Returns `true` even if the note didn't have the tag; only a removal failure returns `false`.

## Signature
`app.removeNoteTag(noteHandle: object, tag: string) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — object identifying the note
- `tag` (`string`) — text of the tag to remove

## Returns
`Promise<boolean>` — whether the tag was removed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const removed = await app.removeNoteTag({ uuid: noteUUID }, "some-tag");
  app.alert(removed ? "Tag removed" : "Failed to remove tag");
}
```

## Related
- [`app.addNoteTag`](./addNoteTag.md)
- [`app.getTags`](./getTags.md)
