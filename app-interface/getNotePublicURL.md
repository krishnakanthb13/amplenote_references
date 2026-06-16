# `app.getNotePublicURL`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Publishing

## Description
Get a public URL for the note, if it has been published. Note that this call requires internet connectivity. Throws if a request to the server fails (e.g., the client is offline).

## Signature
`app.getNotePublicURL(noteHandle: object) → Promise<string | null>`

## Parameters
- `noteHandle` (`object`) — noteHandle identifying the note

## Returns
`Promise<string | null>` — the public URL if published, or `null` if not published.

## Example
```javascript
async noteOption(app, noteUUID) {
  const publicURL = await app.getNotePublicURL({ uuid: noteUUID });
  await app.alert("public URL: " + (publicURL || "none"));
}
```

## Related
- [`app.publishNote`](./publishNote.md)
- [`app.unpublishNote`](./unpublishNote.md)
