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
`String` — the URL of the note.

## Equivalent `app` method
—

## Example
```javascript
const link = note.url();
app.alert(`Open this note at: ${link}`);
```

## Related
- [`note.publicURL`](./publicURL.md)
- [`note.name`](./name.md)
