# `note.attachments`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Gets a list of attachments in the note. See `app.getNoteAttachments` for details.

## Signature
`note.attachments()`

## Parameters
None.

## Returns
`Promise<Array<attachment>>` — an array of [attachment](../appendices/types.md#attachment) objects belonging to the note. Each attachment carries `name`, `type` (MIME type String), and `uuid`.

## Equivalent `app` method
`app.getNoteAttachments(noteHandle)`

## Example
```javascript
const attachments = await note.attachments();
app.alert(`Note has ${attachments.length} attachments.`);
```

## Types & references
- [attachment](../appendices/types.md#attachment) — the element type of the returned array.
- [Note Interface index](./index.md)

## Related
- [`note.attachMedia`](./attachMedia.md)
- [`note.images`](./images.md)
