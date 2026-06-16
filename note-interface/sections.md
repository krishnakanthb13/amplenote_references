# `note.sections`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Content

## Description
Gets the sections in the note. See `app.getNoteSections` for more details.

## Signature
`note.sections()`

## Parameters
None.

## Returns
`Promise<Array<section>>` — an array of [section](../appendices/types.md#section) objects describing the note's heading-delimited sections. Each section carries a `heading` (`{ anchor, href, level, text }` or `null`) and an `index` that disambiguates sections with identical or `null` headings.

## Equivalent `app` method
`app.getNoteSections(noteHandle)`

## Example
```javascript
const sections = await note.sections();
app.alert(`Note has ${sections.length} sections.`);
```

## Types & references
- [section](../appendices/types.md#section) — the element type of the returned array.
- [Note Interface index](./index.md)

## Related
- [`note.content`](./content.md)
- [`note.replaceContent`](./replaceContent.md)
