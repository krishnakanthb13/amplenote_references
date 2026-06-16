# `app.publishNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Publishing

## Description
Publish a note to a public URL. Note publishing requires an Unlimited or Founder subscription, and an active connection to the internet. If the note is already published by the current user, an existing URL will be returned instead of creating a new URL.

## Signature
`app.publishNote(noteHandle: object) → Promise<string | null>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — noteHandle describing the note to publish; must be remotely-persisted (a non-`local-` prefixed `uuid`). Accepts a String `uuid` shorthand.

## Returns
`Promise<String | null>` — the URL of the published note, or `null` if publication failed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const url = await app.publishNote({ uuid: noteUUID });
  await app.alert("Public URL: " + url);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note (must be remotely-persisted; a `local-` prefixed uuid is unsynced). Accepts a String uuid as shorthand. When a note is published, its noteHandle gains a `published` property.
- [App Interface index](./index.md)

## Related
- [`app.unpublishNote`](./unpublishNote.md)
- [`app.getNotePublicURL`](./getNotePublicURL.md)
