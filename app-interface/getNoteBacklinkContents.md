# `app.getNoteBacklinkContents`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Get the content of backlinks — including surrounding context, as would be shown in the backlinks section of a note — from a specific source note to a specific target note.

## Signature
`app.getNoteBacklinkContents(targetNoteHandle: object, sourceNoteHandle: object) → Promise<string[]>`

## Parameters
- `targetNoteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note being linked to (accepts a String `uuid` shorthand).
- `sourceNoteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note containing the link(s) (accepts a String `uuid` shorthand).

## Returns
`Promise<Array<String>>` — markdown strings, each with surrounding context. See the [Markdown content appendix](../appendices/markdown-content.md) and [Markdown reference guide](../guides/markdown-reference.md).

## Example
```javascript
async noteOption(app, noteUUID) {
  const targetNoteHandle = { uuid: noteUUID };
  const sourceNoteHandles = await app.getNoteBacklinks(targetNoteHandle);
  if (sourceNoteHandles.length > 0) {
    const sourceNoteHandle = sourceNoteHandles[0];
    const backlinkContents = await app.getNoteBacklinkContents(
      targetNoteHandle, sourceNoteHandle);
    await app.alert(backlinkContents.join("\n\n"));
  }
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — both arguments; each accepts a String uuid as shorthand.
- [Markdown content appendix](../appendices/markdown-content.md) — structure of the returned markdown.
- [Markdown reference guide](../guides/markdown-reference.md) — supported markdown syntax.
- [App Interface index](./index.md)

## Related
- [`app.getNoteBacklinks`](./getNoteBacklinks.md)
