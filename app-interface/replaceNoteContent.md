# `app.replaceNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Replace the entire content of a note with new content, or replace the content of a single section of the note.

## Signature
`app.replaceNoteContent(noteHandle: object, content: string, options?: object) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `content` (`String`) — markdown content. See the [Markdown content appendix](../appendices/markdown-content.md) and [Markdown reference guide](../guides/markdown-reference.md).
- `options` (`Object`, optional) — keys include `section` (a [section](../appendices/types.md#section) or its `heading` to scope the replacement to a single section), `includeCompletedTasks`, `includeHiddenTasks`.

## Returns
`Promise<Boolean>` — whether the replacement was performed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const newContent = "**new content**";
  await app.replaceNoteContent({ uuid: noteUUID }, newContent);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [section](../appendices/types.md#section) — the `options.section` target for a scoped replacement.
- [Markdown content appendix](../appendices/markdown-content.md) — structure of the `content` markdown.
- [Markdown reference guide](../guides/markdown-reference.md) — supported markdown syntax.
- [App Interface index](./index.md)

## Related
- [`app.insertNoteContent`](./insertNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
- [`app.getNoteSections`](./getNoteSections.md)
