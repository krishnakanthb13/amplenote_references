# `app.attachNoteMedia`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Upload a media file, associating it with the specified note. This function uploads the file directly, so the user must be online for it to work, and it may take a long time, depending on the size of the media and connectivity. Throws if the media file is too large or not allowed, or if network errors prevent upload.

## Signature
`app.attachNoteMedia(noteHandle: object, dataURL: string) → Promise<string>`

## Parameters
- `noteHandle` (`object`) — noteHandle describing the note to attach media to
- `dataURL` (`string`) — data URL describing the media file data

## Returns
`Promise<string>` — the URL of the uploaded media.

## Example
```javascript
async insertText(app) {
  const noteHandle = { uuid: app.context.noteUUID };
  const response = await fetch("https://source.unsplash.com/featured/300x200");
  const blob = await response.blob();
  const dataURL = await this._dataURLFromBlob(blob);
  const fileURL = await app.attachNoteMedia(noteHandle, dataURL);
  app.context.replaceSelection(`![](${fileURL})`);
  return null;
}
```

## Related
- [`app.getNoteAttachments`](./getNoteAttachments.md)
- [`app.getNoteImages`](./getNoteImages.md)
