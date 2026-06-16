# `note.removeTag`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tags

## Description
Remove a tag from the note. See `app.removeNoteTag` for details.

## Signature
`note.removeTag(tagName)`

## Parameters
- `tagName` (`String`) — the name of the tag to remove from the note.

## Returns
`Promise<boolean>` — resolves to whether the tag was successfully removed.

## Equivalent `app` method
`app.removeNoteTag({ uuid }, tagName)`

## Example
```javascript
const success = await note.removeTag("project/active");
```

## Related
- [`note.addTag`](./addTag.md)
- [`note.tags`](./tags.md)
