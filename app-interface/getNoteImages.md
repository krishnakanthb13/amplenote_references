# `app.getNoteImages`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Get all the inline images in a note (does not include images in Rich Footnotes).

## Signature
`app.getNoteImages(noteHandle: object) → Promise<image[]>`

## Parameters
- `noteHandle` (`object`) — noteHandle identifying the note

## Returns
`Promise<image[]>` — array of image objects.

## Example
```javascript
async noteOption(app, noteUUID) {
  const images = await app.getNoteImages({ uuid: noteUUID });
  await app.alert("image count: " + images.length);
}
```

## Related
- [`app.updateNoteImage`](./updateNoteImage.md)
- [`app.attachNoteMedia`](./attachNoteMedia.md)
