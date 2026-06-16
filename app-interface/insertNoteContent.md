# `app.insertNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Inserts content into a note. Throws if content exceeds 100k characters or if the note is readonly.

## Signature
`app.insertNoteContent(noteHandle: object, content: string, options?: object) → Promise<void>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `content` (`String`) — markdown-formatted content to insert. See the [Markdown content appendix](../appendices/markdown-content.md) and [Markdown reference guide](../guides/markdown-reference.md).
- `options` (`Object`, optional) — keys include `atEnd` (`Boolean`, defaults to `false`; inserts at the end of the note rather than the start).

## Returns
`Promise<void>`

## Example
```javascript
noteOption(app, noteUUID) {
  app.insertNoteContent({ uuid: noteUUID }, "this is some **bold** text");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [Markdown content appendix](../appendices/markdown-content.md) — structure of the `content` markdown.
- [Markdown reference guide](../guides/markdown-reference.md) — supported markdown syntax.
- [App Interface index](./index.md)

## Related
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
