# `note.content`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Content

## Description
Get the content of the note, as markdown. See `app.getNoteContent` for more details.

## Signature
`note.content()`

## Parameters
None.

## Returns
`Promise<String>` — the note's content as a markdown String.

## Equivalent `app` method
`app.getNoteContent(noteHandle)`

## Example
```javascript
const markdown = await note.content();
app.alert(markdown);
```

## Types & references
- Returns a markdown `String`.
- [section](../appendices/types.md#section) — use [`note.sections`](./sections.md) to address content by heading-delimited section.
- [Note Interface index](./index.md)

## Related
- [`note.replaceContent`](./replaceContent.md)
- [`note.insertContent`](./insertContent.md)
- [`note.sections`](./sections.md)
