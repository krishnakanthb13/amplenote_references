# `note.url`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Metadata

## Description
Returns the String URL of the note (the in-app link to open the note).

## Signature
`note.url()`

## Parameters
None.

## Returns
`String` — the in-app URL of the note (a link that opens the note inside Amplenote). This is not a public/shared URL; for that, see [`note.publicURL`](./publicURL.md).

## Equivalent `app` method
—

## Example
```javascript
const link = note.url();
app.alert(`Open this note at: ${link}`);
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the underlying note identity this URL targets.
- [Note Interface index](./index.md)

## Related
- [`note.publicURL`](./publicURL.md)
- [`note.name`](./name.md)
