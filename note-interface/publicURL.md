# `note.publicURL`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Publishing

## Description
Get a link to the published version of a note, if the note is published.

## Signature
`note.publicURL()`

## Parameters
None.

## Returns
`Promise<String | null>` — the public URL `String` of the note, or `null` if the note is not published.

## Equivalent `app` method
—

## Example
```javascript
const url = await note.publicURL();
if (url) {
  app.alert(`Public link: ${url}`);
} else {
  app.alert("This note is not published.");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — a published note's handle reports `published: true`.
- [Note Interface index](./index.md)

## Related
- [`note.publish`](./publish.md)
