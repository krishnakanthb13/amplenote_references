# `app.publishNote`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Publishing

## Description
Publish a note to a public URL. Note publishing requires an Unlimited or Founder subscription, and an active connection to the internet. If the note is already published by the current user, an existing URL will be returned instead of creating a new URL.

## Signature
`app.publishNote(noteHandle: object) → Promise<string | null>`

## Parameters
- `noteHandle` (`object`) — noteHandle describing the note to publish (must be remotely-persisted)

## Returns
`Promise<string | null>` — the URL of the published note, or `null` if publication failed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const url = await app.publishNote({ uuid: noteUUID });
  await app.alert("Public URL: " + url);
}
```

## Related
- [`app.unpublishNote`](./unpublishNote.md)
- [`app.getNotePublicURL`](./getNotePublicURL.md)
