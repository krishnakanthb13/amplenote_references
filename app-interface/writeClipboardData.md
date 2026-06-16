# `app.writeClipboardData`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Utilities

## Description
Write to the clipboard. The plugin code execution environment can prevent use of clipboard APIs in some browsers, so this `app` function is provided for full cross-platform support. Throws if an unsupported mime type or invalid base64 data is supplied.

Allowed MIME types:
- `"text/plain"` — the data argument should be the text
- `"image/png"` — the data argument should be base64 encoded

## Signature
`app.writeClipboardData(data: string, mimeType?: string) → Promise<void>`

## Parameters
- `data` (`String`) — data to copy to the clipboard (base64 encoded for non-text types)
- `mimeType` (`String`, optional) — mime type; defaults to `"text/plain"`

## Returns
`Promise<void>`

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.writeClipboardData(noteUUID);
  await app.alert("Note UUID copied to clipboard");
}
```

## Related
- [`app.saveFile`](./saveFile.md)
