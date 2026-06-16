# `note.addTag`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Tags

## Description
Add a tag to the note. See `app.addNoteTag` for details.

## Signature
`note.addTag(tagName)`

## Parameters
- `tagName` (`String`) — the name of the tag to add to the note.

## Returns
`Promise<boolean>` — resolves to whether the tag was successfully added.

## Equivalent `app` method
`app.addNoteTag({ uuid }, tagName)`

## Example
```javascript
const success = await note.addTag("project/active");
```

## Related
- [`note.removeTag`](./removeTag.md)
- [`note.tags`](./tags.md)
