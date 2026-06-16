# `note.images`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Get all inline images in the note. See `app.getNoteImages` for more details.

## Signature
`note.images()`

## Parameters
None.

## Returns
`Promise<Array<image>>` — an array of inline [image](../appendices/types.md#image) objects in the note. Each image carries `caption` (markdown), `index` (read-only), `src`, `text` (OCR), and optional `width`.

## Equivalent `app` method
`app.getNoteImages(noteHandle)`

## Example
```javascript
const images = await note.images();
app.alert(`Note has ${images.length} inline images.`);
```

## Types & references
- [image](../appendices/types.md#image) — the element type of the returned array.
- [Note Interface index](./index.md)

## Related
- [`note.updateImage`](./updateImage.md)
- [`note.attachMedia`](./attachMedia.md)
- [`note.attachments`](./attachments.md)
