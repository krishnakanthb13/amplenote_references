# `app.unpublishNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Publishing

## Description
Unpublish a previously published note. Throws if network connectivity is not available.

## Signature
`app.unpublishNote(noteHandle: object) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — noteHandle describing the note to unpublish; must be remotely-persisted (a non-`local-` prefixed `uuid`). Accepts a String `uuid` shorthand.

## Returns
`Promise<Boolean>` — whether the note is now unpublished.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.unpublishNote({ uuid: noteUUID });
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.publishNote`](./publishNote.md)
- [`app.getNotePublicURL`](./getNotePublicURL.md)
