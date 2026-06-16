# `app.getNoteURL`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Returns a full URL for the specified note. This URL can be used to link to the note and can be used to open the note via `app.navigate`.

## Signature
`app.getNoteURL(noteHandle: object) → Promise<string>`

## Parameters
- `noteHandle` (`object`) — object identifying the note

## Returns
`Promise<string>` — the URL of the note.

## Example
```javascript
async noteOption(app, noteUUID) {
  const noteURL = await app.getNoteURL({ uuid: noteUUID });
  app.alert("note URL: " + noteURL);
}
```

## Related
- [`app.navigate`](./navigate.md)
- [`app.getNotePublicURL`](./getNotePublicURL.md)
