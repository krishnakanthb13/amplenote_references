# `note.tags`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Property
**Category:** Tags

## Description
Returns an `Array` of tags that are applied to the note.

## Signature
`note.tags`  (this is a property, not a method — access it directly without calling)

## Returns
`Array<String>` — the list of tag texts applied to the note. Each entry is the `text` of a [tag](../appendices/types.md#tag) (lowercase letters, dashes, and the `/` parent-child delimiter, e.g. `"project/active"`).

## Equivalent `app` method
—

## Example
```javascript
const tags = note.tags;
app.alert(`Note has ${tags.length} tags: ${tags.join(",")}`);
```

## Types & references
- [tag](../appendices/types.md#tag) — the underlying tag type (this property exposes only the `text` of each).
- [Note Interface index](./index.md)

## Related
- [`note.addTag`](./addTag.md)
- [`note.removeTag`](./removeTag.md)
