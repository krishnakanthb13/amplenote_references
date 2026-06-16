# `note.updateImage`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Update a specific image in the note (for example to change its caption or other properties). See `app.updateNoteImage` for more details.

## Signature
`note.updateImage(image, options)`

## Parameters
- `image` (`image`) — the image object to update (typically one obtained from `note.images()`).
- `options` (`object`) — the properties to change on the image (for example a new caption).

## Returns
`Promise<void>`

## Equivalent `app` method
`app.updateNoteImage(noteHandle, image, options)`

## Example
```javascript
const images = await note.images();
await note.updateImage(images[0], { caption: "Updated caption" });
```

## Related
- [`note.images`](./images.md)
- [`note.attachMedia`](./attachMedia.md)
