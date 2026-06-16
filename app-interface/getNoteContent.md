# `app.getNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Get the content of a note, as markdown.

## Signature
`app.getNoteContent(noteHandle: object) → Promise<string>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).

## Returns
`Promise<String>` — the note content as markdown. See the [Markdown content appendix](../appendices/markdown-content.md) and [Markdown reference guide](../guides/markdown-reference.md) for the supported syntax.

## Example
```javascript
async noteOption(app, noteUUID) {
  const markdown = await app.getNoteContent({ uuid: noteUUID });
  app.alert(markdown);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [Markdown content appendix](../appendices/markdown-content.md) — structure of the returned markdown.
- [Markdown reference guide](../guides/markdown-reference.md) — supported markdown syntax.
- [App Interface index](./index.md)

## Related
- [`app.insertNoteContent`](./insertNoteContent.md)
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteSections`](./getNoteSections.md)
