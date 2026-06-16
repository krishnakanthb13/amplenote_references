# `note.removeTag`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tags

## Description
Remove a tag from the note. See `app.removeNoteTag` for details.

## Signature
`note.removeTag(tagName)`

## Parameters
- `tagName` (`String`) — the tag text to remove from the note. This is the `text` of a [tag](../appendices/types.md#tag): lowercase letters, dashes, and the `/` parent-child delimiter (e.g. `"project/active"`).

## Returns
`Promise<Boolean>` — resolves to whether the tag was successfully removed.

## Equivalent `app` method
`app.removeNoteTag({ uuid }, tagName)`

## Example
```javascript
const success = await note.removeTag("project/active");
```

## Types & references
- [tag](../appendices/types.md#tag) — the tag type; this method accepts a tag `text` String.
- [Note Interface index](./index.md)

## Related
- [`note.addTag`](./addTag.md)
- [`note.tags`](./tags.md)
