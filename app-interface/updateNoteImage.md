# `app.updateNoteImage`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Update an image in a specific note. Throws if the given markdown is not valid in an image caption.

## Signature
`app.updateNoteImage(noteHandle: object, image: object, updates: object) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — noteHandle identifying the note containing the image (accepts a String `uuid` shorthand).
- `image` ([image](../appendices/types.md#image)) — the image to update (only the `index` and `src` keys are necessary), as returned by [`app.getNoteImages`](./getNoteImages.md).
- `updates` (`Object`) — image properties to update, excluding the read-only `index` — e.g. `caption` (markdown), `width` (px), `src`, `text`.

## Returns
`Promise<Boolean>` — whether the image could be updated.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteHandle = { uuid: noteUUID };
  const images = await app.getNoteImages(noteHandle);
  for (let i = 0; i < images.length; i++) {
    const image = images[i];
    await app.updateNoteImage(noteHandle, image, { caption: "**new caption**" });
  }
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [image](../appendices/types.md#image) — the `image` argument (`caption`, `index` read-only, `src`, `text`, optional `width`); the `caption` accepts markdown.
- [Markdown reference guide](../guides/markdown-reference.md) — valid markdown for an image caption.
- [App Interface index](./index.md)

## Related
- [`app.getNoteImages`](./getNoteImages.md)
