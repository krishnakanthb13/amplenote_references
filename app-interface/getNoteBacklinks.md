# `app.getNoteBacklinks`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Returns the list of notes that link to the specified note.

## Signature
`app.getNoteBacklinks(noteHandle: object) → Promise<noteHandle[]>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note being linked to (accepts a String `uuid` shorthand).

## Returns
`Promise<Array<`[noteHandle](../appendices/types.md#notehandle)`>>` — noteHandles for the notes that link to the specified note. Also usable as an async iterable.

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

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — both the argument and the returned elements; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.getNoteBacklinkContents`](./getNoteBacklinkContents.md)
