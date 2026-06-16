# `note.name`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Property
**Category:** Metadata

## Description
Get the title of the note. Returns the note's title as a `String`.

## Signature
`note.name`  (this is a property, not a method — access it directly without calling)

## Returns
`String` — the title of the note. Corresponds to the `name` field of a [noteHandle](../appendices/types.md#notehandle); may be an empty string for an untitled note.

## Equivalent `app` method
—

## Example
```javascript
app.alert(`This note is named ${note.name}`);
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the note's `name` field is the same title surfaced here.
- [Note Interface index](./index.md)

## Related
- [`note.setName`](./setName.md)
- [`note.tags`](./tags.md)
