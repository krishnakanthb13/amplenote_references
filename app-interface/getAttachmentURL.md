# `app.getAttachmentURL`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Given the UUID of an attachment, returns a temporary URL that can be used to access the attachment. The client must be online for this function to succeed.

Note on CORS: the web environment the plugin code executes in requires a server to respond with CORS headers, and the attachments server does not add these headers for the plugin code origin.

## Signature
`app.getAttachmentURL(attachmentUUID: string) → Promise<string>`

## Parameters
- `attachmentUUID` (`String`) — the `uuid` of an [attachment](../appendices/types.md#attachment) identifying the attachment (as returned by [`app.getNoteAttachments`](./getNoteAttachments.md)).

## Returns
`Promise<String>` — a temporary URL to access the attachment content.

## Example
```javascript
async noteOption(app, noteUUID) {
  const attachments = await app.getNoteAttachments({ uuid: noteUUID });
  if (attachments.length > 0) {
    const attachmentURL = await app.getAttachmentURL(attachments[0].uuid);
    await app.alert("URL: " + attachmentURL);
  } else {
    await app.alert("Note doesn't have any attachments");
  }
}
```

## Types & references
- [attachment](../appendices/types.md#attachment) — the `attachmentUUID` argument is an attachment's `uuid`.
- [App Interface index](./index.md)

## Related
- [`app.getNoteAttachments`](./getNoteAttachments.md)
