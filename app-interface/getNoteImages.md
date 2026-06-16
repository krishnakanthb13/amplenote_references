# `app.getNoteImages`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Get all the inline images in a note (does not include images in Rich Footnotes).

## Signature
`app.getNoteImages(noteHandle: object) → Promise<image[]>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — noteHandle identifying the note (accepts a String `uuid` shorthand).

## Returns
`Promise<Array<`[image](../appendices/types.md#image)`>>` — array of image objects, each with `caption` (markdown), `index` (read-only), `src`, `text` (OCR), and optional `width` (px).

## Example
```javascript
async noteOption(app, noteUUID) {
  const images = await app.getNoteImages({ uuid: noteUUID });
  await app.alert("image count: " + images.length);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [image](../appendices/types.md#image) — the returned array elements; pass one to [`app.updateNoteImage`](./updateNoteImage.md).
- [App Interface index](./index.md)

## Related
- [`app.updateNoteImage`](./updateNoteImage.md)
- [`app.attachNoteMedia`](./attachNoteMedia.md)
