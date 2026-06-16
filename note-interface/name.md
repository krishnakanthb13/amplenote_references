# `note.name`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Property
**Category:** Metadata

## Description
Get the title of the note. Returns the note's title as a `String`.

## Signature
`note.name`  (this is a property, not a method — access it directly without calling)

## Returns
`String` — the title of the note.

## Equivalent `app` method
—

## Example
```javascript
app.alert(`This note is named ${note.name}`);
```

## Related
- [`note.setName`](./setName.md)
- [`note.tags`](./tags.md)
