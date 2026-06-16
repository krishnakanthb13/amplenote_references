# `app.unpublishNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Publishing

## Description
Unpublish a previously published note. Throws if network connectivity is not available.

## Signature
`app.unpublishNote(noteHandle: object) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — noteHandle describing the note to unpublish (must be remotely-persisted)

## Returns
`Promise<boolean>` — whether the note is now unpublished.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.unpublishNote({ uuid: noteUUID });
}
```

## Related
- [`app.publishNote`](./publishNote.md)
- [`app.getNotePublicURL`](./getNotePublicURL.md)
