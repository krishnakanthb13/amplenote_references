# `note.addTag`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tags

## Description
Add a tag to the note. See `app.addNoteTag` for details.

## Signature
`note.addTag(tagName)`

## Parameters
- `tagName` (`String`) — the tag text to add to the note. This is the `text` of a [tag](../appendices/types.md#tag): lowercase letters, dashes, and the `/` parent-child delimiter (e.g. `"project/active"`).

## Returns
`Promise<Boolean>` — resolves to whether the tag was successfully added.

## Equivalent `app` method
`app.addNoteTag({ uuid }, tagName)`

## Example
```javascript
const success = await note.addTag("project/active");
```

## Types & references
- [tag](../appendices/types.md#tag) — the tag type; this method accepts a tag `text` String.
- [Note Interface index](./index.md)

## Related
- [`note.removeTag`](./removeTag.md)
- [`note.tags`](./tags.md)
