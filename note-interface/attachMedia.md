# `note.attachMedia`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Attach a media file (image or video) to the note. See `app.attachNoteMedia` for more details.

## Signature
`note.attachMedia(dataURL)`

## Parameters
- `dataURL` (`String`) — a data URL (e.g. `data:image/png;base64,...`) containing the encoded image or video to attach.

## Returns
`Promise<String>` — the URL `String` of the attached media. Use this as the `src` of an [image](../appendices/types.md#image) when embedding it in content.

## Equivalent `app` method
`app.attachNoteMedia(noteHandle, dataURL)`

## Example
```javascript
const imageURL = await note.attachMedia("data:image/png;base64,iVBORw0KGgo...");
```

## Types & references
- [image](../appendices/types.md#image) — the returned media URL becomes an image's `src`.
- [Note Interface index](./index.md)

## Related
- [`note.attachments`](./attachments.md)
- [`note.images`](./images.md)
- [`note.updateImage`](./updateImage.md)
