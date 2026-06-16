# `note.tags`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Property
**Category:** Tags

## Description
Returns an `Array` of tags that are applied to the note.

## Signature
`note.tags`  (this is a property, not a method — access it directly without calling)

## Returns
`Array` — the list of tag strings applied to the note.

## Equivalent `app` method
—

## Example
```javascript
const tags = note.tags;
app.alert(`Note has ${tags.length} tags: ${tags.join(",")}`);
```

## Related
- [`note.addTag`](./addTag.md)
- [`note.removeTag`](./removeTag.md)
