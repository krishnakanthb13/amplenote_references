# `app.getNoteBacklinkContents`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Get the content of backlinks — including surrounding context, as would be shown in the backlinks section of a note — from a specific source note to a specific target note.

## Signature
`app.getNoteBacklinkContents(targetNoteHandle: object, sourceNoteHandle: object) → Promise<string[]>`

## Parameters
- `targetNoteHandle` (`object`) — object identifying the note being linked to
- `sourceNoteHandle` (`object`) — object identifying the note containing the link(s)

## Returns
`Promise<string[]>` — array of markdown strings with surrounding context.

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

## Related
- [`app.getNoteBacklinks`](./getNoteBacklinks.md)
