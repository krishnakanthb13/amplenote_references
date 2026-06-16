# `note.attachMedia`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Attach a media file (image or video) to the note. See `app.attachNoteMedia` for more details.

## Signature
`note.attachMedia(dataURL)`

## Parameters
- `dataURL` (`String`) — a data URL containing the encoded image or video to attach.

## Returns
`Promise<String>` — the URL of the attached media (image URL).

## Equivalent `app` method
`app.attachNoteMedia(noteHandle, dataURL)`

## Example
```javascript
const imageURL = await note.attachMedia("data:image/png;base64,iVBORw0KGgo...");
```

## Related
- [`note.attachments`](./attachments.md)
- [`note.images`](./images.md)
- [`note.updateImage`](./updateImage.md)
