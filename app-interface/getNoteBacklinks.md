# `app.getNoteBacklinks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Returns the list of notes that link to the specified note.

## Signature
`app.getNoteBacklinks(noteHandle: object) → Promise<noteHandle[]>`

## Parameters
- `noteHandle` (`object`) — object identifying the note being linked to

## Returns
`Promise<noteHandle[]>` — array of notes that link to the specified note.

## Example
```javascript
async noteOption(app, noteUUID) {
  let count = 0;
  for await (const referencingNoteHandle of
    app.getNoteBacklinks({ uuid: noteUUID })) {
    await app.alert("referencingNoteHandle: " +
      JSON.stringify(referencingNoteHandle));
    count++;
  }
  await app.alert("count: " + count);
}
```

## Related
- [`app.getNoteBacklinkContents`](./getNoteBacklinkContents.md)
