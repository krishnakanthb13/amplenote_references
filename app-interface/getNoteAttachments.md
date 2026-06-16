# `app.getNoteAttachments`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Returns a list of attachments in the given note. Only attachments that are currently referenced in the note will be returned — if an attachment is uploaded to a note then deleted from the note or moved to a different note, it will not be included in the resulting list.

## Signature
`app.getNoteAttachments(noteHandle: object) → Promise<attachment[] | null>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — noteHandle identifying the note to list attachments for (accepts a String `uuid` shorthand).

## Returns
`Promise<Array<`[attachment](../appendices/types.md#attachment)`> | null>` — array of attachment objects (each with `name`, `type` MIME string, and `uuid`), or `null` if the note doesn't exist.

## Example
```javascript
async noteOption(app, noteUUID) {
  const attachments = await app.getNoteAttachments({ uuid: noteUUID });
  await app.alert(`${attachments.length} attachments`);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [attachment](../appendices/types.md#attachment) — the returned array elements (`name`, `type`, `uuid`); pass an attachment `uuid` to [`app.getAttachmentURL`](./getAttachmentURL.md).
- [App Interface index](./index.md)

## Related
- [`app.getAttachmentURL`](./getAttachmentURL.md)
- [`app.attachNoteMedia`](./attachNoteMedia.md)
