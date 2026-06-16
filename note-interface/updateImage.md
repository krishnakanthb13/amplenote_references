# `note.updateImage`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Media

## Description
Update a specific image in the note (for example to change its caption or other properties). See `app.updateNoteImage` for more details.

## Signature
`note.updateImage(image, options)`

## Parameters
- `image` ([image](../appendices/types.md#image)) — the image object to update, typically one obtained from [`note.images`](./images.md). It is identified by its `src` together with its read-only `index`.
- `options` (`Object`) — an updates object specifying the writable [image](../appendices/types.md#image) properties to change, such as `caption` (markdown String), `text` (OCR String), or `width` (Integer pixels).

## Returns
`Promise<void>`

## Equivalent `app` method
`app.updateNoteImage(noteHandle, image, options)`

## Example
```javascript
const images = await note.images();
await note.updateImage(images[0], { caption: "Updated caption" });
```

## Types & references
- [image](../appendices/types.md#image) — both the image argument and the shape of the updates object.
- [Note Interface index](./index.md)

## Related
- [`note.images`](./images.md)
- [`note.attachMedia`](./attachMedia.md)
