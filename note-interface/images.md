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
`Promise<image[]>` — an array of inline image objects in the note.

## Equivalent `app` method
`app.getNoteImages(noteHandle)`

## Example
```javascript
const images = await note.images();
app.alert(`Note has ${images.length} inline images.`);
```

## Related
- [`note.updateImage`](./updateImage.md)
- [`note.attachMedia`](./attachMedia.md)
- [`note.attachments`](./attachments.md)
