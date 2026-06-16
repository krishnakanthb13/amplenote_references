# `app.getNoteAttachments`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Returns a list of attachments in the given note. Only attachments that are currently referenced in the note will be returned — if an attachment is uploaded to a note then deleted from the note or moved to a different note, it will not be included in the resulting list.

## Signature
`app.getNoteAttachments(noteHandle: object) → Promise<attachment[] | null>`

## Parameters
- `noteHandle` (`object`) — noteHandle identifying the note to list attachments for

## Returns
`Promise<attachment[] | null>` — array of attachment objects, or `null` if the note doesn't exist.

## Example
```javascript
async noteOption(app, noteUUID) {
  const attachments = await app.getNoteAttachments({ uuid: noteUUID });
  await app.alert(`${attachments.length} attachments`);
}
```

## Related
- [`app.getAttachmentURL`](./getAttachmentURL.md)
- [`app.attachNoteMedia`](./attachNoteMedia.md)
