# `app.saveFile`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Utilities

## Description
Save a file.

## Signature
`app.saveFile(file: Blob | File, filename: string) → Promise<void>`

## Parameters
- `file` (`Blob | File`) — object describing the file content
- `filename` (`String`) — filename to use for the file

## Returns
`Promise<void>` — resolves when the save request has been sent.

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
async noteOption(app) {
  const file = new Blob(["some text"], { type: "text/plain" });
  await app.saveFile(file, "test.txt");
}
```

## Related
- [`app.writeClipboardData`](./writeClipboardData.md)
