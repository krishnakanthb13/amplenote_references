# `app.updateNoteImage`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Media & Attachments

## Description
Update an image in a specific note. Throws if the given markdown is not valid in an image caption.

## Signature
`app.updateNoteImage(noteHandle: object, image: object, updates: object) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — noteHandle identifying the note containing the image
- `image` (`object`) — image object (only `index` and `src` keys are necessary)
- `updates` (`object`) — image properties to update (excluding `index`)

## Returns
`Promise<boolean>` — whether the image could be updated.

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

## Related
- [`app.getNoteImages`](./getNoteImages.md)
